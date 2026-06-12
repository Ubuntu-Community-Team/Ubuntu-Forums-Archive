---
title: "Assaultcube help"
date: 2007-08-15
forum: Gaming &amp; Leisure
---

### Post by noobonastick on 2007-08-15
Hi i am very noob. Could someone please tell me how do i  change my settings to:

    * 800x600@16bpp
    * Antialiasing: OFF
    * Anisotropic Filtering:OFF

in assaultcube?. It doesnt exactly tell you in the readme...

thx for ur time

---

### Post by Sockerdrickan on 2007-08-15
Well the last two you probably have to change in sudo nvidia-settings
The first one in the cfg file

---

### Post by noerrorsfound on 2007-08-15
> **noobonastick said:**
> 
    * 800x600@16bpp
I don't know about 16bpp but open the startup script (assaultcube.sh) and after 
```
exec ${CUBE_DIR}/bin_unix/${MACHINE_NAME}${SYSTEM_NAME}client
```

Put a space and put ```
-w800 -h600
```

---

### Post by orduek on 2007-10-31
I thihk i have a resolution problem myself but can't find the .sh file.
There is a big Config folder and i think maybe it's there.
can someone help guide me to the right place?

---

