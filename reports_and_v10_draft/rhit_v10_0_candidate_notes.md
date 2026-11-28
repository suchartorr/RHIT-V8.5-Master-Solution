# บันทึกพัฒนาการและแผนการอัปเกรด: RHIT Candidate Version 10.0 (Zero-Input Dark Sector Closure)

* **สถานะปัจจุบัน:** Candidate / Experimental Validation Complete (~85%–90% Readiness)
* **สาขาจัดเก็บ (Git Branch):** `ws2/suchart-v10-candidate`
* **หลักการควบคุม:** Zero-Contamination Core ($\chi^2 = 1.9421$, $\text{dof} = 4$ คงเดิม 100%)
* **หลักฐานการตรวจสอบความบริสุทธิ์ (SHA-256 Verified):**
  * `rhit_v9_0_ai_ssot.json`: `a5ced502e27892456ae9d012e09132b0fd54543910a3d598116bfc48b762f28e` (Unchanged)
  * `rhit_v9_0_audit_kernel.py`: `43e48b754811390940066083a06d1a51424c4c792e0ecd86494b9107f469a002` (Unchanged)

---

## 1. สาระสำคัญของการอัปเกรดสู่ V10.0 (Core Theoretical Upgrade)

ในรุ่น **RHIT V9.0** ค่าคงที่อันตรกิริยากำลังสี่ $\lambda_{\text{V9}}$ พิสูจน์มาจากเรขาคณิต 5 มิติแล้ว แต่สเกลมวลสสารมืด $m_{\text{eff}} = 2.83 \times 10^{-20}\text{ eV}$ ยังคงเป็นค่าอินพุตอ้างอิง

ในข้อเสนอ **RHIT V10.0 Candidate** เราปิดวงจรตัวแปรอินพุตในเสาหลักที่ 3 โดยผูกสเกลการสลายตัวของสสารมืดเข้ากับ **สเกลการแตกสมมาตร Pati-Salam ($M_I$)** ที่พิสูจน์จากเสาหลักที่ 1 โดยตรง ($f_a = M_I$) ทำให้เสาหลักที่ 3 กลายเป็นผลลัพธ์เชิงทำนายแบบ **Zero-Input (0 พารามิเตอร์อิสระใหม่)**

### สมการหลักที่อัปเกรด
$$m_{\text{eff}}^{\text{(V10)}} = M_I \sqrt{\lambda_{\text{V9}}} = 3.297879 \times 10^{-20}\text{ eV}$$

* **สเกลต้นทาง ($f_a = M_I$):** $6.288608 \times 10^{12}\text{ GeV}$ (จากเสาหลักที่ 1)
* **ค่าคงที่แรงผลัก 5 มิติ ($\lambda_{\text{V9}}$):** $2.750175621636 \times 10^{-83}$ (คงเดิม)
* **รัศมีแกนกลางโซลิตอนในสุญญากาศ ($R_{\text{TF,vac}}^{\text{(V10)}}$):** $235.9135\text{ pc}$ (ลดลงจาก $320.3682\text{ pc}$ ใน V9.0)
* **มวลสูงสุดของโซลิตอน (Kaup/Colpi Limit):** $7.8669 \times 10^{15}\,M_\odot$

---

## 2. สรุปผลการรันทดสอบความสอดคล้องฉบับสมบูรณ์ (Complete Validation Results)

### 2.1 การเปรียบเทียบข้ามระเบียบวิธีบนฐานข้อมูล LVDB (`dwarf_mw.csv` และ `dwarf_all.csv`)

