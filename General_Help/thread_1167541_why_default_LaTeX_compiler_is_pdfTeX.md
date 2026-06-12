---
title: "why default LaTeX compiler is pdfTeX?"
date: 2009-05-23
forum: General Help
---

### Post by baosheng on 2009-05-23
hi, I am using Ubuntu 9.04. But one thing made me very annoyed. The default LaTeX compiler is pdfTeX. I really do not understand why. I want DVI file and my images are in EPS format. And I need to work with BiBTeX. Now BiBTeX can't work coz no proper aux file can be generated.

---

### Post by hugmenot on 2009-05-23
pdftex includes the old latex. If you just run "latex" then you will get your usual dvi file.
"latex" symlinks to "pdftex" but the functionality is the same.

---

