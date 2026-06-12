---
title: "Wallpaper problems post 10.10 upgrade"
date: 2010-10-05
forum: Desktop Environments
---

### Post by mattelation on 2010-10-05
I've just upgraded to Maverick (Studio, if that makes any difference), and am now having problems with the wallpaper. When I log on, I get the wallpaper from the default studio theme, as it was pre-upgrade, but as soon as the system starts loading startup programs, it disappears. If i go to change the wallpaper, the system locks up.

Some odd things too, as the system locks up, AWN Navigator, which I use, seems to open and immediately close many dialog boxes. Most of these icons are for a normal dialog box, but sometimes there is a Google Picasa icon in there too, which seems odd.

Also, the CPU chart in the screenlet that I run shoots up to 100%, and stays there.

I'm somewhere between a beginner and intermediate Ubuntu user, and normally find the answer to a problem with a quick google, but this has got me :confused::confused::confused:

Thanks in advance!

---

### Post by mattelation on 2010-10-06
Anyone?

---

### Post by Monosabio on 2010-10-09
> **mattelation said:**
> Anyone?

Same thing for me, I've just upgraded from 10.04 and I can only get Wallpapers back only if I disable to show Desktop Icons from Ubuntu Tweak.
If I enable 'Show Desktop Icons', I get a white background as Wallpaper.

---

### Post by mattelation on 2010-10-10
I tried that, definately had an effect but didn't bring back wallpaper, just caused a lot of processor use. Updated the system through Update Manager, and all seems to run fine now, so I'm sorted.

---

### Post by Monosabio on 2010-10-10
> **mattelation said:**
> I tried that, definately had an effect but didn't bring back wallpaper, just caused a lot of processor use. Updated the system through Update Manager, and all seems to run fine now, so I'm sorted.

I've solved my desktop problem by following this tutorial:

To Enable RGBA Transparency use this tutorial:
[http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html](http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html)
I'm using [Glassified MacOS Compiz Theme]("http://gnome-look.org/content/show.php/Glassified+MacOS+%28left%2Bright%29?content=125896")

---

### Post by shankru85 on 2010-10-10
Any other help ? I am terribly struck with this problem. This is making me feel bad for having upgraded. I really wonder how Canonical could release something with such a basic bug :( .When i try to change desktop background, thoushands of nautilus windows get opened and system freezes. Please help.

PS: I am kinda person who change wallpapers often :(

---

### Post by shankru85 on 2010-10-11
Hi,

Anyone found any solution to this problem ? :(

---

### Post by mitulv4u on 2010-10-11
Hey i found this on
[http://ubuntuforums.org/showthread.php?t=874191](http://ubuntuforums.org/showthread.php?t=874191)

and it worked for me...I killed Nautilus, and relogged in..

*************************************
Searched for GNOME-related problems rather than UBUNTU-related, and found the solution in [http://www.linuxquestions.org/questions/linux-newbie-8/gnome-desktop-icon-disappeared-27724/](http://www.linuxquestions.org/questions/linux-newbie-8/gnome-desktop-icon-disappeared-27724/)

Basically, nautilus is the process I assumed in charge, and 
killall nautilus
will cause it to go away and being restarted - and voila: Icons and Heron is back.

---

### Post by shankru85 on 2010-10-11
> **mitulv4u said:**
> Hey i found this on
[http://ubuntuforums.org/showthread.php?t=874191](http://ubuntuforums.org/showthread.php?t=874191)

and it worked for me...I killed Nautilus, and relogged in..

*************************************
Searched for GNOME-related problems rather than UBUNTU-related, and found the solution in [http://www.linuxquestions.org/questions/linux-newbie-8/gnome-desktop-icon-disappeared-27724/](http://www.linuxquestions.org/questions/linux-newbie-8/gnome-desktop-icon-disappeared-27724/)

Basically, nautilus is the process I assumed in charge, and 
killall nautilus
will cause it to go away and being restarted - and voila: Icons and Heron is back.


First of all, thanks for caring to reply to the thread. I am not sure if the problem you have referred to, is same as the problem that i am facing. And i am facing it in Maverick meerkat (ubuntu 10.10) and not older ubuntu/gnome. So i really doubt if it will solve my problem. Anyway will try and update. Once again, thanks for caring to reply.

---

### Post by shankru85 on 2010-10-11
This is quite unbelievable. Suddenly after a few reboots, the problem seems to be gone :confused: . Anyway, i will keep a watch on this. Hope i dont hit any problems.

---

### Post by samortan on 2010-10-11
Well, i would suggest you to keep the "Classic" theme selected in your pc. It has double benefit. One, your pc will work at faster speed than the present speed. Second the look of your pc will become some what like professional.

---

### Post by furious_george on 2011-02-20
After some reluctance, I recently upgraded from Lucid to Maverick (not studio, however) and am faced with the same issue.  I can see the wallpaper through the transparent panels, but otherwise it is white.

Disabling "Show Icons" on Desktop works, but is hardly a proper solution.  Anyone else have this problem?

---

### Post by zarulhairee on 2011-11-15
this post might be old but it fixed my problem

[http://ubuntuguide.net/no-background-wallpaper-problem-after-upgrading-to-ubuntu-11-04-natty](http://ubuntuguide.net/no-background-wallpaper-problem-after-upgrading-to-ubuntu-11-04-natty)

---

