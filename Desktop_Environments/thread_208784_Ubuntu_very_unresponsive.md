---
title: "Ubuntu very unresponsive"
date: 2006-07-04
forum: Desktop Environments
---

### Post by nostrich on 2006-07-04
After a 2 month trial run of Ubuntu on my secondary PC, a P3 650mhz with around 250mb RAM, I've switched my main PC over to Ubuntu. But it's really slow and unresponsive. My main PC's a P3 800mhz with 567mb RAM - there's no reason I can think of for it to be this slow.

All I have running is Firefox, irssi, Amarok and Gaim. Firefox will occasionally freeze up and become completele unresponsive for as long as 60 seconds. And if I run Azureus (or Ktorrent, but I prefer Azureus) it does exactly the same. 

The memory usage isn't too out of the ordinary, but CPU usage frequently hits 100% and stays there for ages.

Amarok is crashing frequently, too.

I had a look around the forums but couldn't find anything particularly helpful. Any suggestions?

---

### Post by lapsey on 2006-07-04
terminal command 'top' should give you a good idea of what's using the cpu


you can run as 'sudo top' for extra power

---

### Post by nostrich on 2006-07-04
Well thanks, but that doesn't help me solve any problems. amaroK seems to be using a large amount of CPU, but nothing else looks like it's hogging CPU.

---

### Post by phillywize on 2006-07-04
[QUOTE=nostrich]Well thanks, but that doesn't help me solve any problems. amaroK seems to be using a large amount of CPU, but nothing else looks like it's hogging CPU.[/QUOTE]
From your post, it looks like it *did* help you identify where the problem was coming from (unless you knew already, and weren't clear about it).

What about the good ol' uninstall - reinstall?

---

### Post by ubuntu_demon on 2006-07-04
Make sure you run the correct video driver. What kind of videocard do you have ?

You should try Xubuntu. Xubuntu can be installed right next to gnome(ubuntu) so you the option to choose from your login screen (click on session).

Xubuntu runs great on my P3 826 mhz with 512 mb ram.
$sudo apt-get install xubuntu-desktop

These threads have some general suggestions :
[http://ubuntuforums.org/showthread.php?t=190072](http://ubuntuforums.org/showthread.php?t=190072)
[http://ubuntuforums.org/showthread.php?t=186764](http://ubuntuforums.org/showthread.php?t=186764)

---

### Post by nostrich on 2006-07-04
ubuntu_demon: I was already using xubuntu. But it ran snappily enough when it was bog-standard Ubuntu anyway, so I don't think that's the problem.

My video card is an nvidia geforce 440mx. I installed the right drivers for it (I think). 

I'm going to reinstall the whole thing and do a trial-and-error as I install stuff and see what results in the slowdown. 

Any suggestions I should take on board about the order of things, or what I should install first, or anything like that?

---

### Post by ubuntu_demon on 2006-07-04
I don't think you need to reinstall unless you have seriously messed up your system somehow. Ubuntu doesn't have a registry which slows down the entire pc over time such as windows XP. 

Install (or make sure) the 686 kernel :
$sudo apt-get install linux-686

To install (or make sure) the correct video driver in your case :
$sudo apt-get install nvidia-glx
$sudo nvidia-glx-config enable

Now do a reboot to make the new kernel and videodriver in effect.

You should definetely look more into your memory usage.

What's the result of (during normal usage) : 
$free -m

You should try top :
$top 

press "SHIFT-o" and then "n" in order to sort on memory usage. Press q to quit the program. And copy-paste the results in this thread.

good luck!
(I might not check this thread for a day or so)

---

### Post by nostrich on 2006-07-04
Well I decided to just do it anyway. I've installed the 686 kernel and the video drivers, and xubuntu. Currently installing 99 updates, and it's all still nice and snappy. If I run into problems again I'll be back with $top results.

Thanks for the help thus far, guys.

---

### Post by ubuntu_demon on 2006-07-04
[QUOTE=nostrich]Well I decided to just do it anyway. I've installed the 686 kernel and the video drivers, and xubuntu. Currently installing 99 updates, and it's all still nice and snappy. If I run into problems again I'll be back with $top results.

Thanks for the help thus far, guys.[/QUOTE]
Okay good luck!

---

### Post by nostrich on 2006-07-04
New problem!

Everything was running along just fine, but after a reboot, the resolution has defaulted to 640x480, and the screen resolution settings have no higher options. It was previously set to 1600x1200. I didn't change anything system-wise - about all I did before it happened was install Azureus.

How would I enable the higher resolution again?

Edit: Actually now that I think about it - I did mount a Windows hard drive. When I tried to mount (mount -a) it said it couldn't mount it, I forget the specifics, but it's mounted fine now, at the cost of my resolution.

Edit2: Never mind, restarting Gnome seems to have done the trick. But now XFCE isn;t behaving properly. The panels are there, but the actual desktop is behaving like normal Gnome.

Edit3: I'm an idiot. All is well again.

---

### Post by .t. on 2006-07-04
I am glad to see your proficiency is improving and that Ubuntu is working for you. The more you work for it, the more you'll get out of using it, and the simpler it will be to maintain. Good luck!

---

