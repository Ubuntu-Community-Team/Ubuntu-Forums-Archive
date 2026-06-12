---
title: "Strange XFCE / Xubuntu theme fluctuation"
date: 2008-04-02
forum: Desktop Environments
---

### Post by Polypropylene on 2008-04-02
Hi- I'm trying to install Xubuntu on an older laptop.  P3 600MHz, 192Mb RAM, 30G disk, screen is 1024*768.  It has no CD-ROM so I did a disk-image install.  During that install the only option was the "Ubuntu desktop" with no choice for Xubuntu, so I left it blank and set up with no GUI initially.

Then after I had it working with just the text mode shell, I installed xubuntu by writing:

apt-get install xubuntu-desktop

which did it's thing, taking a couple hours (not sure why it downloads at ~12K/s on this otherwise speedy conncetion).

Apparently you're not supposed to use apt-get for that, and rather use 'aptitude'?  This I read on some other posts after the fact.  Here is my problem.

When I log in, I get a blue background with an mouse and the XFCE logo.  And the panel at top has XFCE 'branded' icons; the help icon is a life-preserver.
However, if I do pretty much anything, it will turn into the Xubuntu "branded" desktop.  The life preserver changes into a question mark, all the windows change to a darker shade of gray, the background changes to a different shade of blue with no mouse, et cetera.  Almost comical at first, but it pretty much locks up the machine as the two themes struggle for dominance, with XFCE usually winning.  But I can't actually use the computer; most applications won't start, especially anything in the settings menu.  If I open up a term and run top at idle, sometimes Xorg is using 99% of cpu, sometimes not.

I removed X completely (via aptitute), and then re-installed using aptitude:
aptitude install xubuntu-desktop

that just finished after 3 hours of downloading again, but the problem is exactly the same.  It happens no matter what 'session' I choose in the beginning --except 'failsafe gnome', which doesn't work, and 'failsafe terminal' which give me the shell.  If I run that failsafe shell I can run the xfce settings panel but I have no idea what to fix or change.  

I've been trying to get this to work for 2 days now and I hope I don't have to reformat and try to re-install, but that's what I'll tonight try unless people have any suggestions here.

Thanks a lot for any help on this perplexing problem!

---

### Post by mali2297 on 2008-04-02
Interesting problem, a new one! :-)

Go to a virtual console, for example by pressing Ctrl+Alt+F2.
Kill the login manager:
```

/etc/init.d/gdm stop

```
Remove everything in the hidden directories ~/.config and ~/.cache:
```

rm -r ~/.config
rm -r ~/.cache

```
Then start the GUI with
```

startxfce4

```
Any improvement?

Did you install Xubuntu 7.10? (Not 8.04 beta.)

---

### Post by Polypropylene on 2008-04-02
Hey, that worked!  Thanks!

Now the xubuntu theme is the only one there, and the xfce style icons are gone.  most things seem to open, but there might be some other unrelated issues since it seems very slow, but I'll check those out myself.  This is with 7.10 by the way.

So I guess it's some problem with GDM, which I guess starts the graphical login screen?  Can I uninstall GDM and start by saying "startxfce4" all the time or should I try to get GDM to work the right way?

---

### Post by Polypropylene on 2008-04-02
Actually never mind, it seems to work properly even after I rebooted.  Great!

There does still seem to be some problem left in that Xorg uses about 20-30% cpu even when it's just sitting there, but looking around these forums it seems that's not an uncommon problem with new installs and I'll look through that.

Thanks again

---

### Post by mali2297 on 2008-04-02
> **Polypropylene said:**
> Hey, that worked!  Thanks!

Now the xubuntu theme is the only one there, and the xfce style icons are gone.  most things seem to open, but there might be some other unrelated issues since it seems very slow, but I'll check those out myself.  This is with 7.10 by the way.

Well, your specs aren't that impressive so it might be normal. You could try Fluxbox or some other light window manager (without Xfce).
To view the memory consumption, run
```

free -m

```
in the terminal. Does the system make use of the swap partition?

---

### Post by Polypropylene on 2008-04-02
Thanks, the swap seems OK.  Actually I figured out what was slowing it down.  It was the "system tray", in the top panel, but it showed up in 'top' as Xorg taking up CPU cycles.  

The computer is not very fast, but the mouse would at least move smoothly while logging in... until the panel opened, I realized.  If I killed the panel, things were much more responsive.  But I didn't want to not have the panel so I tried reconfiguring it.  If I set auto-hide to on, when it hid itself, things became responsive, and when I moused-over to make it appear, it would go back to 2 or 3 frames a second.  Then I removed parts of the panel, and when I got rid of the system tray, it no longer slowed the computer down.

Since all it had was an icon telling me my ethernet was plugged in (I'm sure it can do much more :) I'm fine without it.

And now the real work -- getting it to interface to the usb microcontroller camera I'm building!  Glayven!!
(I can't help but think of Professor Frink's voice every time I use linux.  Vastly slicker than the last time I used it years ago, but still kind of... nerdy? :)

---

