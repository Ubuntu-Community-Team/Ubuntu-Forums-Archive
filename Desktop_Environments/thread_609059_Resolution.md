---
title: "Resolution"
date: 2007-11-10
forum: Desktop Environments
---

### Post by Bigtrigger on 2007-11-10
Hey guys im having troubles with my desktop resolution . i try to change it in the ubuntu screen resolution and it says it changes but nothing happens . so i installed envy for my nvidea card and tried to use the nvidea  software and that gives and error . im not @ home to give the error but if anyone has had a problem similar and has a fix its much appreciated. :)

---

### Post by Bigtrigger on 2007-11-11
here is the error i get when i try to change the setting withg the nvidea - applications > system tools> nvidea settings 

Failed to set MetaMode (13) 'CRT-0: 1024x768_60 @1024x768 +0+0' (Mode 1024x768, id: 64) on X screen 0

Would you like to remove this MetaMode?

any one ?

---

### Post by Bigtrigger on 2007-11-12
Bump

---

### Post by linux4begin on 2007-11-12
Dear 

can you give us more info, more logs, and more hardware details.
so atlease we can have a look in it and can reply you few possibilitied.

---

### Post by PCZahra on 2007-11-12
Last week before I left for the weekend, I had a screen resolution of 1280x1024 using the ATI driver (for Radeon 9200SE) before I turned the computer off. This morning I turned it back on. Screen is 1024x768. I change it back, it says it changes, nothing has happened. I change the driver. It says it changes, nothing has happened. No error messages, the only messages I get say it's working fine.

---

### Post by ironchef on 2007-11-12
> **PCZahra said:**
> Last week before I left for the weekend, I had a screen resolution of 1280x1024 using the ATI driver (for Radeon 9200SE) before I turned the computer off. This morning I turned it back on. Screen is 1024x768. I change it back, it says it changes, nothing has happened. I change the driver. It says it changes, nothing has happened. No error messages, the only messages I get say it's working fine.

I'm having the same exact problem with the same setup (Ati driver/Radeon 9200SE)

---

### Post by faical117 on 2007-11-12
I have the same problem ,pls solution !!!!   :mad:

---

### Post by PCZahra on 2007-11-12
did either of you play around with the Test button before the problem started?

---

### Post by ironchef on 2007-11-13
I just found that going to System--->Preferences--->Screen Resolution and setting the resolution there seems to override the problems with using System--->Administration--->Screen and Graphics

---

### Post by PCZahra on 2007-11-13
> **ironchef said:**
> I just found that going to System--->Preferences--->Screen Resolution and setting the resolution there seems to override the problems with using System--->Administration--->Screen and Graphics

Not here.

---

### Post by PCZahra on 2007-11-14
Well, I solved mine.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
there was a bunch of duplicated gibberish in my xorg.conf, so I used that to rebuild it and then restarted gnome. I was then able to fix up the screen no problem

---

