---
title: "Moving Minimize/Maximize/Close buttons back to the right"
date: 2012-04-15
forum: Desktop Environments
---

### Post by GaryReggae on 2012-04-15
I have just installed Ubuntu 11.10 and am having some difficulties with the UI. I've been using Ubuntu for 2-3 years, that was version 10.4. I am finding this new version very hard to use as it appears that everything has been moved. Is there any way of going back to the original layout?

Anyway, my main question regards the window Minimize/Maximize/Close buttons. I have been using computers for 15 years or so and am used to finding these at the top right. So it's very annoying having them on the left. 

They were on the left in 10.4 but it was easy to fix that using gconf-editor. I can't get that to work in 11.10. I search for it using the Dash tool and it comes up, but when I click on it, nothing happens. I have tried double-click as well but that doesn't work either. 

I have Googled this and an app called Ubuntu Tweak can do this. I've installed it and found the option to move the buttons to the right but there doesn't appear to be any way to save/apply the settings unless I am missing something blindingly obvious. If I close it and open it again then all the changes I made have been lost.

So...any ideas folks? Or am I going to have to put 10.4 back on?

---

### Post by Lemuriano on 2012-04-15
Hi,

Hope a satisfactory solution is find, but if that is not the case you can always try Xubuntu-desktop or XFCE4 which are very customizable and not to far away from gnome2. 

I recently  update from Ubuntu 10.04 to 11.10 and even with Gnome tweak tools, Myunity and classicmenu indicator I did not feel comfortable. Also gnome fallback mode/Gnome Classic or the shell did not make the cut for me. At the end I just did a clean install of Xubuntu on my desktop and HTPC and wondering why I didn´t do it sooner.

Even though I haven´t try it, Cinnamon is worth considering base of what is been written, but remember that is a new project.

Regards.

---

### Post by 3Miro on 2012-04-15
Use Ubuntu tweak, it will let you move the windows buttons:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by Inkknife on 2012-04-15
> **3Miro said:**
> Use Ubuntu tweak, it will let you move the windows buttons:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
I just tryed that because I also want my buttons on the right and the Ubuntu Tweak tool seems to have no effect on the buttons in question.

---

### Post by hrickh on 2012-04-15
You might have to install it (it's in the repositories), but from here on out it looks like Gnome 3 will be using dconf-editor.

Once you've got that program, navigate to org/gnome/shell/overrides and you'll be able to change it there, just as you did in gconf-editor.

HTH

R.
==

---

### Post by GaryReggae on 2012-04-17
> **hrickh said:**
> You might have to install it (it's in the repositories), but from here on out it looks like Gnome 3 will be using dconf-editor.

Once you've got that program, navigate to org/gnome/shell/overrides and you'll be able to change it there, just as you did in gconf-editor.

HTH

R.
==
Thanks, you're on the right lines I think there. I've installed and started up dconf-editor but I can't see 'shell' in the list under Gnome. I've had a look under Desktop and some of the other categories but there doesn't seem to be that option. I've attached a screenshot, so any further suggestions are greatly appreciated.

Thanks,

Gary

---

### Post by jba3 on 2012-04-19
Try:

gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"

Not sure about unity but it works in gnome classic for me

---

### Post by GaryReggae on 2012-04-20
> **jba3 said:**
> Try:

gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"

Not sure about unity but it works in gnome classic for me

Thanks but that doesn't work I'm afraid. It just produces a '>' mark as the input prompt when I run that (instead of the usual prompt with my username and so on).

---

### Post by leogagliardi on 2012-05-03
I ve got the same problem: ubuntu-tweak, dconf-tool or the gconftool-2-... string on command line do not move that buttons where I want. The arguments of free software are becoming more and more blurred after every new version of ubuntu. The possibilities to choose are more and more hidden. Cannonical is introducing more and more shops and banners inside our personal computers, through ubuntuone, through the software center, etc.. And the "darwinian" development of the (free) software beggins to be not so true since they put not the more popular but what it is on the line of their future convenience on the default installation CD, and they take out of support (from repositories) really popular and good software. Remember Amarok, or just see how they are taking definitely out the simple and well organized Gnome.
Let's go back to our buttons. Summarizing: I did it with the old Gconf-editor. It worked for me.I did this:
1) I ve Installed the gnome-shell and entered my session with the Gnome Classic (with effects). I suppose you have already installed it, but if not, check the How-to on other threads, it's easy
2) I've installed the Gconf-tool:
[PHP]sudo apt-get install gconf2 gconf-editor[/PHP]
3) like in previous editions of ubuntu, enter gconf-editor and go to
/apps/metacity/general/button_layout 
there, click and change the order of the comma separated words and put the two points at the beggining or at the end to have the buttons on the right or left respectively. You can also put that two points between words or repeat words on both sides to have buttons on one and other side of the window top.I'm classic in this sense then my string was changed to:
:minimize,maximize,close
the changes would apply inmediately after pressing enter
I hope it helps you

---

### Post by kansasnoob on 2012-05-03
You might find some useful info here:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

---

### Post by nillian on 2012-05-04
I can confirm that leogagliardi's post above worked for me in Unity in 12.04

---

### Post by bohemian9485 on 2012-05-05
Ubuntu Tweak has always worked for me. I found out that you can change the position of the window button by changing the default Ubuntu Ambiance theme.

---

