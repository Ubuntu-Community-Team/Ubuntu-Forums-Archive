---
title: "Gnome not loading properly"
date: 2004-11-29
forum: Desktop Environments
---

### Post by beeldings on 2004-11-29
Everything was working fine until I started up my computer this afternoon. The boot process seemed to load properly, everything was listed OK, nothing failed. However, when Gnome was loaded and after it logged on as the user account, only the background color and mouse cursor were loaded. No splash screen, no panels, no icons, nothing. The same thing happened when I tried logging in as root and when I attempted to load the failsafe Gnome session.  After rebooting my computer, the problem still occured so I decided to restart X and load the failsafe terminal, which is where I loaded Firefox and posted this request for assistance. 

I have a slight idea on where to start. I was thinking of editing my /etc/apt/sources.list file from the terminal (sudo nano /etc/apt/sources.list) and switching everything to Hoary and then upgrading from Warty to Hoary. But I really don't want to upgrade to Hoary unless it's absolutely necessary. I don't want to go through another installation and configuration of Ubuntu, which takes me a good two hours on this computer.

What to do the Ubuntu experts of these boards suggest?

---

### Post by ralph_ubuntu on 2004-11-29
To get an idea about what the problem might be you could try to again start the failsafe terminal and start gnome-session from there. 

Also, what did you change, do before the problem occured?

---

### Post by beeldings on 2004-11-29
I remember loading a few programs from Synaptic, but that's just about all I did, besides updating the Hosts file. If it means anything, I left Firestarter running when I shut down the computer before the problem began. Do you think Firestarter had something to do with Gnome not loading properly?

I tried upgrading to Hoary to see if that would correct the problem, but it did not. What happened with the upgrade is that the kernel image was not installed correctly or became corrupt while downloading, so after I rebooted the computer, Grub could not find a suitable image (a file not found error was displayed) and I was no longer able to load Ubuntu. So, I had to install Ubuntu again, and here I am, about two hours later with a working Ubuntu system (knock on wood).

---

### Post by beeldings on 2004-12-01
The problem is back. I was just in Gnome not more than five minutes ago, and I restarted X because I was unable to access my home directory or the hard drive using the menu on the panel. Since restarting X, I am greeted with the log-in screen, and when I log in, I can see the background color and the mouse pointer, that's it. 

So, I loaded the failsafe terminal and entered "gnome-session". It returned a message about the session manager being /tmp/ubuntu/ICE or something very similar to that. I can easily install Ubuntu again if I needed to, but like I said previously, it takes two hours to fully configure Ubuntu on this machine.

When the problem previously occured, I had left Firestarter running. When I restarted X this afternoon, I left Firestarter running. Do you think Firestarter might be the cause? Before I had to restart X, I remember blocking port 1234 due to a hit I received in the program's log.

---

### Post by Vlekkie on 2008-04-08
I also have the same problem, though I encountered it with both 7.04 and 7.10.  I don't want to reinstall again as it was only the 4th time I booted it that the problem occurred.  The only change I recall making is loading the restricted nvidia drivers the first time I booted up, along with adding a few documents to the desktop (they are still visible.)

Please note that I am entirely new to any form of linux, so I would prefer the solution to be thorouhgly explained. Thank you.

P.S Apoligies for any spelling mistakes, firefox set to Afrikaans dict.

---

### Post by slamdunk on 2008-04-08
same problem here. I'm using since over a month hardy, and after upgrade of yesterday this problem is appared.

Any idea to fix it?

Thanks,
slam

---

### Post by Beaker Bongload on 2008-04-08
yep, same here. Everything works for me but the gnome panels. This mornings hoary update did it for me.

---

### Post by siddesu on 2008-04-09
meh -- ignore, wrong thread

---

### Post by haydonknight on 2008-07-20
Hi,

I'm not very experienced with linux/ubuntu, so may have some things wrong, but here is my 2c of (mis)understanding:

I experienced what I think is the same problem.  Upon a restart, the top/bottom areas of the gnome desktop stopped 'loading'.  The same behaviour occurred in a normal session, a gnome failsafe session, and a session where 'gnome-session' is typed into a terminal-only session.  Prior to this I had been:

+ fiddling around in my ~/.ssh/ directory trying to get an ssh agent working properly

+ getting annoyed with ubuntu (and osx:)) always trying to download updates for stuff I never used; and this using too much of my modest download limit.

+ adapting a strategy of uninstalling things using the synaptic package manager that I thought I didn't need.  This included 'cheese' and 'evolution'

A post on this forum: [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring-manager/+bug/202941]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring-manager/+bug/202941") suggests that it was uninstalling evolution that caused the problem.

I now have what appears to be a working gnome desktop.  To fix, I decided on a brute-force method of reinstalling the desktop manger.  I installed the kde desktop manager:

sudo apt-get install kubuntu-desktop

Then from that I re-installed the gnome desktop manager, which is confusingly to a newbie like me referred to as ubuntu-desktop:

sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop

I guess I didn't need to do the kde step; I guess I could have reinstalled from the failsafe terminal.  I'm not sure whether the 'apt-get remove' step was necessary either.

-Haydon Knight

---

