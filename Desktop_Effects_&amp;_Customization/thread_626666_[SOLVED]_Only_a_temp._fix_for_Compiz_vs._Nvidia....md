---
title: "[SOLVED] Only a temp. fix for Compiz vs. Nvidia...why?"
date: 2007-11-29
forum: Desktop Effects &amp; Customization
---

### Post by Motorhead Kaze on 2007-11-29
I first tried Compiz with Feisty and had lots of problems, but finally played with it enough that I got it working for a little while. Generally I had title bars with no cube, or a cube with no title bars, but once I had them all! (Then I installed Emerald & everything went to poo.)  When I upgraded to Gutsy, Compiz was in the Repos. I was excited and I followed all the things I'd done to make Compiz work before, but with negative results. As usual I read many forum entries and I did many things.  

Compiz started working when I did this:

1. I installed Compiz from [http://phorolinux.com/how-to-install...sy-gibbon.html](http://phorolinux.com/how-to-install...sy-gibbon.html) Did NOT install Emerald. Paused here before going on to "Running Compiz Fusion". I stayed in Metacity till I was all done. (That messed me up once before)

2. Installed the "Compiz Fusion Icon Button". (Useful for selecting your window manager - Metacity or Compiz - and other good things.)

git-clone git://anongit.opencompositing.org/users/crdlb/fusi on-icon

cd fusion-icon

sudo make install

3. Since I have an Nvidia vid card, I had to edit /etc/X11/xorg.conf It is apparently important to first, back up /etc/X11/xorg.conf so I opened a terminal:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_back up

Then, typed in the following command:

sudo gedit /etc/X11/xorg.conf

Scrolled down to the "Screen" section, and inserted the following lines:

Option "AddARGBGLXVisuals" "true"
Option "AddARGBVisuals" "true"

Made sure that between the word "Option" and "AddARGBVisuals" to use a TAB and not spaces, as that was a problem when I used Feisty.

* (just in case you need to revert back to the original xorg.conf type:
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

4. Went to system/preferences/appearance/visual effects and clicked "Normal". When I did that, the title bars in Metacity went out, but right away went to the Compiz Fusion Icon button/select window manager and switched to Compiz and everything was cool. (BTW, I tried clicking "Extra" and the title bars remained off).

5. I clicked "Reload Window manager" in the Compiz Fusion Icon button, and everything worked and I typed this little thing about "How to get Compiz to work"....... *THEN* I restarted Gnome and my title bars were gone.  I switched back to Metacity, went back to visual effects, clicked "None" then immediately back to "Normal" turned Compiz back ON and again everything Compiz works.  My question is...

**WHY?** I restarted Gnome once and my title bars were gone again. I messed with visual effects settings again, Compiz came back.  Starting the computer the next morning, Compiz works great.  This isn't a TV where we pound the side of it and the screen comes back, so what gives?

I also have no idea why Compiz out of the Repos won't work for me, but it doesn't.

P.S. for people who want the Compiz Fusion Icon to start automatically at login,
go to System/Preferences/sessions and in the "Startup programs" tab, click "Add" and type in this info:
Name : Compiz fusion icon
Command : /usr/bin/fusion-icon

for Compiz it's the same, only type:
Name: Compiz
Command: compiz --replace gconf

Note to advisors: "Push Alt+F2 Compiz --replace" isn't good advice for someone with this lack-of-title-bar trouble. Once Compiz is broken, there's no Alt+F2 to use. You need to open a Terminal and type it in. And for those of you who need to get Metacity (default) running again, so you can follow the advice, open a terminal and type metacity --replace, THEN you can go to Alt+F2 and type it again. (Let me know if there's a better way, but for today, that worked fine.)

---

### Post by Znort_Ubern00b on 2007-11-29
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
 try that in terminal...i had prob with compiz in feisty and window borders and this worked and they stay all the time now...

---

### Post by Motorhead Kaze on 2007-11-29
As the Phantom of the Muppet Show would say, "Ah haaaaaah!"

Thank you, I actually saw your thread while cursing Compiz and tried the very thing you suggested.  It didn't work for me, but perhaps it's because I'd already added that bit by hand.  I don't know why things DON'T work, just pretend to when they do.

Strange, today upon starting my computer, Compiz is working very nicely with a cube and windows that burst into flames, until I put it out with some rain.  In normal people language, that means Compiz is working today with no tweeking.

Did I misunderstand Compiz, and it's a weather condition rather than a program??

---

### Post by Motorhead Kaze on 2007-12-23
I should update this and say I got wise and decided that it would probably be a good idea to actually ask this question on the Compiz Forum.  I am pretty sure most if not all them folks frequent this forum too, but I made a visit non the less, and although I wasn't the most helpful "Patient" I got a lot of good advice.  (Znort, thanks to you too)

[http://forum.compiz-fusion.org/showthread.php?p=39719#post39719](http://forum.compiz-fusion.org/showthread.php?p=39719#post39719)

Update 2: I never did find out the "Why" but after a fresh install of Gutsy, Compiz and the cube are working fine.  BUT using Compiz slows down my computer enough that I stopped using it.  Not a complete waste of time, but many hours into my "Learning experience".

---

