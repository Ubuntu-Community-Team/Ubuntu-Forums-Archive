---
title: "Top and Bottom System Trays/Desktop Icons Sometimes Missing at Boot"
date: 2011-07-25
forum: Desktop Environments
---

### Post by dubois928 on 2011-07-25
Ok so I have a problem. I've searched through the forums and found a lot of similar issues, but mine is slightly different. I figure there must be some other issue.

I am running Lucid Lynx 10.04.3. Sometimes when I boot the computer, my desktop icons are not there. I ended up looking for a solution, and found one:

1. Hit Alt-F2 and run gconf-editor
2. Go to apps/nautilus/preferences and check 'show_desktop'

However, show desktop was *already* checked. If I unchecked it, and then checked it again, the desktop icons appeared. Weird, but problem solved right? Wrong.

Sometimes when I boot, the desktop icons are gone again. This doesn't happen at every single boot though. When they are gone again though, I just have to go through the process again. Here's where it gets worse.

Also, sometimes at boot, both the top and bottom taskbars/system trays are completely gone, leaving just the desktop. Once again, this doesn't happen at every single boot. I can't really do anything, so I just reboot again and more often then not, things are back to normal. Or the trays are back, but the desktop icons are gone again.

The weird thing about this is it doesn't happen every time I boot the computer. So if there is a problem I just restart and things are usually fine again. However this is very frustrating, and NOT normal.

Also, because the default drivers for my NVIDIA GeForce MX4000 were not sufficient, I had to remove the Nouveau drivers and install nvidia-glx-96, which corresponds to the official NVIDIA Linux driver version 96.43.17. This is the latest driver version listed for my card on the NVIDIA website. I also had to downgrade from 11.04 because apparently the old drivers are not compatible with the new X Server version in 11.04. I don't know if this has anything to do with it or not. I'm wondering if maybe i should just get a newer card so I don't have to deal with the older drivers.

Help is very much appreciated. I would like to continue to use Linux, as I am trying to switch over from Windows. However I have faced a lot of hardware and graphics issues, as well as software problems. I'm wondering if these might also be caused by the same root issue.

Thanks,
Ken

---

### Post by Krytarik on 2011-07-25
I had the very same issue when I set up my Lucid 10.04. I, too, am using the nvidia-96 due to the old age of my card, it's a GeForce Ti 4200, and it's some 9 years old. Your's is just one year younger:
[http://en.wikipedia.org/wiki/GeForce_4_Series](http://en.wikipedia.org/wiki/GeForce_4_Series)

So, what you need to do is, add the following option to the "Screen" section of your "/etc/X11/xorg.conf":
```
Option         "AddARGBGLXVisuals" "True"
```This should fix it.

Btw., nice to meet someone with a similar old setup. :-D We might want to upgrade at some time. But my system is still running fine enough to not bother too much about upgrading, which would, obviously, mean buying a new system. ;-)

Greetings.

---

### Post by dubois928 on 2011-07-25
Well I tried what you said and it appears to have been successful. I couldn't edit the xorg.conf because it was read-only, so I used sudo gedit in the terminal. After editing the file, I rebooted 5 times to check to see if anything would disappear and so far everything shows up. However, when any animation at all was shown on screen, including mousing over an object, flashes in the shape of small rectangles and horizontal lines appeared on the right side of the screen. I thought maybe it had something to do with my NVIDIA control panel settings, as I had increased anti-aliasing and anisotropic filtering to try to get Minecraft to look better. So I set those back to default and the flashes aren't showing up anymore.

So thank you very much! Unfortunately this does put more of a damper on Minecraft, which I have been struggling to get working and looking well in Ubuntu. Maybe I really do need to upgrade my graphics card...

BTW, If I am the original user and administrator on this computer, then why are  some files and things restricted and require the use of the terminal and  sudo or su?

-Ken

EDIT:

Now I'm seeing some of those lines/flashes rather infrequently, as well as some buttons being blacked out until I mouse over them. Also Minecraft lags more as well as other graphics-intensive applications.

---

### Post by Krytarik on 2011-07-26
> **dubois928 said:**
> 
BTW, If I am the original user and administrator on this computer, then why are  some files and things restricted and require the use of the terminal and  sudo or su?

Well, that's the inherent multiuser, security policy of Linux, and the primary reason why Linux systems are almost immun against malware.

Please see here how to correctly use "sudo" and its colleagues, I strongly advise using "gksudo" to run graphical apps with root rights, otherwise you can possibly screw up your profile:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Regarding Minecraft, try disabling Compiz while running it, it should help a lot. Therefore, run this command via the Alt+F2 dialog (not the Terminal!):
```
metacity --replace
```
To re-enable Compiz, run:
```
compiz --replace
```

---

