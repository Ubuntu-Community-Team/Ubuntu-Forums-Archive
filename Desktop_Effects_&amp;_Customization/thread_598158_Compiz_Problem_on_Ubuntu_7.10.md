---
title: "Compiz Problem on Ubuntu 7.10"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by Dotan on 2007-10-31
Hi all,

I am using ubuntu 7.10 and I have an IBM T30 with ATI Radeon 7500.

When I used the Ubuntu 7.04 I installed Copiz Fusion and it all worked fine. Same computer, same graphic card.

When upgarding to ubuntu 7.10 I stumbled into a problem: "desktop effects can not be enabled" (System --> Preference --> appearance -->Visual Effects)

I guess it is because I am not using any XGL or AIGLX.

I tried many HOWTO's and nothing worked.
Actually it worked once - after installing XGL desktop effects worked, but it was TOO SLOW! how come?

My questions in short:
-- what graphic accelerator I need for my ATI Radeon 7500?
-- how can I not enable my desktop effects when it worked fine on the previous Ubuntu Version?

Thanks,
Dotan.

---

### Post by bananaman on 2007-10-31
Im on the same boat sort of... everything worked fine in Feisty... and now, its either compiz or video playback... boo hoo...:(

---

### Post by thrillhouse on 2007-10-31
Same deal with a T41.  Scrolling is super slow.  No direct rendering.  Google Earth doesn't work.  glxgears crashes the xserver (sends me back to the graphical log in).  Pretty frustrating.

---

### Post by Pathfinder_ on 2007-11-03
If it's slow when running compiz then you might want to change depth from 24 to 16 in your xorg.conf. That might speed it up.

---

### Post by kshane on 2007-11-03
> **Pathfinder_ said:**
> If it's slow when running compiz then you might want to change depth from 24 to 16 in your xorg.conf. That might speed it up.

I just tried that and when I restarted X, I had no video (black screen).  Had to boot to command line and change xorg.conf back...  Thanks for the try, though.  Mine is a little sluggish, but everything works...  Not as sluggish as when I tried using XGL, though..

Kevin

---

### Post by sean5446 on 2008-03-08
Hey I have a similar problem. I have a **Radeon 9200 SE**. I got compiz working this morning and it was great! (smooth, quick, and responsive) :D However, by 1:00, the effects stopped working up. 

I struggled with compiz for about a half an hour, battling back and forth between it working and not working. Finally, it won and produced the error, "desktop effects could not be enabled"

I did some searching on this forum and found that people fixed the error by installing the xserver-xgl package. I installed the **xserver-xgl** package and I was then allowed to turn on compiz and the custom effects. **However, now, the computer hangs and lags really bad. **

When I type compiz in the terminal I get:
```
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

Please help, this is only my second day with Linux!
Thanks in advance!

---

### Post by 22flames on 2008-03-08
Have you tried getting drivers for your video card and also download CCSM from add/remove programs than tell me your results:)

---

### Post by sean5446 on 2008-03-08
CCSM (compiz config) is already installed according to Add/Remove Programs. The driver I am using is "ati - ATI Mach8, Mach32, and Rage..." My video card is a Radeon 9200 SE. Do I need to find and install a new driver?

---

### Post by 22flames on 2008-03-08
that would probobly fix the problem:confused: do you need restrected drivers though....

---

### Post by sean5446 on 2008-03-08
Ive only been on Linux for 2 days. How do I update my drivers? How do I know if I need restricted drivers?

---

### Post by 22flames on 2008-03-08
trust me you do to aquire the drivers go to system preferances restricted drivers manager  it might be in admin. find your driver and installe

---

### Post by sean5446 on 2008-03-08
I went to screens and graphics in the admin menu. It says, "Graphics card (ATI Radeon (fglrx))". I press the Driver button and select "Choose driver by Model" scroll to ATI, and select "Radeon (fglrx)" and press OK, But when the window closes, the changes have not been made. Is fglrx the right driver and how to I apply it to my computer?

---

### Post by sean5446 on 2008-03-08
When I go to Restricted Driver Manager it says "Your hardware does not need any restricted drivers"

---

