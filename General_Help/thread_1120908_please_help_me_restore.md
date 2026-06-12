---
title: "please help me restore"
date: 2009-04-09
forum: General Help
---

### Post by crazypeppo on 2009-04-09
(please help).
I am running ub 8.04 i have alot of custom settings and apps and don't want to re-install.
problem - I downloaded updates and installed open ssh server, putty and virtual box. I was required to restart, when i did it loaded settings and gui came up but all white...it appeared menus were working but no text all white.
so far - i rebooted in safe mode and went in synaptic and deleted all files which i installed last night. I did not delete any of the updates. I rebooted in normal and same thing... all white
I do not know what files i can delete in order to restore to where it was. Can any one please give me some guidance? 
Thank you for reading
Doug

---

### Post by ajgreeny on 2009-04-09
Just in case it's a configuration of one of the new programs installed make sure you "Complete removal" in synaptic, rather than just remove.  It could make a difference, but I doubt it, I'm afraid.

What were the updated packages as it seems more likely that there was something in those that caused the problem rather than the new apps you installed.  Have a look in Synaptic at the File > History to see what upgraded.  Looking at my 8.04, I see there was a new kernel and it is possible that you have this and just need to reinstall any proprietary graphic driver you may have installed in the past.

Here's my list since 27 April:-
libkrb53 (1.6.dfsg.3~beta1-2ubuntu1) to 1.6.dfsg.3~beta1-2ubuntu1.1
doc-base (0.8.7) to 0.8.7ubuntu1
[B]linux-headers-2.6.24-23 (2.6.24-23.48) to 2.6.24-23.52
linux-headers-2.6.24-23-generic (2.6.24-23.48) to 2.6.24-23.52
linux-image-2.6.24-23-generic (2.6.24-23.48) to 2.6.24-23.52[/B]
tzdata (2009b-0ubuntu0.8.04) to 2009d-0ubuntu0.8.04
tzdata-java (2009b-0ubuntu0.8.04) to 2009d-0ubuntu0.8.04
wine (1.1.17~winehq0~ubuntu~8.04-0ubuntu1) to 1.1.18~winehq0~ubuntu~8.04-0ubuntu1
libsndfile1 (1.0.17-4) to 1.0.17-4ubuntu0.8.04.1
libssl0.9.8 (0.9.8g-4ubuntu3.4) to 0.9.8g-4ubuntu3.5
openssl (0.9.8g-4ubuntu3.4) to 0.9.8g-4ubuntu3.5
w32codecs (20071007-0medibuntu2) to 20071007-0medibuntu2.1
firefox (3.0.7+nobinonly-0ubuntu0.8.04.1) to 3.0.8+nobinonly-0ubuntu0.8.04.2
firefox-3.0 (3.0.7+nobinonly-0ubuntu0.8.04.1) to 3.0.8+nobinonly-0ubuntu0.8.04.2
firefox-3.0-gnome-support (3.0.7+nobinonly-0ubuntu0.8.04.1) to 3.0.8+nobinonly-0ubuntu0.8.04.2
firefox-gnome-support (3.0.7+nobinonly-0ubuntu0.8.04.1) to 3.0.8+nobinonly-0ubuntu0.8.04.2
xulrunner-1.9 (1.9.0.7+nobinonly-0ubuntu0.8.04.1) to 1.9.0.8+nobinonly-0ubuntu0.8.04.1
xulrunner-1.9-gnome-support (1.9.0.7+nobinonly-0ubuntu0.8.04.1) to 1.9.0.8+nobinonly-0ubuntu0.8.04.1

---

### Post by lavinog on 2009-04-09
First, remove your email address from the post unless you want to be spammed.

The white screen problem is frequently an issue between compiz and video drivers.
a temp fix would be to dissable compiz (probibly easiest to do by removing compiz from with apt-get)
You can reinstall compiz when the problem is fixed.
What video card do you have, and what video driver are you using?

---

### Post by crazypeppo on 2009-04-09
done

---

### Post by crazypeppo on 2009-04-09
done

---

