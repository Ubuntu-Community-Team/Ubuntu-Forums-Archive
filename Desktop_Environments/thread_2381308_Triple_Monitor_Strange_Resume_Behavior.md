---
title: "Triple Monitor Strange Resume Behavior"
date: 2017-12-29
forum: Desktop Environments
---

### Post by Das Goat on 2017-12-29
System: Dell 7020, 4th gen i7, 16G RAM

Two video cards:

00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Turks PRO [Radeon HD 7570]

The intel has two display ports and the AMD has one display port. All three monitors match.

I have tested four versions and get similar results: U-16.04.3 LTS, U-17.04, Ku-17.04, and Mint 18.3


U-16.04.3 LTS & U-17.04, have the same results. Both install perfectly normally, inital reboot is fine and everything seems normal. But after resume / sleep, the 3rd monitor (attached to the Radeon HD) is just black. The mouse pointer moves all over it, you just cant see anything under it. If I move a windows halfway between displays, the system thinks it is moving the window there. If I go into settings / display, the system sees all three monitors and thinks everything is fine. I can even disable / enable and reorder the displays. However if I fiddle with it too much, the system crashes with a warning about running out of video memory. Sometimes I can reboot and get the system back, but once I have lost the 3rd monitor, it never comes back, it just stays black with a mouse pointer moving around it. I did see an error I couldn't capture that seemed to indicate a problem with Unity, so I tried to load Gnome. That crashed the system immediatly with the low video memory error.

I then tried Ku-17.04. It acted exactly like U-16.04.3 LTS & U-17.04 except that the two working screens behaved worse.

I am not on Mint 18.3. I'm not a fan of Mint, but I can live with it. Usually, all three monitors will work after resume / sleep. However, it will occasionally also do the wierd thing with the 3rd display EXCEPT that I CAN see the background wallpaper but I have no mouse. And for some reason, rebooting on Mint restores all three displays.  Also there's a lot of screen tearing with the pointer.

I did try adding nomodeset after splash with a space in between like this suggestion: [https://www.reddit.com/r/linuxmint/wiki/index/graphics](https://www.reddit.com/r/linuxmint/wiki/index/graphics)  to see if I could fix the screen tearing.

All that did was turn off two of the displays and put me in low resolution mode. I removed the nomodest and rebooted back to what passes as normal right now.

Finally, twice while I was writting this post, the two monitors on the integrated Intel adapter went crazy and the system froze, but the picture on the Radeon was perfect. I though maybe there was a problem with that card, but I just wrote all of this for the second time, in a text file first this time, and no trouble. Maybe that had something to do with Chrome?

While I am waiting for a suggestion from you good people, I will probably load Fedora or CentOS just to try something completely different. Or maybe work with Win 10 for a full day to see if any errors crop up there.

---

### Post by Das Goat on 2018-01-04
I've been working with Mint 18.3 for a few days now. Most of the time the resume behavior is normal, but if I leave it alone for an extended period of time, I get errors. Specifically, if I turn off the monitors, the system freaks out and can't recover. If I leave them on and resume after 12 ish hours, the left two work and the right just displays the background.  Init 6 fixes it, but that is inelegant. One I had to power cycle the computer to get anything back.

I hope everyone is still on vacation, because its not usually like the forum to be silent so long.

---

