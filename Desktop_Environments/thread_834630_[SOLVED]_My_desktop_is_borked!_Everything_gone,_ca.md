---
title: "[SOLVED] My desktop is borked! Everything gone, cant run anything."
date: 2008-06-19
forum: Desktop Environments
---

### Post by izzmit on 2008-06-19
Final Update:
Somehow my gnome-panel was uninstalled. I reinstalled it and its all back to good.
Feel free to close.

[System:
Dual boot Hardy Heron/ Win XP Pro
ATI X200M integrated gfx
1250m ram
]

Update: Seems to just be my taksbar thingy. Everythign else seems functional.

So, I was just getting the hang of this linux thing. I finally got Wireless going, got firefox updated, installed VLC Media player, and was watching a movie while installing the ATI Drivers following [these instructions]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide").
Everything seemed to be doing well, and i got through all these commands:
```

sudo apt-get update	
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

```
Well, it had just finished and I went to minimize VLC and accidentally exited it. I went to reopen it and it wouldn't open.
I assumed it must still be running in the background like things do in windows, and tried to go to system monitor to force it to end.
System Monitor wouldnt open.
Annoyed, I restarted.

Everything is gone. "Everything" being the bar along the bottom (it defaults to along the top of the screen in a fresh install).
I like a clean desktop, I spose.

Anyways, my screen is completely blank with only a cursor and the background image. I can still get the right click context menu, and from there I was able to make a new desktop icon, open it to get into the file browser, open some random file in there with firefox and managed to get my browser running.

So, I can run my programs fine, it seems, and can Alt-Tab to different ones, but there is no running program icon anywhere on the desktop.

I cannot do alt-f2 and try to run commands, because nothing comes up.

I cant access the terminal, cuse I have no clue where to find it without the "accessories" menu.

I can right click and make new icons, but I cannot right click "make new launcher"

Strange thing i noticed:
I had installed WICD networking to replace the one that comes default, and it was working OK, but the couple times I used it, I had to restart the daemon before it would connect. For some odd reason, when I got firefox open, I was already connected. It was set to auto connect, but hadnt done so successfully in the past. This may or may not be related, but I figured id mention it.

Please help! I was just starting to have fun with this.

Update:
I found a link to a nifty little program Gnome-do (like launchy in windows. kickass)
I Installed it, and then used "open file with" and in the little command box beneath it I ran it with gnome-do. Now i have gnome-do running, and can therefore access the terminal now. Happy day, but now what?

---

