---
title: "How to change 'out of range' resolution"
date: 2011-10-01
forum: Desktop Environments
---

### Post by pcal on 2011-10-01
I've done a silly thing. Got a nice big new monitor to put on my No 1 machine, and moved its old not quite so big monitor to my No 2 machine. After connecting up the monitor, I booted the machine, and set the resolution higher to match the new monitor which seemed ok, then shut down the machine.

Now, a few days later, I've gone back to that machine but can't access the system as the monitor shuts down with out of range message whenever x tries to start.

I can still use the recovery mode to access the command line. The generic graphic mode offered in that menu generates a page of errors and returns to the menu before I've had a chance to read them all. I've tried a number of approaches found in various threads in this forum but no luck so far.

1 suggested removing a config file, but the file in question didn't exist anyway. Another suggested changing settings in xrandr, but that only generates errors about not being able to find any screens.

Sorry these messages are a little vague - I'm using the No 1 machine now, while the problem beast is in another location, so all these details are from memory...

How can I in a command line environment reconfigure x to use a lower screen resolution?

Thanks an anticipation,

Pcal

---

### Post by Palartzski on 2011-10-01
ive actually been running into a similar problem. ive been following this tutorial:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

my particular issue is changing the vertical and horizontal refresh rates. however, i run into issues when i get into command-line mode because it doesn't read any of my input. however, the tutorial above seems like it might apply to your problem as well but im not sure if you've already given any of those steps a try already.

---

### Post by pcal on 2011-10-02
Thanks for the link.

Didn't solve the problem directly, but provided the pointer to the means to do so.

The key was the xorg.conf file, once I had that opened in an editor, was able to manually change the display resolution to a generic value (I used 1024x768 ) which got x running ok - albeit crammed into one corner of the display.

After that I could access the configuration tool to set it to and test a range of settings until I found the right one.

My original error, was forgetting to hit the Apply button in the configuration tool. I thought I was looking at a newly configured screen, but it was just the old one with the new setting only taking effect after I rebooted.

Won't do that again!

Regards,

Pcal

---

### Post by Palartzski on 2011-10-04
i was wondering how you generated the xorg.conf. my system currently does not have one. ive tried to generate it using Xorg -configure, but i always get an error because my GUI is already running. any help would be greatly appreciated.

---

### Post by pcal on 2011-10-04
> **Palartzski said:**
> i was wondering how you generated the xorg.conf.

I didn't actually generate the file at all. It was already there in the appropriate folder as indicated in the 'howto' you linked to. I didn't have the gui running at all, so perhaps that is part of your issue? At boot time, on the grub menu, choose the 'recovery' version for whatever kernel you are using, then select the 'continue normal boot' option from the recovery menu, and it should (or at least, it did for me) drop you off at a command line interface from which the instructions in the howto all worked.


```
sudo nano /etc/X11/xorg.conf
```

This was the bit that cracked the issue for me. Several pages down through the file was a section that detailed the resolution settings, which I just edited and saved.

Hope it helps...

pcal

---

