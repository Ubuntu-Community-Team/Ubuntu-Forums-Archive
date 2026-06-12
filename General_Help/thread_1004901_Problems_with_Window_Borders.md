---
title: "Problems with Window Borders"
date: 2008-12-07
forum: General Help
---

### Post by mysteriork on 2008-12-07
I am currently running Ubuntu 8.10 and Desktop Effects with my Nvidia Geforce 7400 Go.  Everything seems to be running smoothly except for occasionally a given window (Firefox, Pidgin, etc.) will lose its "dressing" along the top or it will get really blurred out to a point where you can't even see the "X" at the top right to close the window...

Here is a picture:

[IMG]http://www.uploadpad.com/files/Screenshot.png

What is the problem here?  Is it fixable?  The strange thing is that the window will look like that and then sometimes it will be fine...

Thanks.

---

### Post by Wartender on 2008-12-07
```
metacity --replace
```
that is all.
(it should work)

---

### Post by Hairyz0r on 2008-12-07
> **Wartender said:**
> ```
metacity --replace
```
that is all.
(it should work)

Im getting the same problem, 

This does work, but it disables compiz effects,  

is there a workaround to have the best of both? :)

---

### Post by IceReaver75 on 2008-12-08
If your using a nvidia card you can try to use the 180.06 beta driver.  You have to manually install it but it stops all the window flicker problems.  Thats the driver im using with a GeForce 6200 card.

If you need the steps to manually install the driver I can offer them if needed.

---

### Post by Hairyz0r on 2008-12-08
> **IceReaver75 said:**
> If your using a nvidia card you can try to use the 180.06 beta driver.  You have to manually install it but it stops all the window flicker problems.  Thats the driver im using with a GeForce 6200 card.

If you need the steps to manually install the driver I can offer them if needed.

Yes please, that would be great

Thanks

---

### Post by EreboShade on 2008-12-08
i've the same problem

