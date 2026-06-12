---
title: "Grey screen on boot Inspiron 1501"
date: 2013-03-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Shapieron13 on 2013-03-22
Installed is an ATI Radeon Xpress 1150 card.  Since V11.04 I have been getting a grey screen on boot from a live cd.  Using 'nomodeset' in Grub  fixed this. Once installed everything works fine. Now at  V12.10 nothing helps.  Plugging in an external monitor I get a proper display, but the laptop screen is still grey.  The same happens with Mint, Mageia, Puppy 5.5 Racy, and several others. A long and intensive searche of several forums have been of little help.  Please help!:confused:

---

### Post by rparker on 2013-04-28
I am having the same issue. Were you able to find the cause and a solution?

I reverted to Lubuntu 12.04 and no problem with installation using 'nomodeset'.

---

### Post by Bill_Highestcreek on 2013-09-19
I was having the exact same problem on a Dell Inspiron 1501. It seems to be a problem with the display driver in the kernel. However, there is a work-around:
As you already mentioned, the notebook is booting and fully functional, it's just the screen that is not working correctly. If you disconnect the notebook from AC and wait until it goes into screen suspend mode (screen off, probably 5 minutes) and then wake the screen up again by pressing a key, the screen is working correctly. You can also try to close the lid, wait a few seconds ans open it again but that only works once logged in.
So, you could configure the time before shutting off the screen at 1 minute and automatic login, but you can also run a script at startup:

In Ubuntu / Mint etc:
Make sure you have automatic login enabled (sorry if that's a draw-back, but this trick is only working after the user is logged in...) 
edit the fle /etc/rc.local as root
Insert the following lines at the bottom, _above_ the very last line (exit 0):

```
xset dpms force suspend
sleep 1
xset dpms force on
```

That's it. Reboot and you'll still see the grey / white screen at startup, but after the system logged you in and starts X-windows your screen will switch off for a second and wakes up again. Works great and you can leave Grub as it is and have max sreen resolution.

---

