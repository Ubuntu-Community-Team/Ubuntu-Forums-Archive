---
title: "no right-alt in 9.10 desktop on asus 1005ha"
date: 2009-11-17
forum: Desktop Environments
---

### Post by stairwayoflight on 2009-11-17
Hello there,

I along with many have been enjoying Karmic since its release. However, I am having a few issues.

Number one right now, is the keyboard. At the moment, when I boot into 9.10 Ubuntu Desktop and hit alt-tab, I am unable to switch between applications. This behaviour isn't occuring in Windows, as I am able to switch using the same alt and tab with no problems.

It may be hairy debugging the problem, because I have an Asus 1005ha and its been having keyboard issues (in Windows also). The one issue I am seeing repeated in Windows, is that after the machine is on for some time, the keyboard shuts down. The system doesn't respond to keypresses unless I insert a usb keyboard or reboot. (This problem is rumoured to be due to heat. Maybe a fan control script would prevent this.)

For starters, can someone help me with my alt-tab problem? I don't know where to start, but here is a snip of my xev output. When I depress right alt and release, I get:

KeyPress event, serial 36, synthetic NO, window 0x4000001,
    root 0xfa, subw 0x0, time 241894, (164,13), root:(907,175),
    state 0x0, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4000001,
    root 0xfa, subw 0x0, time 242285, (164,13), root:(907,175),
    state 0x80, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

The interesting part is that in Ubuntu, when I hit right alt-tab, a tab character is produced for program input. That is, a tab is entered in gedit, and Bash interprets it as a tab also, offering completion options. I have only used UNR on this computer up till now. The present behaviour is new, after a fresh install of Ubuntu Desktop from the alternate install cd on usb. Maybe I'll try and duplicate the problem using the standard desktop installer.

---

### Post by stairwayoflight on 2009-11-17
Ok, it seems the problem doesn't occur with the desktop system installed from the livecd. The problem only occurs when installing from the alternate iso. I should also mention I had used the ubuntu usb startup disk creation utility to use the installer from usb.

It is a bit perplexing, as I had wanted to start from a command line system. My 1005ha doesn't have an optical drive, and the alternate cd doesn't recognize my usb dvd rom drive. It seems it is still a bit fudgy to install such a system on my hardware.

My issues from this point are pretty much resolved (grumble, grumble). But my conscience makes me wonder if it is better to file a bug about the problem. (I wouldn't even know what to file it against at this point.) Maybe in a week or two after I fix my desktop I can set up a couple of vm's and compare the filesystems/files.

---

### Post by Johannes Eva on 2009-11-18
Do you think it's related with your Laptop?
Same problem with DELL XPS M1330.

Installed from the live CD, same problem!!!

Maybe:
[https://bugs.launchpad.net/ubuntu/+bug/382473](https://bugs.launchpad.net/ubuntu/+bug/382473)

---

