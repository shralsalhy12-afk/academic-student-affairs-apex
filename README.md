# academic-student-affairs-apex
Oracle APEX Academic &amp; Student Affairs Management System with Custom UI and PL/SQL Triggers
# Academic & Student Affairs Management System

نظام إلكتروني متكامل لإدارة شؤون الطلاب والأقسام الأكاديمية، تم تطويره باستخدام بيئة **Oracle APEX** وقواعد بيانات **Oracle**، مع تصميم واجهات مستخدم عصرية (UI/UX) مخصصة.

## 🚀 مميزات المشروع (Features)
- **لوحة تحكم رئيسية (Dashboard):** تصميم عصري ببانر ترحيبي، صور تفاعلية، وقوائم مرتبة لتسهيل التنقل (تم تخصيصها في صفحة 2).
- **إدارة الطلاب:** شاشات إدخال وتعديل (`Modal Dialogs`) مصممة بثيم فاتح ومريح للعين مع حقول منظمة.
- **إدارة الأقسام الأكاديمية:** نظام متكامل لربط التخصصات والخطط الدراسية مع بانر مضيء (`Glowing List Banner`).
- **الأتمتة وقواعد البيانات (PL/SQL):** استخدام `Triggers` مخصصة لتوليد أرقام السجلات (`DEPT_ID`) تلقائياً ومنع أخطاء القيم الفارغة (`NULL`).

## 🎨 التقنيات المستخدمة (Tech Stack)
- **Frontend & UI:** HTML5, CSS3, Google Fonts (Cairo), Custom Inline CSS.
- **Backend & Database:** Oracle Database, PL/SQL (Triggers & Sequences).
- **Platform:** Oracle APEX.

## 📂 كود الأتمتة وقواعد البيانات (Code Snippets)
تم استخدام محفز برمجي (`Trigger`) لتوليد الأرقام التسلسلية للأقسام تلقائياً لضمان سلامة البيانات:
```sql
CREATE OR REPLACE TRIGGER bi_DEPARTMENT 
BEFORE INSERT ON DEPARTMENT 
FOR EACH ROW
BEGIN
    IF :NEW.DEPT_ID IS NULL THEN
        SELECT NVL(MAX(DEPT_ID), 0) + 1 INTO :NEW.DEPT_ID FROM DEPARTMENT;
    END IF;
END;
/
