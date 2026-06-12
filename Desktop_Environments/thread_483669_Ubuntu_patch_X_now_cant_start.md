---
title: "Ubuntu patch X now cant start"
date: 2007-06-25
forum: Desktop Environments
---

### Post by GNUoob on 2007-06-25
Hi all,

I recently did an install of Ubuntu a few weeks ago and all was well. really enjoyed it and have since been playing with it to get to understand linux better.

well last night i auto installed a update directly from ubuntu itself. i have not modified my apt sources so thats how i know. it told me an update was avail by the orange icon in the top right of my gnome desktop. well i installed it and rebooted later on to discover my desktop/x is now broke.

was it a bad patch? anyway to remove it and go back to what i had before?

i did the Cntrl+ALT+F2/Backspace to get my command line loaded and apt-gotted fvwm but that wont start upeither.


Help me please :)

---

### Post by Happy_Man on 2007-06-25
Was it the error that read, "Your Xserver failed to start...."? If so, keep hitting enter until you get to a text prompt. It will ask for you to log in, or you may be logged in already. Just get to a text that looks like "<yourname>@<your computer>$:" Enter in this command ```
sudo dpkg-reconfigure xserver-xorg
``` Keep hitting enter for all the defaults until you get to a long list of drivers. Scroll to select "vesa", and keep hitting enter until it finishes. the type ```
sudo reboot
``` Your computer should, hopefully, now reboot into a working GUI again.

---

### Post by GNUoob on 2007-06-25
Ok thank you for the quick response.

I am currently at work and will try this when i get home tonight.




my actual error is when the gui for logging in comes up my screen goes completely white. i cant see the box to put in my login name at all, completely white. right before this though i can see the Ubuntu scroll bar with the orange filling to the right as it loads the moduels/etc.

---

### Post by Happy_Man on 2007-06-25
> **GNUoob said:**
> Ok thank you for the quick response.

I am currently at work and will try this when i get home tonight.




my actual error is when the gui for logging in comes up my screen goes completely white. i cant see the box to put in my login name at all, completely white. right before this though i can see the Ubuntu scroll bar with the orange filling to the right as it loads the moduels/etc.
Oh. Then boot recovery mode, and use the commands I gave you.

---

### Post by GNUoob on 2007-06-26
its up and working

thank you

---

