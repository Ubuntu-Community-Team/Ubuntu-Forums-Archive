---
title: "No desktop"
date: 2009-05-03
forum: Desktop Environments
---

### Post by PeterK-NC on 2009-05-03
Earlier this week, I purchased my first Linux computer, an EEE PC 900 (4 GB SSD, 512 MB RAM). A friend gave me the Ubuntu Netbook Remix pen drive version, and having liked Ubuntu, I installed it so that it would run on my computer. Everything was fine.

Yesterday, I installed Kubuntu to see what it was like. It took up too much space on my netbook, so I downloaded the Ubuntu Netbook Remix to my Mac and followed the instructions to make my own pen drive bootable version.

Each time I install Ubuntu on my netbook, my desktop disappears after restarting my machine. When I turn my computer back on, I get to the login screen. I log in successfully, but all I get is my background. I can right click & create folders, change wallpaper, and create an OpenOffice doc. But I do not have my menu bars.

<REVISED TEXT>
I should also say that the missing desktop seems to happen after I run the update manager. I update the packages that are provided by the manager, and then I restart my computer. It's at this point my desktop disappears.
</REVISED TEXT>

I have tried different login options, none of which seem to work: the GNOME session (just get wallpaper), Failsafe GNOME (just get wallpaper), Failsafe terminal (get a terminal, but I'm not sure what to do with it).

Before my missing desktop experience, my computer was connecting to my wireless network. I'm not sure if I'm connecting to my network when I'm now logging in with a missing deskop.

So, is there a way I can get my menu bars back?

---

### Post by joshedmonds on 2009-05-03
Have a read of the following threads, I had some success with the quoted solution (the launchers, not the .deb), but only perfect results with a reboot:

> **njpatel said:**
> This a bug in the desktop-switcher package ([https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519](https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519)), which I'm trying to fix and get uploaded to Jaunty before release.

To fix the issue you have currently (gnome-panel and/or windowmanager not starting), please run the following command depending on which mode your currently running in:

If in Netbook-mode, should execute:

gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel"]

If in Classic mode:

gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel","filemanager"]

I have updated desktop-switcher .debs available in that bug for which I am looking for testers (I would appreciate feedback on that bug). Once you've run the above commands, you can install the latest deb from that bug and hopefully further switches will work without issue.

Thanks and sorry for desktop-switcher screwing up :)

-- Neil

 and

[http://ubuntuforums.org/showthread.php?t=1136567](http://ubuntuforums.org/showthread.php?t=1136567)

---

### Post by joshedmonds on 2009-05-03
Having reread your post and seeing you haven't used Ubuntu for long, I'll go a little more step by step with what worked for me:

I had no top or bottom panel when I used the 'desktop-switcher' application (System -> Preferences -> Switch Desktop Mode) to return to the 'Classic Desktop'. I rebooted and when at the full 'Classic Desktop' created the following launchers. If you can't get to a full desktop, boot with a liveCD and put these launchers in the /home/<username>/Desktop folder of the install.

Right click on the desktop, select 'Create Launcher', and paste the following into the box labelled 'Command':

```
gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel","filemanager"]
```

Give the launcher a 'Name' and click 'OK'

This will create an icon on your desktop that you can double click to run, and which should restore your panels.

You can also create a launcher for 'desktop-switcher' on the desktop by dragging the launcher from the menu. A copy will be made on the desktop. This way even if you don't have panels, and the first launcher doesn't work, you can return to the UNR desktop.

---

### Post by PeterK-NC on 2009-05-03
Thank you for your patience & understanding. Based on your help, here is what I did:

I've reinstalled Ubuntu so many times, I can't remember if I was last in Classic mode or Netbook mode. So I followed both sets of command lines a couple of times apiece. Still no luck.

So is my final solution to re-install Ubuntu (which I don't mind doing) and dragging the desktop switcher to my desktop so I always have it around?

And what causes this so that it stops happening? I feel comfortable with Ubuntu (not a big switch having grown up on a Mac), but if I have to constantly have to struggle with my desktop, it does make it frustrating.

---

### Post by pauna on 2009-05-03
> **PeterK-NC said:**
> 
So is my final solution to re-install Ubuntu (which I don't mind doing) and dragging the desktop switcher to my desktop so I always have it around?


I'm not sure what your aim is (always use UNR/classic or switch between modes etc), but reinstalling is probably not necessary.

First you need to try to launch a gnome-terminal window by pressing Alt-F2 ("Run application") and entering gnome-terminal. When you have the terminal window, you can launch the command "gnome-panel" and see whether that gives your panels back.

I was bitten by this bug with my EEE PC 901 and launching the gnome-panel command just once as above restored my panels and they are now permanent. However, I do not switch between UNR mode and classic mode, I stay with the classic look permanently.

---

### Post by PeterK-NC on 2009-05-03
Too late…I've already started the re-install process.

I've tried the ALT+F2 process, but I couldn't get the keys to respond.

I'm content to stay in Classic mode, and I always want my desktop around (top & bottom menu bars).

I still don't know what's going on & why my desktop disappears. Is there something in one of the updates that I need to uncheck?

I guess that may not be a fair question since no one can actually look at my laptop…come tomorrow, I'll have some of the developers at my office look things over to see if they can't help me while looking at my laptop.

---

### Post by joshedmonds on 2009-05-03
Just to confirm your experience, when the Gnome panels gave up the ghost on me, the only alt+ combo I could use was alt+F6, which gave me the most recent windowed application (this was Nautilus for me).

Ultimately the switcher is buggy, and as Pauna says, it might be worth picking a mode and sticking with it for now. This answer might not be quite what you were looking for, but that's part of the fun - remember 8.04 is the stable long-term release (If 9.04 is causing problems, I personally would try 8.10 before 8.04).

Your problem may also be outside the realm of what we've offered (i.e. not related to UNR / switching at all), and if so you might want to repost this problem with a different heading e.g. Ubuntu - gnome panels missing on EeePC 900 after update.

I apologise for also not clarifying the actual desktop environment you are using, you do mention Kubuntu just once but not the KDE login options so everything above assumes Gnome (the default Ubuntu window manager)

---

### Post by trjames on 2009-05-03
so, i've followed these directions and now i can see my panels but when i close the terminal. it tells me that there are still processes running and it all goes back to no panels when i close it anyway. **how do i get this to stick after closing the terminal?**

---

### Post by Brandon Williams on 2009-05-03
I suggest that you download the .deb referenced in [this blog post](http://www.ubuntumini.com/2009/04/desktop-swticher-is-kind-of-broken.html) and install it. This version not only works, but also corrects the problems caused by the other one.

This .deb version comes direct from Neil Patel, the author of the desktop switcher. It will hopefully make its way into an official update soon.

You may want to try this to straighten things out first:
    1. log out
    2. at the gdm login screen press Ctrl+Alt+F1 to get to a console login
    3. log in
    4. rm -rf .gconf
    5. logout
    6. Ctrl+Alt+F7 to get back to the gdm login screen
    7. login

When I originally had the problem you describe, this method cleared it up. It's sort of a brute force method compared to the previous suggestion of using gconftool-2, but since the other method hasn't been working for you, this might help. Make sure you download and install the suggested version of desktop-switcher first, though.

---

