---
title: "NVIDIA GeForce4 MX 440 drivers"
date: 2009-01-03
forum: Desktop Environments
---

### Post by kedrigern38 on 2009-01-03
I'm dual booting Ubuntu 8.10 and Vista 32 ultimate.

My video card is an NVIDIA GeForce4 MX 440 with AGP 8X (according to Windows), and I'm having problems with anything but the standard generic drivers in Ubuntu.

The Ubuntu OS let me know that updated NVIDIA drivers were available, so I selected and installed them. There were warnings that the Ubuntu programmers/team could not control the drivers because the are provided by NVIDIA. What a mistake.

The screen resolution dropped to less than 640 x 480 after a reboot, screen dialogs are so large I can't select apply or OK or whatever. I tried to reinstall the generic drivers using Synaptic, but cannot apply the changes because I can't move the dialog box or tab to the apply/OK button.

So, I'm currently wiping the partition using Paragon Disk Manager to reinstall Ubuntu 8.10 and try again.

Which drivers do I need to install for my NVIDIA GeForce4 MX 440? I would like to experiment with some of the more advanced Ubuntu graphics settings/options.

You're talking with a noob here, so please be specific.

Thanks

---

### Post by graysky on 2009-01-03
[http://www.nvidia.com/object/linux_display_x86_96.43.07.html](http://www.nvidia.com/object/linux_display_x86_96.43.07.html)

D/l the driver from that web site.

---

### Post by kedrigern38 on 2009-01-03
Screw Ubuntu and linux. I've been dicking around with this issue for hours and, despite following instructions on Linux forums to the letter, get nothing but error after error, I can't do this, I can't do that, can't find this can't run that blah blah blah.

Ubuntu and linux are **DEFINITELY** not ready for prime time.

Keep it!

---

### Post by benerivo on 2009-01-03
What have you tried so far? If you tried the 'Restricted Drivers' option in Ubuntu and it failed, then it may have been because of an incompatibility with the xserver in 8.10 and the older (96xx) drivers you would need for your card. I'm not sure if this has been fixed yet. I would definitely recommend the envy program.```
sudo apt-get install envyng-gtk
```This program will then appear in the main menu and it runs through the installation of nvidia and ati drivers.

---

### Post by Surkow on 2009-01-03
This is probably a limitation of the official nvidia drivers. You can try [Envy]("http://albertomilone.com/nvidia_scripts1.html") for installing older drivers than are currently offered in the repositories. nVidia removed support for your graphics card in newer versions of the driver. The nvidia site itself suggests to use version 96.43.07 for the GeForce MX series.

Edit: like benerivo mentioned it can also be an issue with the older drivers and the newer xserver.

---

### Post by kedrigern38 on 2009-01-03
Tried Envy. Ran sudo install envyng-gtk and the program wouldn't run even from a terminal window.

Can't run this, can find that blah blah blah. Not installed. Even though I followed instructions on the program's site and Ubuntu forums.

But the NVIDIA drivers that are completely incompatible and hose the system are available for install in Synaptic.

Uninstalled Envy and tried using Synaptic to install. Same problem. It won't even launch much less look for or install drivers.

I'm a PC Tech and we've considered offering Ubuntu to our customers as an alternative to Windows.

NO WAY!

I've had my issues with Windows (since DOS). But if our customers ran into the same problems I did just trying to get a graphics driver to work, they'd be at our door with torches ready to string us up.

It's just not ready for prime time.

---

### Post by graysky on 2009-01-03
> **kedrigern38 said:**
> I'm a PC Tech and we've considered offering Ubuntu to our customers as an alternative to Windows.

NO WAY!

No offense dude, but I'm sick and tired of posts like this.  You're a PC tech and you expect a community of users LIKE YOU to spoon feed you information in real time free of change?!  

Damn, learn some patiences or how to use google effectively.  Do you realize that it has been approx. 1 h since you posted and already you pissed all over the product and insulted the user base?  Keep windows, you deserve it.

---

### Post by tenchi19134 on 2009-01-03
> **kedrigern38 said:**
> 
I'm a PC Tech and we've considered offering Ubuntu to our customers as an alternative to Windows.

NO WAY!

I've had my issues with Windows (since DOS). But if our customers ran into the same problems I did just trying to get a graphics driver to work, they'd be at our door with torches ready to string us up.

It's just not ready for prime time.

Dude most of us here are PC Techs and we just deal with our problems the same way we deal with windows problems (mostly Vista) S.T.F.W. Search the web.

Vista isn't ready for prime time and neither was XP when it was first released. Let's just say Vista is M.E. all over again. And your complaints about Ubuntu are that Hardware developers don't support Ubuntu and not the other way around. Get your facts straight.
As a community we try to break bonds with money hungry corps. and help those who need help.

So in conclusion...... UP YOURS!!!

---

### Post by Surkow on 2009-01-03
> **kedrigern38 said:**
> Tried Envy. Ran sudo install envyng-gtk and the program wouldn't run even from a terminal window.

Can't run this, can find that blah blah blah. Not installed. Even though I followed instructions on the program's site and Ubuntu forums.

But the NVIDIA drivers that are completely incompatible and hose the system are available for install in Synaptic.

Uninstalled Envy and tried using Synaptic to install. Same problem. It won't even launch much less look for or install drivers.

[...]
While not commenting on the rest of your post. You should be able to launch envy from the menu. If you want to try it with the terminal (which isn't needed at all) you can try "envy -t" which allows you to get the text based version. It will ask you for your password. "gksudo envy -g" gives me the graphical version. When I started with Ubuntu years ago I installed these drivers by hand and had a lot more patience (say 2 months) in mastering the basics. Nowadays I never have to worry about incompatible hardware because I buy hardware that is actively supported in Linux. Blame the lack of support of nvidia for your terrible experience. Just use a modern pc to experiment with Ubuntu.

---

### Post by 2hot6ft2 on 2009-01-03
> **kedrigern38 said:**
> 
You're talking with a noob here, so please be specific.

> **kedrigern38 said:**
> 
I'm a PC Tech
I'm running the exact same card with the drivers recommended in
System>Administration>Hardware Drivers
Makes me glad I do my own tech work.

---

### Post by pietjanjaap on 2009-01-03
Envy in textmode you start with(see envy site): sudo envygt -t
Then you get a menu.


Install envy, is inside of ubuntu.
Go to the envy website(google), there you can find the textmode instructions.
To start envy in textmode sudo envyng -t, then you get a menu in textmode.
Choose remove drivers, (the ubuntu will start again without drivers if you want).
Now reboot to recovery mode,
choose x fix (here your video card and monitor will be search.
then go to textmode,
install your driver with sudo envyng -t
reboot.
If your screen size is not ok, go to system-preferences-screen resolution, and change it, and reboot.

If you install the video driver with envy with gui, then you can choose 3 drivers(nvidia).
If it goes wrong always remove everything and start from the beginning.

---

### Post by graysky on 2009-01-04
[http://www.nvidia.com/object/linux_display_x86_96.43.07.html](http://www.nvidia.com/object/linux_display_x86_96.43.07.html)

D/l the driver from that web site.

Drop to a tty (ctrl+alt+F1) and do the following:

```
$ sudo /etc/init.d/gdm stop
$ cd /path/to/your/downloads
$ sudo sh NVID<TAB>
```

That will run the nvidia installer.  Answer the questions and restart gdm after it installs your driver.

```
$ sudo /etc/init.d/gdm start
```

As I said before, you need an attitude adjustment if you expect folks to help you in these and other forums.  Ubuntu is a fine product, you just need to learn how to use it.

---

### Post by kedrigern38 on 2009-01-04
Open mouth insert big foot.

Have you ever had one of those days? That was my week, and I took it out on the Ubuntu user base. I apologize. This has never happened before and will not happen again.

I am embarrassed these posts actually came out of me.

I did many Google searches on the errors/messages I received when trying to update the video card drivers (as I always do with PC problems), followed the suggestions step-by-step and searched some more when another dialog or message appeared. Hence the 'hours.' 

I should have just given up for the day and chalked it up to a lack of information/my education concerning Ubuntu Linux.

Graysky: Thank You for responding so quickly. Again, I did not mean to 'piss' on you or the Ubuntu user base. I have answered posts in free forums concerning Windows problems, and I've also had the same type of replies that I spewed. I apologize again.

I realize all of the members of the forum are just trying to help new users solve some of the riddles and you perform a valuable much-needed service.

2hot6ft2: I actually did select the NVIDIA drivers in System>Administration>Hardware Drivers several times (after Google searches and resetting to generic), but they did not work correctly. The highest resolution I could get was 640 x 480. That's when I started searching for an answer. Again, frustration took over and I should have recognized it, stopped and walked away.

As for Envy, I found the program using Google, installed/uninstalled using Synaptic and apt-get several times. Each time no program icon appeared in the applications menu, and the package would not run from terminal using any of the switches provided on the Envy site and presented in Google searches.

Again, I apologize for cracking and hope anyone who read my ridiculous posts weren't offended too greatly.

---

### Post by bunty on 2009-01-06
Running one of those cards on Gentoo. Works perfectly.

lspci 
02:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

[ebuild   R   ] x11-base/xorg-server-1.3.0.0-r4 
[ebuild   R   ] x11-drivers/nvidia-drivers-96.43.07


If your total skill in "dicking about" is the windows 3 R's (retry , reboot, reinstall) you stick to windows, it was designed for dicks like you, if that's what you consider being a PC tech means. LOL.

Please don't use linux, please don't recommend it to your "prime time" customers. This influx of dick techs is rapidly polluting the linux user space.

You've been using windows for 15 years and it's so bad you're looking to change. After one hour of "dicking about" you give up on linux.

What a joke.

PS. Glad to see your last post above shows you have realised you were off the mark. Fair play for posting back to acknowlege your short-comings in dealing with it.

---

