---
title: "GNOME 3 Bugs"
date: 2011-10-19
forum: Desktop Environments
---

### Post by Pjautuvas on 2011-10-19
Hello, this is a problem with the Gnome 3. I tried to change the system font in settings and Gnome tweak, but nothing helped, the panel looks very ugly. In addition, when I open  windows, or I go to the Activities for approximately one second, windows pieces spills on screen. How to fix it?
This is screenshot:
[IMG]http://img708.imageshack.us/img708/4492/42322112.png[/IMG]
P.S. Sorry for my poor English.

---

### Post by Bao2 on 2011-10-19
Try this in a terminal that will reset the entire Unity to defaults:

unity --reset

---

### Post by Pjautuvas on 2011-10-19
Atfter that command Unity opens and still is that bug.

---

### Post by asadmalik on 2011-10-19
[IMG]http://imageshack.us/photo/my-images/684/29932058.png/[/IMG]

i am having the same issue with gnome 3 :

[[IMG]http://img684.imageshack.us/img684/2071/29932058.png[/IMG]]("http://imageshack.us/photo/my-images/684/29932058.png/")


[URL="http://imageshack.us/photo/my-images/684/29932058.png/"]
[/URL]

---

### Post by weelk on 2011-10-19
I've had the same thing with ATI additional drivers. If you run on ATI then you might have a problem. I have uninstalled the driver but problem remained. My desktop works best wit default drivers otherwise goes ape. So for me the only way was clean install and don't touch the drivers.

---

### Post by Pjautuvas on 2011-10-19
I use ATi cardand installed the drivers. I can't use Ubuntu without the drivers, becouse I can't set 1280x1024 resolution and use Effects.

---

### Post by ZoiaGuyver on 2011-10-19
There are some known bugs with the latest ATI drivers and Gnome-Shell, a few of the distros I use (Sabayon being one of them) disable Gnome-Shell due to the bugs, It's not actually gnome or the distros bug it's a bug in the Radeon drivers themselves. AMD/ATI said they were working to fix them, how long that will take is anyones guess.

Sorry to be the bearer of bad news, but for now if your running an ATI card for graphics I would suggest not trying to run gnome-shell on it.

P.S I have read that installing the opensource radeon drivers can fix some issues (it wont fix all of them) and the ATI catalyst 11.9 fixes some and raises others. Your welcome to try either of them as a solution, it may work on your system, I wouldn't guarantee it though. Also I wouldn't recommend the ATI binarys unless you know how to manually install them.

---

### Post by asadmalik on 2011-10-19
i did a fresh install and after the install, i had 2 options in the additional drivers for ati-
one of them was a post release update (which i think is an update to catalyst 11.9 from 11.8).
but this driver fails to install and i have to finally activate the older driver.

so maybe i have to live with the older drivers unless some help arrives from amd/ati:(

---

### Post by bladerunner6 on 2011-10-19
same problem i have with nouveau drivers on my old nvidia geforce fx 5200....

---

### Post by tonysathre on 2011-10-20
I'm having this exact problem too. It's awful because I can't stand Unity. I'm running on an HD5870.

> **weelk said:**
> So for me the only way was clean install and don't touch the drivers.

Did any of you notice this same problem in GNOME 3 on a clean install and not installing other drivers? Or does it only persist if you install additional drivers?

Tony

---

### Post by bladerunner6 on 2011-10-22
clean install

---

### Post by masgeeks on 2011-10-22
I had same issues with ATI fglrx drivers and gnome shell - and since I was so early on in the setup of the machine, I bailed and started again - was quicker and cleaner.  The non-proprietary drivers work just fine with gnome shell, but I don't do any gaming... so... gamers would not be happy I should think, to not be able to use the proprietary drivers...  :(  Don't get full 3D support without them, from what I understand...

---

### Post by BigCityCat on 2011-10-22
For the record intel graphics drivers are working good.

---

### Post by pheonixcoder on 2011-11-03
I have a ATI 4600 series card which is supported by Ubuntu11.10 release. With open source drivers gnome-shell mostly works fine, but i keep hitting few bugs 
e.g. 
all the windows i had opened in different workspace came to a single one when i hit the overview mode. 
One more issue i saw was in the overview mode if you hover over the window you will get an option to close it, this option is disappeared now. I can't explain why. :(

A bit annoying actually, but with ATI card gnome does tend to be moody.

---

