---
title: "Ubuntu 9.10: Downgrade GDM to previous version"
date: 2009-11-19
forum: Desktop Environments
---

### Post by scorp123 on 2009-11-19
As you may be aware the current version of GDM included with Ubuntu 9.10 leaves a lot to be desired ... 

Many people have complained about this. Me too. I even went so far and replaced the current GDM with KDM:
[http://ubuntuforums.org/showthread.php?p=8337723#post8337723](http://ubuntuforums.org/showthread.php?p=8337723#post8337723)

Simply downgrading to the previous GDM did not seem to work ... Until now. I just ran across this posting:

[http://www.ubuntugeek.com/how-to-downgrade-gnome-display-manager-2-28-to-2-20-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-downgrade-gnome-display-manager-2-28-to-2-20-in-ubuntu-9-10-karmic.html)

As the author clearly states in that posting: following those steps may break your system! [COLOR="Red"]**_Please:_** only proceed if you know what you do![/COLOR]

Best thing probably would be you try that procedure on a virtual machine (e.g. inside VirtualBox or VMware) first before doing it for real on your real Ubuntu OS installation.

I post this in the hope it might be useful to others who are disappointed with the new GDM just as myself ... :)

---

### Post by scorp123 on 2009-11-19
OK, I just tried it and it works. The steps:

[LIST]
[*] log out of your GNOME session
[/LIST]

[LIST]
[*] when at the GNOME login screen, hit **Ctrl+Alt+F2** ... this should take you to the text console (you have several of those and you can switch between them using Ctrl+Alt+F1, Ctrl+Alt+F2, Ctrl+Alt+F3, and so on. It's like having multiple screens on the same computer. Your **graphical desktop** should usually be sitting and waiting for you on **Ctrl+Alt+F7** ...)
[/LIST]

[LIST]
[*] We have to stop GNOME now:
```
sudo /etc/init.d/gdm stop
```
(the system might complain slightly about those "init" commands being outdated, that Ubuntu uses new-style "upstart" commands and what not .... oh well, I'm oldschool ... :D  )
[/LIST]

[LIST]
[*] Now we install the new old GDM 2.20:
```
sudo apt-get install gdm-2.20
```
The packet manager will add a few extra packages as dependencies and ask for your confirmation. It will also warn you that a few other packages will be removed as consequence. Hit "Y" if you agree with what it wants to do ...
[/LIST]

[LIST]
[*] Once the new old GDM 2.20 has been installed a dialogue should appear on your screen, asking you which login manager you want to use: **"gdm"** or **"gdm-2.20"** ... Use the cursor keys to highlight **"gdm-2.20"** and then use the Tab key to highlight the **"OK"** button. Hit enter ....
[/LIST]

New old GDM 2.20 unfortunately has a slight bug in its config file and there are two methods to correct it.

**_Method #1_**

This means we have to edit the config file. This is the method that was suggested on "UbuntuGeek":
[http://www.ubuntugeek.com/how-to-downgrade-gnome-display-manager-2-28-to-2-20-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-downgrade-gnome-display-manager-2-28-to-2-20-in-ubuntu-9-10-karmic.html)

Background info:

There is a line in **/etc/gdm/gdm.conf** that says ... :
```
...
StandardXServer=/usr/**[COLOR="Red"]X11R6[/COLOR]**/bin/X
...
```

The highlighted part above is wrong ... On Ubuntu 9.10 there is no **"/usr/X11R6"** directory. If you rebooted your system now you'd now run into trouble and the GUI environment would not be able to start.

Hence why that line needs to be corrected. Either manaually with whatever editor you see fit (vi, vim, nano, pico ...) or automated with "sed" as demonstrated on the web site above.

I personally don't like that idea. What if there is an update? Chances are the config file would be overwritten and those changes might then be lost ... which means that after an update there might be unexpected troubles.

**_Method #2 -- way easier:_**

So instead I chose to give that config file what it wants ... I created the sub-directory it wants so its paths are correct now. The commands I used for this:

```
cd /usr
sudo mkdir X11R6
cd X11R6
sudo ln -s /usr/bin bin

```

The commands above create an empty directory with the name **"X11R6"**, we go into that directory and then create a symbolic link between **/usr/bin** (where all the programs really are) and the **"X11R6"** directory, so that the programs underneath **/usr/bin** can now also be found as **/usr/X11R6/bin** but without wasting any extra space.

Time to restart GDM:
```
sudo /etc/init.d/gdm start
```

Or simply reboot:
```
sudo reboot
```


In both cases the old GDM should start now and it should look exactly like the login screen in Jaunty. Best of all: **it's themable again** and all the GDM login themes that you may have used in the past should work tip top again. :D

---

### Post by scorp123 on 2009-11-19
Oh ... sorry for my redundant post. Someone already posted instructions one week ago:

[http://ubuntuforums.org/showpost.php?p=8294939&postcount=1](http://ubuntuforums.org/showpost.php?p=8294939&postcount=1)

OK ... I suck at Google :D

---

### Post by mechaxl on 2009-12-05
well it helped me at any rate.

thanks for the info

---

### Post by justanotherperson on 2009-12-15
holy **** it worked lmao im typing from my lapop becuse my desktops ubuntu didint start XD but i found your kde thing and boom it ran although still kinda slow lol thanks

---

### Post by r_avital on 2010-01-14
> **scorp123 said:**
> Oh ... sorry for my redundant post. Someone already posted instructions one week ago:

[http://ubuntuforums.org/showpost.php?p=8294939&postcount=1](http://ubuntuforums.org/showpost.php?p=8294939&postcount=1)

OK ... I suck at Google :D

Not at all!  Your post is valuable, because your Method#2 is so much safer.  I'll give it a try.

I had all but given up.  THANKS ;)

---

### Post by MooPi on 2010-01-14
You may have missed this but a tool has been made to configure GDM2 [http://ubuntuforums.org/showthread.php?t=1358026&highlight=GDM2](http://ubuntuforums.org/showthread.php?t=1358026&highlight=GDM2)

You may be able to use gdm to your satisfaction.

---

### Post by holmstrom on 2010-01-15
Both the methods of solving the /X11R6/ issue caused problems for me. The first method (removing the entry) caused Ubuntu to boot in low graphics mode and no GDM displayed. The second one made a lot of fuss about failing graphics and double displays until finally booting into GDM 2.20 (and thereafter working fine, mind you).

For some reason it also switched out my grub background to a Debian logo.

Strange.

---

### Post by Aryamaan on 2010-01-16
Hey,
I tried downgrading. When i hit ctrl+alt+f2.. i get the black screen... but thr is nothing written there... it's an empty screen with a cursor and i can't enter any text. Pls help !

---

### Post by rfm33428 on 2010-02-27
To start, I suppose everyone has a different experience based on there hardware & preferences.  One thing I can agree with, like a lot of people I'm finding, is that the new GDM sucks.

I followed the steps provided to downgrade from 2.28 to 2.20 using method 2.  Every time I turn on or restart my computer, I have a Xserver conflict error of 2 Xservers on the same display :0 that I have to choose 'yes' to get through.  From what I can see, by choosing 'yes', it take the Xserver you want to display :1

I find it annoying & wish I knew more on how to resolve the issue.  Instead I've found a method that helps to a degree.  Unfortunately, you'll still get that error the 1st time after downgrading, every time you update your kernel & video driver.   If this process helps you too, then you gotta admit it's less annoying.

What I did was:
a) I created the directory for X11R6
    cd /usr
    sudo mkdir X11R6
    cd X11R6
    sudo ln -s /usr/bin bin

b) Then I jumped down to the text console ctrl-alt-f1 to stop   the gdm
   sudo /etc/init.d/gdm stop  *as stated before, there is that issue that comes up but it still stops

c) Then I removed the new gdm 2.28
   sudo apt-get remove gdm

d) Then I installed the older gdm 2.20
   sudo apt-get install gdm-2.20

e) Finally I rebooted
   sudo reboot

Choose 'yes' when the Xserver error comes up so it can use display :1.   Also, if you jump between different consoles, typically it's f7 for the default.  Now with this change your using f9.  As it did for me, I hope it makes your downgrading less painful.

---

### Post by dunicraig on 2010-02-28
I downgraded to 2.20 and its working great however I was wondering if I update ubuntu will it cause any errors or problems?

---

### Post by rfm33428 on 2010-03-03
Oddly enough, at least it doesn't make sense to me, changing my splash screen solved the error I was getting.  I've been re-installing Linux & downgrading the original posted way.  Changing my splash screen seems to be the cure for my issue.

If anyone could explain why, PLEASE enlighten me.

---

### Post by plenthoz on 2011-01-18
what do you mean by changing the splash screen,,i have the same problem can you teach me step by step...thanks :D

---

### Post by D3VILG3N3 on 2011-04-07
Hello i'm using Ubuntu 10.10.
 
you think this will also work on maverick ?

---

