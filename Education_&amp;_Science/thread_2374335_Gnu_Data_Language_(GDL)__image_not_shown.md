---
title: "Gnu Data Language (GDL) : image not shown"
date: 2017-10-14
forum: Education &amp; Science
---

### Post by szrozr on 2017-10-14
Hi, I am new to coding with GDL, I made an example to show a JPEG image but the result is blue screen could anybody help me?

Here is my code:
PRO get_image
GDL_STARTUP='/home/sezer/.gdl_startup'
file = filepath('gul.jpeg', ROOT_DIR='/home/sezer/Masaüstü')
read_jpeg, file, image
window, xsize=275, ysize=183
device, decomposed=0
loadct, 25
tvscl, image
END

SS link: [https://imgur.com/a/Jc3h0](https://imgur.com/a/Jc3h0)

---

