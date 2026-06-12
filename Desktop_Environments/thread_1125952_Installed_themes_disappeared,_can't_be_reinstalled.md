---
title: "Installed themes disappeared, can't be reinstalled"
date: 2009-04-14
forum: Desktop Environments
---

### Post by dbsoundman on 2009-04-14
I downloaded several (4 or 5) themes from gnome-look.org tonight to add to my Ubuntu 8.10 install. Instead of installing and applying only the one I wanted, I decided to just install all of them first, then choose the one I wanted from the preview in the "themes" dialog window. I installed them through that same dialog window, and they all supposedly installed correctly. However, none of them showed up as applicable themes in the theme chooser window (i.e. they just aren't there), and when I look in /usr/share/themes, I see other themes that I may have installed at some point which also do not show up, such as "Redmond", but none of the themes I just installed even have folders in there. Additionally, if I try to install these themes again, I get an error message saying something like it can't move over the directory (I'm guessing this is meaning that it believes there's already a directory of that name in existence in that path).

Any ideas of what I can do here? Thanks!

-Dan

---

### Post by ahbart on 2009-04-15
If you installed these theme as a normal user you will find them in /home/username/.Themes

---

### Post by Jakey_TheSnake on 2009-04-15
> **ahbart said:**
> If you installed these theme as a normal user you will find them in /home/username/.Themes

^ delete them from that directory, then you can reinstall.

---

### Post by dbsoundman on 2009-04-15
Thanks! I figured out my problem was twofold: I wasn't looking in the /home/dan/.themes file, and the things I downloaded were not total themes like Clearlooks, for example; they were pieces basically, so I had to set a theme like Clearlooks, then "customize" it. I already moved the themes to the /usr/share/themes directory too so I actually did myself a favor overall. Thanks for the help!

-Dan

---

