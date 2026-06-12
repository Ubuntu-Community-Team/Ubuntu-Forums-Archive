---
title: "screen resolution and scrolling poblems"
date: 2009-04-15
forum: General Help
---

### Post by saking on 2009-04-15
I have a computer with Windows XP.  I installed a second hard drive and installed Ubuntu 8.10 on the second drive to have a dual boot system.

Once Ubuntu was running, I noticed that there was a problem when scrolling.  In Web pages and other windows with scroll bars, The graphics would not refresh properly when scrolling.  Also, menu bars and icon bars would not be completely redrawn when windows would be moved or resized.

I thought maybe lowering the screen resolution would help.

I clicked System > Preferences > Screen Resolution

The resolution was set one level higher than 1024x768, so I set it to 1024x768.  The refresh rate was set to 75 Hz.  I noticed there were several other options here, but I left it at 75.

This did not solve the scrolling problem.

I had other work to do under Windows, so I rebooted.  When I logged into Windows, I noticed that my screen resolution has changed.  It is now set to 1024x768, and this is now the highest resolution available, whereas previously there had been a higher resolution which I had been using.

When I finished my work, I went back to playing with my new Ubuntu installation.  When I logged in, I found that my screen resolution is now set to 960x600 and this is now the highest resolution available.  The refresh rate is now set to 60 Hz, and this is the only rate available.

But, the scrolling problem is gone.

Look Ma, I fixed it :)

Can someone please help me understand what is going on here?

---

### Post by Narvinye on 2009-04-16
The drawing problems and scrolling is most likely being caused by the display driver that you are using.
Run ```
gedit /etc/X11/xorg.conf
``` to see what driver X is using.  I'd recommend finding an alternative display driver for the video card you are using.

You could also try running a repair on the display by booting into the recovery mode via Grub and running a repair on the display.  I'd recommend making a backup of xorg.conf in the event this leaves you in a worse position. (This may be done for you automatically)

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

As far as your Windows display settings being changed, I have no idea how that is possible. Cheers!

---

