---
title: "Max Desktop Resolution = 1024x768 (4:3)"
date: 2009-02-05
forum: Desktop Environments
---

### Post by SwitchLink on 2009-02-05
I am running Ubuntu 8.10 64-bit with an Nvidia 8800 GTS video card.  I am running the Ubuntu recomended driver (1.77 I think, ran all updates last night) but my screen resolution is only 1024x768.

I seem to remember it was working a few weeks ago (1280x960 or higher).

I installed Envy, but never configured it because I found out I didn't need it (was an old article I found that came out before ubuntu supported the video driver).

I'm newish to Linux in General, and am trying to think of any other relavant data, but can't think of anything else other than making sure all the software was updated properly (apt-get in the terminal and the update through the GUI).

Is there a reason it used to work and now it doesn't?  I have no data on the machine and I am using the install to learn.

---

### Post by tsaowang on 2009-02-05
Hi,

did you try to download the latest drivers from nvidia ?
If not, go there [ftp://download.nvidia.com/XFree86/Linux-x86_64/180.27/](ftp://download.nvidia.com/XFree86/Linux-x86_64/180.27/) and download the latest driver for your version (supposing it's the 64 bit one)

Then, do the following :

How to install this drivers:

It is very easy and you can do it just following this steps. (I recommended to uninstall any previous version)

1) Download the driver (for example in your desktop)

2) Enter in a real terminal mode: CONTROL + ALT + F1 (don't do it now as you wouldn't be able to keep reading)

3) Turn off x.org:
Code:

sudo /etc/init.d/gdm stop

4) Go to your desktop:
Code:

cd Desktop

5) Run the installer:
Code:

sudo sh ./Nxxx.run

(If you hit TAB after the first N the rest of the filename it will automatically appear)
Don't forget to choose x.org automatic configuration at the last step inside the installation program.

6) Then you can turn on x.org again
Code:

sudo /etc/init.d/gdm start

And start your session again by typing:
Code:

startx


Good luck

---

### Post by surj08 on 2009-02-05
I use the restricted drivers that ubuntu recommends.

Goto >system >admin > hardware drivers

Easyest way I think...

---

### Post by surj08 on 2009-02-05
Would you mind providing instructions as to how to uninstall older versions?

Thank you

---

### Post by SwitchLink on 2009-02-25
I kept putting this on the back burner and ignoring it until today, when I finally got tired of working in 1024x768.

Since I was using the Ububtu drivers for NVIDIA that the system recommended and downloads automatically, I decided on a whim to remove "envyng-qt" since I didn't use it anyway

sudo apt-get autoremove envyng-qt

Now my desktop resolution is back to normal.  Sorry for going AWOL for 2 weeks.  I thought I had this thread on subscription and was relying on email notification to see if anyone replied to me.

So, while I'm not sure why envy restricted my desktop resolution, I did want to share this in case someone else had the same problem.

---

