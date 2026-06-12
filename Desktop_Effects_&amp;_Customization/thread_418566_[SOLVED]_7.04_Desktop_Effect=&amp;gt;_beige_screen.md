---
title: "[SOLVED] 7.04 Desktop Effect=&amp;gt; beige screen !!"
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by pognonec on 2007-04-22
:(
I am not familiar with Ubuntu yet, but use it more and more. I just upgraded from 6.10 to 7.04, and saw that new menu: Desktop effect. Of course, I had to try it, even though there was some kind of warning that it may not work on all computer... I selected both choices offered, had to install some new proposed 3D accelerator software (my laptop:Inspiron 8100).
It kind of worked, but I had strange background: my desktop Ubuntu tree was replaced by a uniform black color.
I restarted, everything booted OK, but at the end, I only got a scary uniform beige screen, with nothing else but the mouse arrow!
I stopped by pressing on the main switch, and just before it went off, the beige screen disappeared, and I could briefly glance at my usual desktop!
What can I do to come back to my precious setting?
What is this Desktop Effect doing??
Is it a good idea to leave it around if it messes up thing like that??

---

### Post by insyncim64 on 2007-04-22
the same to you.My graphic card is ATI mobile-radeon X1600.It seems not thing when i finished install the ubuntu 7.04.But the OS can not identify the graphic card and recommend me to download driver for the graphic card.Also i can`t use the compiz desktop effect(when i enable the effect,beige screen!!).So i did it.
Here comes the problem.When i reboot the computer and enter the ubuntu again.There is something wrong with the X-sever.I reboot again and again.But remains the same.

---

### Post by pognonec on 2007-04-23
I found a solution to get rid of this white screen problem. It was originally posted by CyBuzz in [http://ubuntuforums.org/showthread.php?p=2430197#poststop](http://ubuntuforums.org/showthread.php?p=2430197#poststop)
Here it is:
On your scary screen: Ctrl-Alt-F1
and enter in the shell that appears:

mkdir tmp
mv .gnome* tmp/
mv .gconf* tmp/

The only problem is that you will lose your desktop settings (background, etc, as well as some other settings). But IT WORKS!
:)

---

### Post by tmcgee on 2007-05-18
I have the same problem. I am running Fiesty and it is going pretty well, then I enabled Desktop Effects and when I was closing Firefox, the desktop locked up on me such that all I could do was power off. Ctrl-Alt-F1 wouldn't even work. Since then, when I boot up, I get a white screen of death... I can tell Ubuntu is still running (i.e. I can log in, I'm blind, but I can tell because of the HDD activity). Then I can do the Ctrl-Alt-F1 and get a terminal session.

I've done the following fixes suggested in these forums, but I am still getting the white/beige screen....
1.)
mkdir tmp
mv .gnome* tmp/
mv .gconf* tmp/

2.)
sudo apt-get remove compiz

3.)
Startx
Ctrl-Alt-Backspace

HELP!!!! Any Ideas Welcome... I am down right now and I really don't want to switch back to Window$.

---