| ชุดข้อมูล & ระเบียบวิธี | แบบจำลอง | $k$ | $\chi^2$ | $\chi^2_{\text{red}}$ | เทียบ NFW | AIC |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: |
| **Milky Way Satellites (Wolf, $N=46$)** | NFW Baseline | 2 | `1355.62` | `30.810` | ฐานเปรียบเทียบ | `1359.62` |
| **Milky Way Satellites (Wolf, $N=46$)** | Hybrid V9 (`320.37 pc`) | 3 | `804.44` | `18.708` | `-40.66%` | `810.44` |
| **Milky Way Satellites (Wolf, $N=46$)** | **Hybrid V10 (`235.9135 pc`)** | 3 | **`870.84`** | **`20.252`** | **`-35.76%`** | **`876.84`** |
| **Local Volume Superset (Wolf, $N=94$)** | NFW Baseline | 2 | `3264.30` | `35.482` | ฐานเปรียบเทียบ | `3268.30` |
| **Local Volume Superset (Wolf, $N=94$)** | Hybrid V9 (`320.37 pc`) | 3 | `3058.60` | `33.611` | `-6.30%` | `3064.60` |
| **Local Volume Superset (Wolf, $N=94$)** | **Hybrid V10 (`235.9135 pc`)** | 3 | **`3152.68`** | **`34.645`** | **`-3.42%`** | **`3158.68`** |
| **MW Clean dSph (Spherical Jeans, $N=40$)** | NFW Jeans | 2 | `225.95` | `5.946` | ฐานเปรียบเทียบ | `229.95` |
| **MW Clean dSph (Spherical Jeans, $N=40$)** | C1-Smooth V10 (`235.9135 pc`) | 3 | `235.45` | `6.364` | `+4.21%` | `241.45` |
| **MW Clean dSph (Spherical Jeans, $N=40$)** | Cored Soliton V9 (`320.37 pc`) | 3 | `227.10` | `6.138` | `+0.51%` | `233.10` |
| **MW Clean dSph (Spherical Jeans, $N=40$)** | **Cored Soliton V10 (`235.9135 pc`)** | 3 | **`228.73`** | **`6.182`** | **`+1.23%`** | **`234.73`** |
| **LV Clean dSph (Spherical Jeans, $N=82$)** | NFW Jeans | 2 | `754.66` | `9.433` | ฐานเปรียบเทียบ | `758.66` |
| **LV Clean dSph (Spherical Jeans, $N=82$)** | C1-Smooth V10 (`235.9135 pc`) | 3 | `771.69` | `9.768` | `+2.26%` | `777.69` |
| **LV Clean dSph (Spherical Jeans, $N=82$)** | Cored Soliton V9 (`320.37 pc`) | 3 | `689.72` | `8.731` | `-8.60%` | `695.72` |
| **LV Clean dSph (Spherical Jeans, $N=82$)** | **Cored Soliton V10 (`235.9135 pc`)** | 3 | **`677.06`** | **`8.570`** | **`-10.28%`** | **`683.06`** |

#### ข้อค้นพบสำคัญจากการทดสอบ Spherical Jeans
* **ชัยชนะของ V10.0 ในกลุ่มสมดุลท้องถิ่น (`LV Clean dSph`, $N=82$):** เมื่อคัดกรองระบบนอกสมดุล (`NON_EQUILIBRIUM_OUTLIERS`) ออก 12 แห่ง โปรไฟล์ **Schive/Robles Cored Soliton V10 (`235.9135 pc`)** ลดค่า $\chi^2$ เหลือ **`677.06`** ชนะทั้ง NFW (**`-10.28%`**, $\Delta\text{AIC} = -75.60$) และชนะรุ่น V9.0 เดิม ($\chi^2 = 689.72$)
* **ความเร็วกระจายตัว $\sigma_{\text{los}}$ ใน 5 กาแล็กซีมาตรฐาน (`MW N=46`):**
  * **Segue 1** ($r_{1/2} = 19.52\text{ pc}$): สังเกตการณ์ `3.97 km/s` $\rightarrow$ V10.0 ทำนาย **`4.13 km/s`** (แม่นยำกว่า V9.0 ที่ได้ `2.73 km/s`)
  * **Draco** ($r_{1/2} = 220.25\text{ pc}$): สังเกตการณ์ `9.55 km/s` $\rightarrow$ V10.0 ทำนาย **`9.45 km/s`**
  * **Sculptor** ($r_{1/2} = 223.23\text{ pc}$): สังเกตการณ์ `9.20 km/s` $\rightarrow$ V10.0 ทำนาย **`9.24 km/s`**
  * **Leo I** ($r_{1/2} = 229.10\text{ pc}$): สังเกตการณ์ `9.29 km/s` $\rightarrow$ V10.0 ทำนาย **`9.45 km/s`**
  * **Fornax** ($r_{1/2} = 695.33\text{ pc}$): สังเกตการณ์ `12.10 km/s` $\rightarrow$ V10.0 ทำนาย **`12.08 km/s`**

### 2.2 การสั่นพ้องหลุมดำ M87* และจุดอิ่มตัวของเมฆโบซอน
* **ค่าการจับคู่อะตอมความโน้มถ่วง ($\alpha_g$ ของ M87*):** ขยับจาก `1.3770` เป็น **`1.6041`** (ยังคงอยู่กลางหน้าต่างสั่นพ้องสูงสุด $[0.2, 2.0]$)
* **การอิ่มตัวแบบ Level-Mixing Equilibrium:** แรงผลัก $\lambda_{\text{V9}}$ กดมวลเมฆโบซอนให้อิ่มตัวที่ระดับ $M_{\text{cloud,sat}} / M_{\text{M87}^*} \sim 7.01 \times 10^{-13}$ ทำให้สูญเสียสปินเพียง $\Delta a_* \sim 10^{-12} \approx 0$ สอดคล้องกับค่าสปินสูงจากภาพถ่าย EHT ($\vert{}a_*\vert{} \gtrsim 0.5\text{--}0.9$)
* **เวลาหน่วงเสียงสะท้อนคลื่นความโน้มถ่วง ($\Delta t_{\text{V10}}$ ของ M87*):** $3.290 \times 10^6\text{ s}$ (เปลี่ยนแปลงเพียง $-2.3\%$ จาก V9.0)