[http://ubuntuforums.org/showthread.php?p=6315358#post6315358](http://ubuntuforums.org/showthread.php?p=6315358#post6315358)

please you can post or send me a pm to solve this problem? thanks

---

### Post by IceReaver75 on 2008-12-08
This is how I installed the Nvidia 180.06 driver manually

1: goto Synaptic Package Manager and search for linux-source-2.6.27 and click for installation.

2. go here : [http://www.nvidia.com/object/linux_display_ia32_180.06.html](http://www.nvidia.com/object/linux_display_ia32_180.06.html) and download the NVIDIA-Linux-x86-180.06 pkg1.run file and move it to your home folder

these next steps you will have to write down cause you will be going to a tty session and wont have a graphical desktop anymore

3: press Ctrl-Alt-F1
it will leave the desktop and go into the tty session and will ask for your sign-in name and password type those in

4: next type sudo /etc/init.d/gdm stop......it will ask for your password type in in this stops your x-server to install the driver

5: next type ls......this lists what is in your home folder the nvidia driver should be listed along with your folders

6: next type sudo sh NVIDIA-Linux-x86-180.06-pkg1.run......make sure it is typed exactally like that then follow the steps that come up on the screen answer yes to all questions it should build the new nvidia driver

7: after the driver is built you want to type 
   sudo /etc/init.d/gdm start......this will restart your x-server and bring your graphical interface back

it should move your nvidia x-server settings to application/system tools...check that to make sure the 180.06 driver is listed there and all window problems should be gone

hope this helps and you can understand the steps

---

### Post by mysteriork on 2008-12-08
I just followed those steps and installed the new driver...

Upon restarting, my desktop loaded fine, but when I tried to enable desktop effects, my screen went white with colored bars running down the middle.  The screen stays like this and never loads the effects properly and I am forced to restart.

Any idea what may be happening?

---

### Post by Hairyz0r on 2008-12-08
> **IceReaver75 said:**
> This is how I installed the Nvidia 180.06 driver manually

1: goto Synaptic Package Manager and search for linux-source-2.6.27 and click for installation.

2. go here : [http://www.nvidia.com/object/linux_display_ia32_180.06.html](http://www.nvidia.com/object/linux_display_ia32_180.06.html) and download the NVIDIA-Linux-x86-180.06 pkg1.run file and move it to your home folder

these next steps you will have to write down cause you will be going to a tty session and wont have a graphical desktop anymore

3: press Ctrl-Alt-F1
it will leave the desktop and go into the tty session and will ask for your sign-in name and password type those in

4: next type sudo /etc/init.d/gdm stop......it will ask for your password type in in this stops your x-server to install the driver

5: next type ls......this lists what is in your home folder the nvidia driver should be listed along with your folders

6: next type sudo sh NVIDIA-Linux-x86-180.06-pkg1.run......make sure it is typed exactally like that then follow the steps that come up on the screen answer yes to all questions it should build the new nvidia driver

7: after the driver is built you want to type 
   sudo /etc/init.d/gdm start......this will restart your x-server and bring your graphical interface back

it should move your nvidia x-server settings to application/system tools...check that to make sure the 180.06 driver is listed there and all window problems should be gone

hope this helps and you can understand the steps

it worked!!!

thanks very much

---

### Post by IceReaver75 on 2008-12-08
> **mysteriork said:**
> I just followed those steps and installed the new driver...

Upon restarting, my desktop loaded fine, but when I tried to enable desktop effects, my screen went white with colored bars running down the middle.  The screen stays like this and never loads the effects properly and I am forced to restart.

Any idea what may be happening?


sorry I really can't say whats going on there.  I never had that problem before.  When I restarted my x-server it enabled normal desktop effects automatically for me with no problems.  When the driver was being installed did it build a new nvidia kernel and did you let it overwrite your x-org config.  From what i just read doing some searching is that if you dont let it overwrite your x-org when finished you might get that problem.

---

### Post by mysteriork on 2008-12-08
How do I let it override xorg?

---

### Post by mysteriork on 2008-12-08
I actually did override xorg apparently, but then I realized that I should be using the x64 build of the driver...

So, I downloaded that driver and when I followed your steps but with the new file...when I try to execute the command and install the driver it says the command does not exist!?

But, if I do the same command with the first file, it works...

So, I don't understand this at all

---

### Post by mysteriork on 2008-12-08
Disregard that last one...apparently I installed the right one.

But, I still cannot enable desktop effects and also, when I open a window there is no taskbar at the top at all!

---

### Post by Wartender on 2008-12-08
well maybe you can do metacity --replace , and in compizconfig disable the window decorations (before runnsing metacity --replace) maybe you can use the other effects?
i'm not sure at all though.

---

### Post by IceReaver75 on 2008-12-08
you might have conflicting drivers now that both the 32 bit and the 64 bit are installed.  You might have to un-install the 32 bit driver to make things straighten out:

I believe to uninstall the 32 bit driver you can do that through a terminal by typing sudo sh NVIDIA-Linux-x86-180.06-pkg1.run --uninstall

if you cant do it through a terminal just follow the steps as before but replace the the uninstall command in there in place of the sudo sh command

if that dont work i'll try finding some more info by digging some more and try to help you out the best i can

you did change the sudo sh command to sudo sh NVIDIA-Linux-x86_64-180.06-pkg2.run when installing if not it will install the 32 bit version again thats assuming your using this driver now
[http://www.nvidia.com/object/linux_display_amd64_180.06.html](http://www.nvidia.com/object/linux_display_amd64_180.06.html)

---

### Post by EreboShade on 2008-12-09
ok, thanks, i solved all!!!

---

### Post by eternalnewbee on 2008-12-09
This works for me: Right-click on Compiz Fusion Icon, under **Select Window Manager** select **Compiz**, and under **Select Window Decorator**, select **GTK Window Decorator**.
Of course you need to press **ALT-F2**, and enter ```
compiz --replace
```

---

### Post by EreboShade on 2008-12-09
> **eternalnewbee said:**
> This works for me: Right-click on Compiz Fusion Icon, under **Select Window Manager** select **Compiz**, and under **Select Window Decorator**, select **GTK Window Decorator**.
Of course you need to press **ALT-F2**, and enter ```
compiz --replace
```

i returned in the default option and i changed with this option, but it doesn't solve.

the first solution is the best!

---

### Post by eternalnewbee on 2008-12-09
> 
i returned in the default option and i changed with this option, but it doesn't solve.

the first solution is the best!
I was actually referring to **mysteriork**.
But I'm glad IceReaver75's solution worked for you. Hope it works for **mysteriork** as well.

---

### Post by dcviana on 2008-12-09
I tried installing the 180 drivers and they kind of worked, but now my screen is slightly dislocated to the right.

Like, there is a little piece of the right side of the screen on the left, and the same piece is missing on the right side.

I can't post screenshots because the screen capture program is capturing the screen without the problem, so I think its really a driver problem.

If I open nvidia-settings and mess with the stretch options (I have a widescreen laptop) it goes back to normal, I don't even need to change the option, I just change it temporaly and go back to the previous option, the screen refreshes and the problem vanishes.

The problem is, I have to do it everytime I boot Ubuntu, so if anyone had this problem and managed to solve it please let me know.

By the way, I have a GeForce 7600 Go board on an Intel Core Duo and Ubuntu 32bit

---

### Post by EreboShade on 2008-12-09
> **dcviana said:**
> I tried installing the 180 drivers and they kind of worked, but now my screen is slightly dislocated to the right.

Like, there is a little piece of the right side of the screen on the left, and the same piece is missing on the right side.

I can't post screenshots because the screen capture program is capturing the screen without the problem, so I think its really a driver problem.

If I open nvidia-settings and mess with the stretch options (I have a widescreen laptop) it goes back to normal, I don't even need to change the option, I just change it temporaly and go back to the previous option, the screen refreshes and the problem vanishes.

The problem is, I have to do it everytime I boot Ubuntu, so if anyone had this problem and managed to solve it please let me know.

By the way, I have a GeForce 7600 Go board on an Intel Core Duo and Ubuntu 32bit

maybe you must refresh the monitor with automatic settings???? bye :P :lolflag:

---

### Post by dcviana on 2008-12-10
I solved the problem (well, sort of) but the solution was ugly as hell.

I went to System -> Preferences -> Sessions and added the command "nvidia-settings -l" (without quotes) to the list of programs to run at startup. 

Now it automaticaly load the default settings and this activates the "refresh" that fixes everything.

I still see the error while the system is loading, but it disappears as soon as Gnome finishes loading.

Well, it's ugly I know, but now I can have compiz activated without window borders corruption. Hope when the final 180 series drivers are released this problem will be solved.

---

### Post by Sayuuk on 2009-01-02
Nice,

I've had this problem for... ever?

Finally I can fully enjoy the desktop effects!

Stefan

---

