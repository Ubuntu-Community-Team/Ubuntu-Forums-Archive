---
title: "Compiz with Dual Monitors"
date: 2009-04-11
forum: General Help
---

### Post by dr.silly on 2009-04-11
I just installed a second monitor to find that compiz has been disabled. When I attempt to run compiz --replace & i get

```
sam@sam-desktop:~$ compiz --replace & 
Checking for Xgl: [3] 7223
sam@sam-desktop:~$ not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1024) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 

[2]-  Done                    compiz --replace

```

both monitors are set to 1280x1024 resolution
i don't know whether xinerama or twinview is enabled, how do i determine?

any help is appreciated

---

### Post by Darkshade on 2009-04-11
What video card do you have and what drivers are you using?

---

### Post by ad_267 on 2009-04-11
If you're using an nvidia card then run "sudo nvidia-settings" and use TwinView.

---

### Post by dr.silly on 2009-04-11
im not using nvidia so i guess that rules out twinview

my xorg.conf says it is using the intel driver and apparently i have the 82915G/GV/910GL intel integrated graphics controller blah blah blah

---

### Post by dr.silly on 2009-04-12
Would it work if I decreased the resolution?

---

### Post by dr.silly on 2009-04-12
when i decrease my screen resolution compiz works fine but still not functional at a reasonable resolution :(

---