### 2.3 การปรับปรุงสมการวิวัฒนาการแรงโน้มถ่วง $G_N(z)$ ในยุคแผ่รังสีเด่น
* เพิ่มพจน์ความหนาแน่นรังสี $\Omega_r(1+z)^4$ ($\Omega_r \approx 9.1627 \times 10^{-5}$ จาก $T_{\text{CMB},0} = 2.7255\text{ K}, N_{\text{eff}} = 3.044$) ในอัตราส่วนฮับเบิล $E(z)$
* **ผลลัพธ์ $\Delta G / G_0$:**
  * ยุคใกล้ ($z = 0.5\text{--}2.0$): **`+0.0990%`** ถึง **`+0.3933%`**
  * ยุค CMB ($z = 1100$): **`+3.5688%`** (เกณฑ์ Planck $< 5\%\text{--}10\%$)
  * ยุคสมดุลสสาร-รังสี ($z = 3400$): **`+4.2411%`** ($z_{\text{eq}} \approx 3436.8$)
  * ยุค BBN ($z = 10^8\text{--}10^{10}$): **`+11.4119%`** ถึง **`+14.6769%`** (ที่ $z = 10^9$ ได้ **`+13.0444%`**, เกณฑ์ BBN $< 10\%\text{--}20\%$)

---

## 3. รายการสิ่งที่ต้องทำเมื่อพร้อมอัปเกรดเป็น V10.0 อย่างเป็นทางการ (Release Checklist)

- [x] **1. รันทดสอบขยายผลบน `dwarf_all.csv` ($N = 94$) และ Full Spherical Jeans (`Clean dSph`, $N = 40, 82$):** เสร็จสมบูรณ์และยืนยันค่าแฮช SSOT ไม่เปลี่ยนแปลง
- [ ] **2. อัปเดตฐานข้อมูลกลาง (`rhit_v9_0_ai_ssot.json` $\rightarrow$ `rhit_v10_0_ai_ssot.json`):**
  - เพิ่มสูตรเชื่อม $f_a = M_I$ และอัปเดตค่า `m_eff_eV` เป็น `3.297879e-20`, `R_TF_vac_pc` เป็น `235.9135`, และ `alpha_g_M87` เป็น `1.6041`
  - ระบุข้อสังเกตเรื่องการวัดโพลาไรเซชันของ M87* ด้วย ngEHT และกลไก $T^\mu_{\ \mu} = 0$ รอบหลุมดำ
- [ ] **3. อัปเดตเคอร์เนลหลัก (`rhit_v9_0_audit_kernel.py` $\rightarrow$ `rhit_v10_0_audit_kernel.py`):**
  - คำนวณ `m_eff` จาก `M_I * sqrt(lambda_V9)` โดยตรง
  - เพิ่มพารามิเตอร์ตัวเลือก `Omega_r` ในฟังก์ชัน `compute_gn_evolution`
  - รันตรวจสอบ `self_audit()` เพื่อยืนยัน `AUDIT_PASSED` ($\chi^2 = 1.9421$, $\text{dof} = 4$)
- [ ] **4. อัปเดตเอกสารต้นฉบับ (ไทยและอังกฤษ):**
  - ปรับแก้ตัวเลขและคำอธิบายใน `Paper.md`, `Paper_TH.md`, ไฟล์ `.tex` และคอมไพล์ไฟล์ `.pdf` ใหม่ทั้งหมด
- [ ] **5. รวมสาขาและสร้าง Release V10.0:**
  - Merge สาขา `ws2/suchart-v10-candidate` เข้าสู่ `main` และสร้าง GitHub Release ใหม่เพื่ออัปเดตเวอร์ชันบน Zenodo

---

## 4. เอกสารอ้างอิงในสาขา
* `reports_and_v10_draft/RHIT_V10_Candidate_Development_and_Audit_Report.pdf`
* `reports_and_v10_draft/RHIT_V9_2026_Empirical_Benchmark_Report.pdf`
* `reports_and_v10_draft/RHIT_V9_M87_Bosenova_Spin_Audit.pdf`
