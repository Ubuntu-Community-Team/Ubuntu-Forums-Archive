---
title: "gnome/openbox problem"
date: 2009-01-25
forum: Desktop Environments
---

### Post by macheboy on 2009-01-25
I am using Ubuntu Intrepid Ibex and today I wanted to se how is Openbox, but when I restarted, after loging in, I couldn't see almost anything, i.e. I only saw some of the apps that are autostarting when I log in. same happens for all users and sessions.
Now I am in the failsafe terminal and I started Opera from terminal (firefox window is too small and I can't resize it)
Also, there are no title bars, gnome-panels or icons.
Can i somehow fix or reinstall Xserver?

I tried
```
sudo dpkg-reconfigure xserver-xorg
```
and restoring my xorg.conf from backup, but noting helped.

thanks
Mak

---

### Post by urukrama on 2009-01-26
If you see Opera, your xserver/xorg is fine. If you can run an application with a graphical user interface, that means X is running.

 It sounds to me like Openbox and Gnome just don't load (lack of window decorations, no panels, etc.). We'll a little more information to help you with this problem. 

How did you install Openbox? How do you login? Do you use GDM or just startx? If you use GDM, What session do you choose? If you use startx, please post your .xinitrc here.

---

### Post by macheboy on 2009-01-26
I installed openbox using
```
sudo apt-get install openbox obconf
```
and removed it the same way after it was not working.
I am using gdm with default GNOME session, but have tried all the others (since this one stopped working), and the failsafe terminal was the only usable.

---

### Post by macheboy on 2009-01-26
Trying to fix things, I somehow managed to break the whole system down so it wouldn't even start, not even after, I tried to copy something from LiveCD, so I reinstalled everything. Fortunatley, I had separate partiton for hom.
Still thanks for your time.

---

### Post by SMOA on 2009-01-27
I'm having a similar problem and I don't want to reinstall, maybe someone can help. I also installed openbox, but it worked great. I was loading it by choosing an openbox session from the grafix login page. I wanted to start it from a prompt. So I figured out how to boot to a prompt, now I need to know to know how to get openbox to start.

---

### Post by Mike80 on 2013-04-28
I installed openbox and a few other shells one after another and was trying each of them but after loging to gnome/openbox I just see an icon on the desktop. No bars no nothing. I started firefox thru terminal which I opened thru a keyboard shortcut. I can't log out so I can choose another DE. If I push the reset button on my pc when it starts it comes to this again. I already tried the failsafe or something after the grub but gets the same. Now I only see the wallpaper. I can open things thru the terminal at least otherwise I couldn't type this.
I copied my home folder to another partition just in case I have to reformat (which I will tomorrow for sure - it's near 2am and gotta go to work tomorrow/today 9am).
Just to let others know it happened after installing gnome openbox and loging out and then in in it.  Cheers.
--edit add--
After reading [http://ubuntuforums.org/showthread.php?t=1142709](http://ubuntuforums.org/showthread.php?t=1142709) I tried ```
openbox --replace
``` and I got window decorations and the openbox menu working now from the right mouse button (the way it should be) and can now log out and pick another shell if I want.. I think.. haven't tried yet, just typing this first. Gotta get some sleep for work, damn thing...:)

---

### Post by oldos2er on 2013-04-28
Closed, please don't bump old threads.

---

