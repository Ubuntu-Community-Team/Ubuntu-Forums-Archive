---
title: "UNR 9.10 - slow transitions"
date: 2009-11-02
forum: Desktop Environments
---

### Post by cyberbug on 2009-11-02
I upgraded to 9.10 UNR on my Asus EEE904, everything works great except one big annoying problem:
In the main desktop window, everything is like slow-motion, the transition ob the pages, the scrolling, clicking on icons.
My netbook ran just fine on 9.04 UNR with its Atom processor and Intel videocard. 
The strange thing is that inside the application, everything works great, just the main window is lagging.
Anything i can do to fix that?

---

### Post by Glucklich on 2009-11-02
Can you tell me if your CPU shows up as being used at 100%? I've seen two other people with this problem.

If it is, you might want to try running:

> sudo dpkg-reconfigure -phigh xserver-xorg


Here's one of the other threads I told you about:

[http://ubuntuforums.org/showthread.php?t=1309738]("http://ubuntuforums.org/showthread.php?t=1309738")

See if this helps you. It might not be the same problem.

---

### Post by karl_kashofer on 2009-11-02
Hi !

I have the same problem, upgraded from UNR 9.04 to 9.10 and now the main window is unusably slow. It takes like 20 seconds to switch from one tab to the next.
Everything else is snappy.

Its not the CPU problem, and resetting xorg.conf does not help.

Advice anyone ?
Cheers,
Karl
Hw: EEE 900A Intel 945M

---

### Post by Glucklich on 2009-11-02
Ah... I didn't got that upgrading part. My apologies. Making a clean install, in general, is better than upgrading.
Wait a while to see if anyone comes with a more definitive answer for this issue. If nobody shows up, you got nothing to loose in trying a clean 9,10 install.

---

### Post by gadolinio on 2009-11-02
> **cyberbug said:**
> I upgraded to 9.10 UNR on my Asus EEE904, everything works great except one big annoying problem:
In the main desktop window, everything is like slow-motion, the transition ob the pages, the scrolling, clicking on icons.
My netbook ran just fine on 9.04 UNR with its Atom processor and Intel videocard. 
The strange thing is that inside the application, everything works great, just the main window is lagging.
Anything i can do to fix that?

I had the same problem. I think it may have something to do with the netbook-remix-like desktop, because by going to preferences-->choose desktop behavior or something like that, and then selecting the classic ubuntu desktop, everything worked fine, with the normal GNOME/desktop/wallpaper/panels/etc.

---

### Post by cyberbug on 2009-11-03
CPU is running at 100% on "Netbook-launcher", i did try to reconfigure the Xorg, but that didn't work.
anything else i can try?

---

### Post by hhboyhh on 2009-11-03
Hi, I am using a Toshiba NB100 and i am having the same problem. I first upgraded from 9.04 to 9.10 and sometimes the deskto was very slow. I agree with gadolinio, when you change to desktop mode, every thing works fine. The i tried a fress install of 9.10 but the problem still happens, is not so common as before but is still there.

---

### Post by karl_kashofer on 2009-11-05
Hi !

until this is fixed i would really like to disable the unr menu.
however, i could not find out how to do this.

please tell me how to restore the normal gnome desktop.
i am on german language, so a commandline would be best, or please be really specific about what icons to select.

desperate...


karl

---

### Post by sandman652001 on 2009-11-06
I think you should be able to get back a normal desktop by installing ubuntu-desktop

from the commandline
sudo apt-get install ubuntu-desktop

---

### Post by cyberbug on 2009-11-11
managed to solve this problem today, although, i'm not 100% sure what was exactly the cause.
My Asus EEE 904ha was very slow, and the CPU was running on 100% ever since i upgraded to Karmic UNR from 9.04 UNR.
Since my /home was on another partition (lucky me), today i formated the computer, and installed a fresh copy of Karmic UNR (on EXT4), this did the trick. my netbook is now responsive, CPU is 3%~ on the desktop.
If you can, my suggestion is to try a fresh install...

---

### Post by noliuz on 2010-02-12
i had this problem too with A8M Asus Notebook. but after i use latest nvidia proprietary graphic card , it gone.

---

