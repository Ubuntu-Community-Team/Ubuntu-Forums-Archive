---
title: "compiz water effect making system unable to use"
date: 2009-11-12
forum: Desktop Environments
---

### Post by nitstorm on 2009-11-12
hi guys, newb here. tried playing around with compiz and played with the water effect thing, now, wherever i move my mouse or click something, open up the terminal all i see are black patches in shapes of the windows i wanted open, any solution to this???? or do i have to re-install the whole os :S:S:S????? please help me out!!!!

---

### Post by steveneddy on 2009-11-12
Using Compiz takes LOTS of processor speed and RAM.

If you are lacking in the 3D graphics area, it will not work well for you.

If you know that the graphics card should do the job, try installing the correct drivers, or newer video drivers for your card.

Info on what video card you are using would help.

Or just stop using the water effects in Compiz (my recommendation)

---

### Post by nitstorm on 2009-11-12
tried disabling it but every window, every panel just turns black wen i click on them... no graphics card here.

---

### Post by steveneddy on 2009-11-12
> **nitstorm said:**
> tried disabling it but every window, every panel just turns black wen i click on them... no graphics card here.

Your system must have some type of 3D acceleration video chip in there somewhere or Ubuntu would have not enabled Compiz.

Look at:

System --> Administration --> Hardware Drivers

and see if the system recognizes any hardware that requires 3D accelleration.

Post results back here.

---

### Post by nitstorm on 2009-11-12
the moment i click something, it goes black, hence i cant do anything!!! is there some solution to this from vista???

---

### Post by steveneddy on 2009-11-12
Start the machine is safe mode and in terminal type:

```
metacity --replace &
```

and restart normally.

---

### Post by nitstorm on 2009-11-12
ok will try that and post on it, thanks mate :D

---

### Post by nitstorm on 2009-11-12
dang!! displays the error

Windows manager error: Unable to Open X Display

 booted into ubuntu and still the same problem :(

---

### Post by durand on 2009-11-12
If you start in safe mode without an x server (which I think is the default..), window managers wouldn't work anyway. What you could do is change the session at the login screen to failsafe gnome. That should use metacity. You could then open compiz advanced settings and change the settings there to disable water.

---

### Post by nitstorm on 2009-11-12
> **durand said:**
> If you start in safe mode without an x server (which I think is the default..), window managers wouldn't work anyway. What you could do is change the session at the login screen to failsafe gnome. That should use metacity. You could then open compiz advanced settings and change the settings there to disable water.

and please tell me how i could do that, step-by-step please, total newb here. Thanks in advance man :)

---

### Post by durand on 2009-11-12
Ok. When you start your computer up, you should go to a login screen where you need to type a username and password to login. (This is the default on ubuntu.) When you get there, type in your username (or click on it on the list) and then you should see three dropdown boxes at the bottom of the screen. The last one says GNOME by default. Change that to Failsafe GNOME. Then type in your password and login. This should get you to a desktop without compiz. You can then go to System > Preferences > Advanced Compiz Settings Manager and disable the water plugin. When you log back out, you should log into your normal desktop. If not, change the dropdown back to GNOME and then login.

---

### Post by nitstorm on 2009-11-12
tried doing that twice, same problem, whatever i click turns black, the dropdown menus, the terminal window which i pressed shift+f2 i think... do u think u could tell me how to change the thing to metacity? maybe that would work?????

---

### Post by durand on 2009-11-12
Goto System->Preferences->Appearance->VIsual Effects and click None.

as posted here: [http://ubuntuforums.org/showthread.php?t=877605](http://ubuntuforums.org/showthread.php?t=877605)

If your clicks itself are turning your screen black then you may have a different problem.

You could also try the failsafe terminal option in sessions. You don't get any window manager here, only a terminal so the simple thing to do is hover your mouse over the terminal and then type **ccsm** and press enter. Then untick the water effect and close the settings window. Then type **exit** and press enter.

---

### Post by nitstorm on 2009-11-12
jus wondering how u could turn back from the metacity to the old one..

tried meddling a lil more, ran it in failsafe terminal typed metacity --replace & and after that typed ccsm there and no features were selected, so i jus exited and came out and booted back and its freaking doing the same thing with every mouse click...

maybe i could uninstall this whole compiz thing, is there a code to uninstall it from the terminal??? if so, please post that..

---

### Post by durand on 2009-11-12
```
sudo aptitude search compiz | grep "i "
```

Uninstall all the programs you see there with 
```
sudo aptitude remove compiz compiz-core [...rest of programs...]
```
You can also use synaptic, which is a graphical program and easier to use but I figured that you wouldn't be able to use it if it turns your screen black.

---

### Post by nitstorm on 2009-11-12
jus tried uninstalling everything with the sudo apt-get remove compiz  and sudo apt-get autoremove compiz, even after that ccsm opened up, dunno why, i unchecked every option it had including gnome capability, still the screen goes black and crashes, gonna try ur method one last time now and then will bother about it only later, got my exams tomorrow. <prayers><prayers>let this work and ubuntu be fine :))

---

### Post by durand on 2009-11-12
ccsm will open up because its not a compiz package. It doesn't matter if its installed because if compiz isn't there, it won't do anything. Good luck with your exams!

---

### Post by nitstorm on 2009-11-12
wooo hooo!!!!! u rock bro!!! followed the procedure and everything got alright :D thnx man! thanks a mil !!! postiing this from ubuntu  :D  thanx a mil again :D THREAD SOLVED !!! thnx to durand :D

---

### Post by durand on 2009-11-12
Awesome :)

---

### Post by nitstorm on 2009-11-12
cheers mate :D

---

