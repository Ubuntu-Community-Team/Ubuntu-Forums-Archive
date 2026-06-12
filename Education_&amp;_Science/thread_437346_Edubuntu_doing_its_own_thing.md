---
title: "Edubuntu doing its own thing??????"
date: 2007-05-08
forum: Education &amp; Science
---

### Post by mr_larrynm on 2007-05-08
:mad: :mad: :mad: :mad: :mad: 

WTF!!!!!!

I downloaded the 7.04 of Edubuntu and was happy with everything on the LiveCD.  I ran the install and instead of having everything running on the computer just how it was on the CD I find out that the entire education section is missing!!!!!!!!!!!!!!!!!!!!!!!!!

Thinking that maybe I missed some minor change in the install process, I rebooted off of the LiveCD and reran the install.  I sat in rapt attention watching everything that was happening and was shocked to see the install process removing all of the educational stuff from the install after the hardware detection phase (@ 98% complete).

Maybe someone here would kindly explain this to me.   I mean I was pulling this down for my children and their day school's computers so I would not have to worry about doing anything extra to the install.

---

### Post by epimetheus79 on 2007-06-11
"the entire education section is missing!"

Same problem here...

---

### Post by Jussi01 on 2007-06-11
Try using the alternate edubuntu cd (I didnt know there was a live edubuntu cd) I just installed it last week on my brothers pc, works perfectly.

---

### Post by LaserJock on 2007-06-12
Hi, I'm one of the Edubuntu developers. Let me explain the situation with this a little bit.

During the Feisty development cycle we decided that we really needed to split Edubuntu up into 2 CDs. One of the reasons was that we were always running out of room on the single CD and had to remove some things from what Ubuntu installs, like mono apps and some language packs. Secondly, we want to add more educational applications to Edubuntu like moodle, teacher tools, and secondary/university level apps.

Unfortunately, an unforseen consequence of splitting Edubuntu into two CDs is that the LiveCD installer, ubiquity, does not install the packages that come on the 2nd CD. This will be fixed in Edubuntu 7.10 but for 7.04 the recommended method is to use the Classroom Server Addon CD (which is somewhat misnamed because it can actually be used on any *buntu machine) to install the educational apps. The Desktop CD has never been the recommended installation method in Edubuntu because it doesn't include the automatic LTSP server setup and you can do virtually any installation you need from the Classroom Server CD (alt disc).

I'm really hopeful that we can get all of the disc issues (including misleading naming and wording on the download pages) fixed for Edubuntu 7.10, but being the first *buntu with 2 CDs caused some growing pains and that's where the problem came from.

-LaserJock

---

