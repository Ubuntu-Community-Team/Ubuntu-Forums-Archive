---
title: "Fix for suspend on Vostro 1400 with nvidia driver"
date: 2009-01-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Jengu on 2009-01-30
Open /etc/default/acpi-support and change SAVE_VBE_STATE=true to SAVE_VBE_STATE=false. I've seen lots of threads suggesting more changes but for me that was all that was necessary. Posting here for googlers ;)

---

