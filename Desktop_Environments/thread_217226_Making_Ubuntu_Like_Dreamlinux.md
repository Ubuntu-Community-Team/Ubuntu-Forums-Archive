---
title: "Making Ubuntu Like Dreamlinux"
date: 2006-07-16
forum: Desktop Environments
---

### Post by Protostar on 2006-07-16
Hello all. I want to know how I go about making Ubuntu exactly like Dreamlinux. I tried that distro (XGL edition) and really liked it, but unfortantely I couldn't get it to display my desired resolution and it didn't recognize my wireless network card. I know I will have to install Xubuntu desktop, but where do I go from there? TIA for you help.

---

### Post by ragoo on 2006-07-16
why couldn't you just try to make Dreamlinux work?
getting the resolution right doesn't sound too hard, andif the wireless card is possible to use with xubuntu, it should be possible to make it work in some other linux distro too i guess..

to make it look excactly the same, download all the packages needed that are used in dreamlinux, and find the same themes\skins etc.. that's used in dreamlinux, and apply them in Xubuntu. that might work.

---

### Post by Protostar on 2006-07-17
[quote=ragoo]why couldn't you just try to make Dreamlinux work?[/quote]

I tried everything i knew how as far as the resolution is concerned. I did sudo dpkg-reconfigure xserver-xorg and it didn't give me the option to change the screen resolution. I didn't even get around to trying to get the wireless card to work, as the resolution was so unbearable (640x480, on a 21 inch monitor).

[quote=ragoo]to make it look excactly the same, download all the packages needed that are used in dreamlinux, and find the same themes\skins etc.. that's used in dreamlinux, and apply them in Xubuntu. that might work.[/quote]

I had already thought of that, but I thought maybe someone had done it before and would have someone along the lines of a howto or something. Oh well, Google time I guess.:p

---

### Post by %hMa@?b&lt;C on 2006-07-17
well, it uses xfce, so you can do
sudo aptitude update && install xubuntu-desktop
check around here for icons and stuff
[http://xfce-look.org/](http://xfce-look.org/)

---

### Post by rejser on 2006-09-15
Found an easy solution?
Shouldn't it be possible to install from dreamlinux repos (they are on debian if I remember correct). 
They have a beautiful thing going with the engage kicker, xgl and xfce 4.4 (with the amazing thunar)

---

### Post by Markkreuzz on 2006-09-15
you can edit etc/X11/xorg.conf and remove or comment(using # in the front) all the resoulutions you don't want to use e.g. 600x400, 800x600. and also be careful of the sync range as this could mess up your screen if not set properly.

---

### Post by YanalAlHasan on 2006-09-15
I think i had a similar problem with resolution you can change it by pressing (control and alt) then press as i think one of the buttons beside the numlock (/,*,- or +) it should change the resolution to something readable.But i am sure that dreamlinux is the worst linux in the whole world.Take my word and dont use it.The graphical copy paste is very bad it doesnt paste even if you have permission to.And also it crashes a lot.every time it crashed i reinstall it again (i did that for 8-12 times!!) until i realised that the problem is with it.So dont ever consider using it.
Hope this helps

---

### Post by La_Frenezo on 2006-09-15
> **Protostar said:**
>  ...but unfortantely I couldn't get it to display my desired resolution ...

Did you already try to edit your "/etc/X11/xorg.conf" file? If not try adding your desired screen resolution.

E.g if your file looks like this:
.
.
Modes      "1024x768" "800x600" "640x480"
.
.

...and you want to have "1280x1024", add "1280x1024" at every of those lines.
.
.
.
Modes      "1280x1024" "1024x768" "800x600" "640x480"
.
.
.

Good luck!

---

### Post by Markkreuzz on 2006-09-15
or you can just leave Modes "1280x1024" in there and remove the other resolution, that should force X to use that resolution, else you will get an error message

---

