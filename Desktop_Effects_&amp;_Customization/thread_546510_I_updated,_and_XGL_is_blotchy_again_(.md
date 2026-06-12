---
title: "I updated, and XGL is blotchy again :("
date: 2007-09-08
forum: Desktop Effects &amp; Customization
---

### Post by darkhacker902 on 2007-09-08
Ok, let me go through some background first.

Im Running a Gateway MT6452
1gb Ram
ATI Radeon Xpress 1150M (200m series)
160GB HD.
Ubuntu Ultimate.

So About a month ago, I wanted desktop effects. Yup. Searched and searched and searched, and FINALLY Got Compiz Fusion working. After breaking, and reconfiguring X, I Finally got it, By installing the Fglrx Drivers through a terminal, because X was broken at the time. So, Apparently, I got it working, and when I booted XGL, it was all nice and clean, and everything worked and I was so happy.


Well, this morning, It said I needed to update, and some involved gnome, and compiz, So, What would you normally do? I updated. All happy and giddy. And while that was going, I was looking through the boot up manager, and saw some stuff like HP Printing assistant, and since I never print anything, I was like, pft, I dont need that. Well, I unchecked that, and a few other things, Because They didnt pertain to any work I do whatsoever, so I unchecked em, Finished my update, and compiz stopped working because I accidentally pressed ctrl+S and moved my mouse, which activated the water, and it makes my computer completely slow down. I was not worried about this, because it has happened frequently, so I wait around 5 minutes, and I just open a terminal, type in compiz --replace, and It was all better. (oddly, water effects work in beryl, just not compiz...) Well...It wasnt fixing. So I had to ctrl+alt+backspace. When I did, and logged back on, XGL was all blotchy again. I nearly peed myself, and cried, in anger, and in sadness. WELL, Come to find out, as I log back into Gnome, that im using the freakin Mesa Drivers again. So WHAT DO I DO????


And Also, if anyone can tell me how to reconfigure X in a terminal session, I would love that, because JUST IN CASE...ya know :P.

I will write it down, so I will remember.


Thanx for any help :)

---

### Post by soniiic on 2007-09-09
this could be the first time i've ever replied to a post on this forum as i am very linux unintelligable, but i am sorting out XGL on an ATi card myself and looked through this this morning:

> After kernel updates

After every update of the kernel (linux-image-<arch>), you will need to recompile the kernel module (make sure to get the latest linux-headers too) as explained under the installation section. After you recompile the module, you can regain direct rendering by logging into a console (ctrl+alt+f1) and typing:

sudo /etc/init.d/gdm stop (kdm if you use Kubuntu)
sudo rmmod fglrx (even if this command fails, go on)
sudo modprobe fglrx
sudo /etc/init.d/gdm start (again, Kubuntu users type kdm)

source: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by darkhacker902 on 2007-09-09
Yeah, But this wasnt a kernel update. It was just the package manager, updating some of my packages. Plus I tried that, and it didnt work :(.

---

