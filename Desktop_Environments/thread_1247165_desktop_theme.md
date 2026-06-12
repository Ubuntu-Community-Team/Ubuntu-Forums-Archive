---
title: "desktop theme"
date: 2009-08-22
forum: Desktop Environments
---

### Post by AmerNewbieInDE on 2009-08-22
how do i transfer my desktop from one pc to another?

---

### Post by fela on 2009-08-22
If you installed the themes by dragging them to the appearance applet, the theme folders will be inside /home/$USER/.icons and /home/$USER/.themes. To transfer them to a different Ubuntu installation just copy the right theme folder (the name of the theme) to those folders on the other installation. You can use something such as a flash drive to copy them.

---

### Post by AmerNewbieInDE on 2009-08-22
can i just copy my whole home folder? the systems are identical, well, maybe some different programs. i just reloaded this pc so dont have everything back on

---

### Post by fela on 2009-08-22
> **AmerNewbieInDE said:**
> can i just copy my whole home folder? the systems are identical, well, maybe some different programs. i just reloaded this pc so dont have everything back on

I don't advise replacing your new home folder with the old one, as programs store their settings in directories in your home folder. You'll have to press ctrl+H to see these directories in the file browser, as they begin with a period (.) and so are hidden directories.

It's much easier and faster to just copy the .themes and .icons directories.

---

