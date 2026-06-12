---
title: "Refersh rate problem"
date: 2006-08-12
forum: Desktop Environments
---

### Post by arnie_ on 2006-08-12
My screen is fuzzy in Ubuntu. The problem is I got the wrong refresh rate. In Windows I could choose between 5 or 6 refresh rates. It was just one that gave a clear picture. Think it was 70 hz. In Ubuntu I can just choose between two, 60 and 75 hz. If i modify xorg.conf to run at 70hz and restart X I get a lower resolution. I've also set vrefresh and hrefresh to the recommeded values of my monitor.

I have the nvidia driver installed. I've a Geforce FX5900XT. My monitor is a Samsung syncmaster 191T. Here's my xorg.conf:[http://pastebin.se/3407](http://pastebin.se/3407)

Any suggestions?

---

### Post by NullaPax on 2006-08-13
I have the same problem. I can only get 60hz :( 

Any help for us out there ?

---

### Post by scotty2hott2k on 2006-08-13
its a bug in the new nvidia drivers you need to use the Option "UseEDID" "False" option in your xconfig

after whiuch your card section should look like:

> 
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option "UseEDID" "False"
EndSection


then just restart X and you can select any resolution/refresh rate you put in your X config, beware as it will let you choose modes your hardware wont work with.

---

