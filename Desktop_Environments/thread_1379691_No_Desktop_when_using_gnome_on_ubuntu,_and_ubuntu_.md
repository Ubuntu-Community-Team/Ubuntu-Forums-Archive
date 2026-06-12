---
title: "No Desktop when using gnome on ubuntu, and ubuntu only"
date: 2010-01-12
forum: Desktop Environments
---

### Post by QofDeath420 on 2010-01-12
So, I installed windows 7 the other day and other than having to figure out how to make grub reappear every thing seemed almost fine, except one little thing. my desktop is completely black now. hmmm. no cool bakground and no icons. yeah, its not the end of the world but its annoying and I'd like things to work. 

Here where things get more interesting though...

I used hirens to wipe my harddrives clean to start fresh, then reinstall xp, windows 7 and ubuntu, still no desktop. So I did it again and didn't install 7, and still no desktop, then I did it again and just installed ubuntu, and still no desktop. Then I tried pulling out my big bag of distros. It seems like the ubuntu linux variants that run gnome (mint, superOS, UbuntuStudio in my case) fail, though Kubuntu and other KDE based OSes work fine, as well as openSUSE and Fedora (using gnome or KDE). This strikes me as an odd problem, and it didn't happen till I went and decided that I was gonna try microshit's latest subpar offereing. Regardless it's not on my harddrives at all, I want to use ubuntu with gnome becasue it's the best linux i've used for me (and I am not a fan of KDE), any help could be appriciated.
A little about my system if it helps:
Running a Pentium 4 with 1gb of ram
ATI all-in-woinder 9000 tv tuner/graphics card
gigabyte motherboard
Just let me know if you need anyother info, and anyhelp will be greatly appreciated

---

### Post by Jaesin on 2010-01-12
do you have a command line or just a blank screen?  If you have a command line, type "sudo apt-get install ubuntu-desktop" and that should reset it or "sudo apt-get install gdm ubuntu-desktop" It would also work from kde but I don't know what kde's "Apt-get" command is.

---

### Post by QofDeath420 on 2010-01-12
no its not the CLI, it just a black desktop. To be sure I drug some files onto it, then tried again, and it asks if I want to overwrite the files, so I guess the desktop is there, technically speaking, but its not visible. Also when you log in or out you see it for about a second before it goes black, its there, just not visible.

---

### Post by Jaesin on 2010-01-12
try ALT-F2 then type --restart

also try ALT -F2 --restart metacity

---

### Post by QofDeath420 on 2010-01-12
that didn't work it told me no such file or directory...
anyother ideas?

---

### Post by QofDeath420 on 2010-01-13
I just tried installing ubuntu studio from the repositories, and I had a desktop after I restarted, then this morning after I turned my computer back on, no desktop again... What the hell...

---

### Post by nothingspecial on 2010-01-13
Do you have a seperate /home

That`s the only reason I can think of this happening on any gnome install.

Hit Alt-F2 and type gconf-editor

go apps > nautilus > preferences and make sure "show desktop" is checked.

---

