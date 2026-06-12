---
title: "Mouse Wheel-Up jumps back in Firefox"
date: 2009-06-10
forum: Desktop Environments
---

### Post by myonta on 2009-06-10
Hey folks. Stop me if you've heard this one...

So, an interesting little "feature/bug" has turned up (literally). When web browsing with Firefox (3.0.10) if I scroll up with my mouse it jumps back a page--usually only when I hit the top of the page, but sometimes immediately. 

Some may consider this a feature. For me, though, being a chronic "what did that just say" type of reader it is extremely annoying because I will be web browsing, scroll up, swear at the previous page(s) I've jumped to, and hit the forward button, trying to convince myself to to click the arrows on the right side instead.

Help me Ubuntu-Kenobi: you're my only hope!
~Jon

(PS: I only scrolled up once during the writing of this post, but it still filled me with regret)

EDIT: Here's an interesting tidbit that may help in the solution: I opened up Opera just to make sure it was just Firefox going back. It is, but in Opera I get the right-click context menu when scrolling up instead. Hmmm... So, what do I change in xorg.conf, then?

---

### Post by splashhtc on 2009-06-10
:D

i have a similar bug too

but in my case when i scroll up ..on the third scroll up the page goes the opposite way...

i had tested the opensuse on the same machine...(very frustrating distro) anyway,...but this bug doesnt occur ,...

any ideas...??

---

### Post by nigmac on 2009-06-20
I have a similar problem, when I scroll down on my mouse wheel firefox moves back one page and then when I stop scrolling, it reloads the page I was on! It's really frustrating. I had the same problem in Hardy but I found adding a line to the xorg.conf solved it. When I go into the xorg.conf on Jaunty the mouse section is hashed out saying HAL in use. How do stop this issue?

Thanks...

---

### Post by jay4rest on 2009-07-01
I am having the same problem, the minute I hit the top of the page it goes back to the previous site. It is so annoying that I am switching to Seamonkey until it is fixed. BTW if you scroll up when you hit the previous window it takes you back to the page you were at. It is a big loop.

---

### Post by jay4rest on 2009-07-02
THE FIX
I have managed to fix the problem. It appears that it might be an x-org setting? See below:
[http://www.linuxquestions.org/questions/linux-software-2/mozilla-firefox-mouse-scroll-wheel-behavior.-475209/](http://www.linuxquestions.org/questions/linux-software-2/mozilla-firefox-mouse-scroll-wheel-behavior.-475209/)

Here is what you need to do:
1. In the terminal type: sudo gedit
2. Enter password. This will give your text editor root privileges, which you will need.
3. Then open the xorg.conf file located at root level: etc/X11/
4. Add the following to the very end of the page:
Section “InputDevice”
Identifier “Mouse0&#8243;
Driver “mouse”
Option “Protocol”    ”auto”
Option “Device”     ”/dev/input/mice“
Option “Buttons”     ”5&#8243;
Option “ZAxisMapping”  ”4 5&#8243;
Option “CorePointer”
Option “SendCoreEvents” ”true”
EndSection

5. Then save the file.
6.  Type in the terminal: sudo dpkg-reconfigure -phigh xserver-xorg
7. Reboot and reinstall your video drivers (System>Administration>Hardware Drivers).

Jay Forrest's Tech Blogg
[http://jay4rest.wordpress.com/](http://jay4rest.wordpress.com/)

---

### Post by myonta on 2009-11-16
Alright, so maybe as the original poster I can resurrect this thread.

The story for me was that the problem disappeared on it's own. Yah, weird. However...

So, I've installed Karmic (fresh install, though my /home folder is preserved on a separate partition) and just noticed today that the problem has returned. So, I hunted down this thread and implemented the instructions from jay4rest and... well, after reboot I get a "K8 powernow failed transistion" error (I'll post verbatim if you like) and can get no futher than command line (ie: xserver isn't working).

Any idea what I should do? I'm guessing it's the dpkg-reconfigure command (what is "-phigh"?) and the default drivers don't seem to be loading. So, help!

~Jon

---

### Post by myonta on 2009-11-16
slight update: I can't seem to get to the command line. After GRUB I get this ('red-cube' is the computer name):

```
Ubuntu 9.10 red-cube tty1

red-cube login: [   141.780411] powernow-k8: vid trans failed, vid 0x1c, curr 0x18
[   141.780721] powernow-k8: transition frequency failed
```

So, yeah... I'd really rather not have to do a full reinstall if possible.

---

### Post by myonta on 2009-11-16
Ok... it's fixed. Here's the story (for reference sake):

After doing some investigating it seems that the "k8-powernow vid trans failed" error had to do with my Motherboard interacting with my CPU's voltage and Ubuntu wasn't having any of it! So, after grabbing DOS-on-USB 2 (from download.com) and the driver utility for my board (from ASrock) I managed to update my firmware.

With the error gone, I was left with a working command line. I had a backup of the original xorg.conf and, so, basically did this (first line is backing up the problematic xorg.conf):

```
sudo mv /etc/X11/xorg.conf xorg2.conf
sudo mv /etc/X11/xorg.conf~ xorg.conf
sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot
```
And, voila! I'm back in a full GUI Ubuntu and--lo and behold--the wheel-up issue has mysteriously disappeared once again. 

Well that was fun guys. :)

~Jon

---

### Post by rupert160 on 2010-06-11
Strangely I had exactly the same problem, it was just after I had vacuum cleaned out my computer. After putting everything back together including putting my USB mouse into a PS/2 adaptor and a KVM with a another "dead" linux box at the other end...

Everything worked fine except for the above problem. After shutting down and pushing the connectors harder together and rebooting... voila! It worked again. I'm glad I didn't go down the driver/Xorg.conf path...

---

### Post by Diskdoc on 2012-03-22
I'm having trouble with this. I'm using my USB-mouse through a PS/2 adapter and a KVM switch. Running Lucid.

Had a look at my X.org.0 log and it seems X.org ignores the settings in xorg.conf and detects the mouse on its own! Any suggestions on what to do?

---

### Post by overdrank on 2012-03-22
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

