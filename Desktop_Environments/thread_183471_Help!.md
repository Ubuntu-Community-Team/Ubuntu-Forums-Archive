---
title: "Help!"
date: 2006-05-28
forum: Desktop Environments
---

### Post by Mohammad Ansarin on 2006-05-28
Hi

I just got my ubuntu from the mailing service (THANK U!) and i try to start it with the live cd, and the ubuntu loader starts and all but after loading when it's sopposed to display something like the welcome screen the screen goes funny and displays a bunch of colorful vertical lines. my vga card is nvidia fx 5500. should i install linux? should i get a new vga card? should i forget linux altogether? (:( ).

thanks 

bye

---

### Post by Sutekh on 2006-05-28
No don't give up.  All that is required is to install some video drivers that are more suited to your card.

Try Method 1 in this thread

[Ubuntu Forums - HOWTO Latest NVIDIA Drivers]("http://www.ubuntuforums.org/showthread.php?t=75074")

You can also give this a shot in the LiveCD too, you don't have to install to check out whether or not this will work.

---

### Post by Mohammad Ansarin on 2006-05-29
hi again, i'm not that much up on linux so, how do i install the drivers when i cant even get into linux? and i don't know how to work in the linux environment, so i need help on that too.

thank u

m a

---

### Post by Sutekh on 2006-05-29
[quote=Mohammad Ansarin]hi again, i'm not that much up on linux so, how do i install the drivers when i cant even get into linux? and i don't know how to work in the linux environment, so i need help on that too.

thank u

m a[/quote]Oh, it goes completely screwed.  Ok, you can still fix this.

Next time you get all that messy screen stuff, press Alt+Ctrl+F1.  This should take you a text screen.  It should look like ubuntu@ubuntu :~$ (I think)

Anyway you can use this command to change the video drivers temporarily to the **vesa** drivers, which seem to be a general fix-all driver.  This should work for your NVIDIA card.
```
sudo dpkg-reconfigure xserver-xorg
```
- this command will reconfigure the X server (the GUI), you will be asked a long string of questions regarding the input devices of your PC; your keyboard, mouse and monitor. If you don't know what you should answer to these questions go with the default/suggested ones.
 
  - the important step is when you are asked to choose the video card driver for the X server choose **vesa**
 
  - once you are done use this command
 ```
sudo /etc/init.d/gdm restart
```  - this will restart the GNOME Display Manager, and start the GUI.

If this gets the GUI working you can still try to follow the thread I originally linked.  It will install the more appropriate NVIDIA drivers.  If you install Ubuntu you may need to do this again.

These links may help you get along working in Linux

[http://psychocats.net/ubuntu/installingsoftware.php](http://psychocats.net/ubuntu/installingsoftware.php)

[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by steve.horsley on 2006-05-29
> - this command will reconfigure the X server (the GUI), you will be asked a long string of questions regarding the input devices of your PC; your keyboard, mouse and monitor. If you don't know what you should answer to these questions go with the default/suggested ones.
It is my understanding that just accepting the defaults for everything else should be OK.

---

### Post by Sutekh on 2006-05-29
[quote=steve.horsley]It is my understanding that just accepting the defaults for everything else should be OK.[/quote]If I recall correctly, but sometimes I don't, there were two or so questions where the cursor was active on No, but the dialog suggested that Yes was good to use.

So I try to disinguish between default (just press Enter all the time) and suggested (going by what the dialog suggests) values

Either way you should come out okay in the end.

---

### Post by Mohammad Ansarin on 2006-05-30
Hi.

Thank u very much sutekh. i got into the gnome environment and well, enjoyed it. now what do i do, go with method 1, and install the nvidia driver? 

thank u again

bye

m a

---

### Post by tseliot on 2006-05-30
[QUOTE=Mohammad Ansarin]Hi.

Thank u very much sutekh. i got into the gnome environment and well, enjoyed it. now what do i do, go with method 1, and install the nvidia driver? 

thank u again

bye

m a[/QUOTE]
Yes, method 1 should work just fine.

---

### Post by Sutekh on 2006-05-30
[quote=Mohammad Ansarin]Hi.

Thank u very much sutekh. i got into the gnome environment and well, enjoyed it. now what do i do, go with method 1, and install the nvidia driver? 

thank u again

bye

m a[/quote]Hey thats great!  

Yes go with Method 1, you should find it straightforward.  If not, don't hesitate to ask for help.

---

### Post by Mohammad Ansarin on 2006-05-30
Hi again.

I have the nvidia driver 8212. can i go with method 2 to install the real driver or should i first try method 1 and when it works, work on method 2?
thank u tseliot your thread was VERY useful

thank u 

bye

m a

---

### Post by Sutekh on 2006-05-30
No you've done enough.  Method 1 is still the real driver, just the one that has been packaged into a file that can be installed by apt-get.

You don't need to use Method 2 unless the Ubuntu NVIDIA drivers dont work or you need a specific version.

A most very useful thread I agree, I need it quite often

---

### Post by Mohammad Ansarin on 2006-05-30
by the way should i install ubuntu and then do this??

bye ma

---

### Post by Sutekh on 2006-05-30
[quote=Mohammad Ansarin]by the way should i install ubuntu and then do this??

bye ma[/quote]LiveCDs are pretty good indicators of real hardware issues you may have when you install.

It is most likely you will need to follow these fixes if you install Ubuntu.  The good thing is, that using the LiveCD you know that you can get it working.

---

### Post by Mohammad Ansarin on 2006-05-30
thank u for ur great help. my email is [email]mansarin2005@gmail.com[/email] if u need to send an email.

i want to install ubuntu now. should i first try method 1 on the live cd and then try to install it? i'm pretty good with computers but linux is a new experience for me.

thank u for ur help

bye 

m a

---

### Post by Sutekh on 2006-05-30
You could try the Method 1 on the LiveCD or if you want to get things rolling, go for the install.

Are you planning to dual-boot with Windows?

You can't go past this great guide on dual-booting with Windows (just a good guide in general for the installation process)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Mohammad Ansarin on 2006-05-31
1. what the heck is dual boot? 2. i TRYED to install ubuntu but the installer just stops on 23% gives an error and gives a route to bootstrap.log and closes the base system installation. 3. THE INSTALL WRECKED MY WINDOWS! the incomplete install not only didn't give me linux, it even wrecked my boot menu and after 10 hours non-stop coffee-espresso-cafelate-tea-icecream i managed to get my two windows xp os's running and FINALLY they worked and i came online to give u this message, sutekh. HELP ME!!!

i tryed to install linux with the expert install, and it stopped on the base system, i even did the partitioning and freed up a 10GB partition for linux. so, how do i install linux?

Thank u

bye

m a

---

