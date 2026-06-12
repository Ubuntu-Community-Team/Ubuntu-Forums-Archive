---
title: "No Taskbar or Icons after startup.  Mini 9"
date: 2009-06-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Crickwilson on 2009-06-08
I worked on updating 9.04 all night last night after an all day hair puller trying to get the .img file to work, once I had worked it out I shut down and went to sleep. I wake up this morning and turn it on and I have nothing to work with, no taskbar, no icons, nothing but one untitled folder I created last night.

I'm actually using Ubuntu it right now. I used the folder I created to go to my pictures and made one of them open with firefox.  Thats the only way I could get it to open. 

I'm able to open windows to my documents etc. but I have no idea how to get to the terminal or any other program that could help fix the problem.

If this helps I will list the Programs I installed last night (from what I remember): 
> 
1. Updated repositories, third party etc.

2. Installed firestarter 

3. Compiz

4. Vlc media player

6. Restricted-Extras

7. WineI hope this is an easy fix, it seems like it should be but perhaps I'm wrong.

---

### Post by jaqrah on 2009-06-08
Are you using regular desktop or Netbook Remix?  The reason I ask is because compiz and Netbook Remix do not play nice together.  And I noticed you installed compiz.

---

### Post by Brandon Williams on 2009-06-08
My guess is that you used the desktop-switcher at some point, which is clearly called out as buggy in both the 'Known Jaunty Jackalope bugs' forum thread and the Jaunty release notes. Read the [bug report](https://bugs.launchpad.net/desktop-switcher/+bug/349519/comments/96) to find info about the fix, which is currently in Jaunty proposed.

---

### Post by tincoster on 2009-06-10
Hi Guys,

I have the very same problem. I had to re install my system 3 times to get back to normal. 
I realized that the problem is comming from Ubuntu updates. after the new updates and restarting the computer brings me to just only desktop wallpaper. Nothing else. 

Mouse is working fine, but cannot open any program or Ctrl, Alt, F2 etc are not working.

I tried with every available keys to change it but without any results.

I could only do is changing the wallpaper by right click on the desktop and Ctrl +Alt + Del to turn off the computer.

Only solution I have is reinstall all and prevent Ubuntu update.


Please Help.!

Andy

---

### Post by dileepm on 2009-06-10
Its obvious problem of compiz. To clear this get to boot menu --> recovery console --> drop to root shell

```
apt-get remove compiz-core compiz
```and then to reboot

```
init 6
```Login

---

### Post by ugm6hr on 2009-06-10
> **tincoster said:**
> I realized that the problem is comming from Ubuntu updates.

Not unless you have:
a. installed compiz
b. enabled non-standard repositories
c. run out of RAM

I have 9.04NBR running fine on my Mini 9, with latest updates.

I do use the standard Gnome interface though (which I would recommend).

---

### Post by ricog on 2009-07-08
Luckily, I had a keyboard shortcut setup for terminal. I could type desktop-switcher and toggle back and forth. Switching out of netbook-remix and back into it enabled me to see the remix menu. Which I then used to run Administration > Update Manager. Now when I first log in it is broke, but switching to either one gives me a fully working interface. A few things to note:


[LIST=1]
[*]I believe there may already be a keyboard shortcut for terminal without having to configure it. Does anyone know?
[*]Initial login just isn't initializing propery. To get that to work, one just needs to debug the boot process and login to see what's failing.
[*]Fortunately for Ubuntu (and most linux I know), reboots aren't a very common thing. So I think I can live with running the switcher manually if I have to reboot. At least until a fix can be found.
[/LIST]

---

### Post by MOMensink on 2010-03-25
> **tincoster said:**
> Hi Guys,

I have the very same problem. I had to re install my system 3 times to get back to normal. 
I realized that the problem is comming from Ubuntu updates. after the new updates and restarting the computer brings me to just only desktop wallpaper. Nothing else. 

Mouse is working fine, but cannot open any program or Ctrl, Alt, F2 etc are not working.

I tried with every available keys to change it but without any results.

I could only do is changing the wallpaper by right click on the desktop and Ctrl +Alt + Del to turn off the computer.

Only solution I have is reinstall all and prevent Ubuntu update.


Please Help.!

Andy
Hi all,

Brand new to the amazing world of Ubuntu and very much liking it so far! I got some experience in Linux from running a console-driven Linux-server (very stable!) and decided to take the plunge and convert my MSI Wind U100 into a Ubuntu remix (be it dual boot for the time being).
After the recent update (to much a newbie to sum up all the updates and knowing where to find the proper logs) I experienced the same problem as you guys mentioned: just a blank wallpaper, no application launcher activated or whatsoever. No permissions to do anything as a matter of fact, I wasn't given the opportunity to activate the key chain.

The solution I came up with is to log out, not switch user. While in the log-in screen, look carefully at the bottom of the screen. You'll notice the possibility to change the language and keyboard configuration, as well as - very strange - the option to change de mode in which Gnome will load. By default it is set to "failsafe". Tap on the options and select the regular Gnome. Login *et presto!* problem solved! (In my case). Everything loaded as usual, key chain activated, the whole monty.

Hope it helps!

Cheers,

MOMensink

---

