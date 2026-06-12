---
title: "Breezy Keyboard Woes"
date: 2006-02-16
forum: Desktop Environments
---

### Post by jckdnk111 on 2006-02-16
I installed breezy on my new Sony Vaio (model PCG 6G4L) and it worked great until I set it down on the docking station which has an external usb keyboard and mouse.

X-Server couldn't start, so I made a backup of /etc/X11/xorg.conf and ran the following: sudo dpkg-reconfigure xserver-xorg

This seemed to have fixed me right up.....everything was working great (and still works great) when I am docked, but when I am undocked my keyboard acts strangely. Any key with a built-in function (as in requires you to hold the FN key to use the secondary function) displays the function without me pressing the FN key.....so my "J" key also normally serves as a "1" when the FN key is pressed. Now when I press the "J" key i see a "1" unless I hold the FN key in which case I get a "J"....all other keys without secondary functions work as they should (I type "A" and get "A").

I've tried everyone's advice in every thread I can get my hands on with no luck. Also, the keyboard works fine from a console (not terminal). I of course tried running dpkg-reconfigure xserver-xorg again with no luck....I tried reverting back to my known good xorg.conf, I even tried un-installing / re-installing xkeyboard-config and x-window-system-core with no luck....I booted up a live breezy disc and tried copying over it's xorg.xonf with no luck, I removed / re-added my keyboard under System > Prefs > Keyboard > Layouts.....I am at a breaking point here....please help!

---

### Post by dcstar on 2006-02-16
[QUOTE=jckdnk111]I installed breezy on my new Sony Vaio (model PCG 6G4L) and it worked great until I set it down on the docking station which has an external usb keyboard and mouse.
.....[/QUOTE]
This any help?:

[http://ubuntuforums.org/showthread.php?t=87619&highlight=Sony+Vaio](http://ubuntuforums.org/showthread.php?t=87619&highlight=Sony+Vaio)

---

### Post by jckdnk111 on 2006-02-16
hmmmm....thanks for the link, but unfortunately it didn't get me anywhere.

I am really stumped on this.....is there maybe a way to force x-windows to use the same keyboard settings as the system (as in console)?? 

I could take the time to re-install everything, but what if it just happens again....I love Ubuntu and I will do anything I can to stick with it, but I have to be able to use my laptop....arrrrgggghhhh! Maybe I should try Kubuntu,???

---

### Post by pippin on 2006-02-17
hi there  don't suppose u managed to figure out how to fix your problem because i have the exact same thing happening to me.its driving me nuts.looks like i,ll have to do a clean install, oh well........

---

### Post by jckdnk111 on 2006-02-17
OK I got it....if you have enabled auto-num lock on gnome (which is included in automatix I believe) with a standard pc104 US keyboard and then unplug the keyboard (or un-dock it in my case) you might run into this problem.

a useful tool in troubleshooting a keyboard problem is xkeycaps ... basically a gui for xmodmap which shows the exact mapping of every key as you type.....great tool!

The fix, turn off num-lock (hold down FN and hit the numlk / scrlk) or uninstall numlockx......I still love ya Breezy :)

---

### Post by pippin on 2006-02-17
excellent stuff jckdnk111  that worked a treat :mrgreen:

---

### Post by persev on 2006-05-09
Finally a fix thanks! I will post links to this thread in other threads about this problem.

---

