---
title: "Any news on Intel driver for Studio Hybrid?"
date: 2008-11-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Scheater5 on 2008-11-04
There's talk [here]("http://ubuntuforums.org/showthread.php?t=875771") but the thread is pretty much dead - but I wondered if there was any news on getting the graphics card in the Studio Hybrid (apparently "Eagle Lake," under generic name X3100) to work with the appropriate driver as opposed to the Vesa driver?  I'm planning on getting one here soon for an HTPC, and I'd like to know how the graphics are going to look under ubuntu.  Thanks in advance.

---

### Post by superm1 on 2008-11-05
Should work on intrepid AFAIK.

---

### Post by Waschmittel on 2008-11-06
Works like a charm. I had a problem with tearing when watching videos with  XVideo because the new driver uses textured video per default. But I found out that by manually setting the XVideo adapter to use to 1 in VLC for example, tearing can be avoided. The disadvantage of that method is that you get a blue rectangle in the task swicher instead of the video if you compiz.
So you have to choose between slight tearing or not having a correct miniature view of the video when using compositing.
Apart from that DVI etc. works perfectly out of the box.

---

### Post by Scheater5 on 2008-11-07
Good news - I won't be using compositing at all.  (that is, unless the transparency in XBMC is compositing)

---

### Post by sirebral on 2008-11-07
I am using a Studio Hybrid right now.

Setup was simple.  Insert Disc then Install.

It runs Compiz with the advanced effects.  However, it has problems with 3D overall.  I can run 1 3D process at a time.  I have problems with NwN Using the Linux Client - It's installed but Aborts at certain places (attempting a re-install later) - and I cannot run it unless the appearance settings are None.

I have ran some files from Torque as well.

---

### Post by emteeoh on 2008-11-14
I'm having problems with the Studio Hybrid and 8.10. It doesn't always work: after the bootsplash, the screen goes blank, and my monitor eventually shuts off. Hitting alf-F* or ctrl-alt-F* make no difference, so I don't know if its just a video problem or a generic boot problem. What I've been finding is that if I go into recovery mode then boot from there, it works fine. To me, that suggests some sort of initialisation problem.


When it boots, its fine though. The optional wifi card works with the Broadcom STA wireless driver, and the wireless keyboard and mouse work out of the box.

---

### Post by robertj20112 on 2009-03-06
> **emteeoh said:**
> I'm having problems with the Studio Hybrid and 8.10. It doesn't always work: after the bootsplash, the screen goes blank, and my monitor eventually shuts off. Hitting alf-F* or ctrl-alt-F* make no difference, so I don't know if its just a video problem or a generic boot problem. What I've been finding is that if I go into recovery mode then boot from there, it works fine. To me, that suggests some sort of initialisation problem.


When it boots, its fine though. The optional wifi card works with the Broadcom STA wireless driver, and the wireless keyboard and mouse work out of the box.

Finally, someone else who has experienced this problem!  I got my wife the studio hybrid Nov 2008 because it fits so well on her built-in desk.  Had to install Intrepid because Hardy would stop in the middle of install with a blank screen (probably related.)  I figured there was a video driver incompatibility in Hardy that was fixed in Intrepid.  But every second or third boot, my wife experiences the same problem you have.  Rebooting (sometimes twice) will result in a clean, complete boot.  I've been hoping whatever driver incompatibility is there (if that's the problem) will be fixed, eventually.  However, I'd sure like to solve the problem now.  Sure would appreciate any help!  TIA.

Sam

---

### Post by sirebral on 2009-03-06
Try  CTRL - ALT - F7.

I admit the bug is slightly problematic on mine, but mine works great.  If she wants cool desktop effects the I would suggest emerald and fusion-icon.

Also try CTRL - ALT - Backspace

---

### Post by robertj20112 on 2009-03-07
Thanks for the quick response.  I'll try your suggestion and let you know how it works.

---

### Post by robertj20112 on 2009-03-15
After five+ days of flawless booting (so I couldn't try the suggestion}, I finally got the boot hang today.  Unfortunately, neither suggestion corrected the problem.  On a whim, I tried typing in the userid, then password, as if the screens had appeared (in actuality, the monitor was blank).  While this seemed to have the desired effect of allowing the boot process to continue (judging from the resulting hard drive activity), the screen remained dark.  Strangely enough, when this happens and I press the power button on the PC to turn it off, the video returns with the shut-down screen (decreasing orange bar and the word Ubuntu), and the PC shuts off.  Rebooting produced a normal boot.  Still a mystery!  But thanks for the suggestion.

---

### Post by sirebral on 2009-03-15
That is so weird.  Every time that happens to me I just restart Xorg (CTRL - ALT -  Backspace) and the login screen reappears.  I have noticed the same blank screen that allows login.

---

### Post by JasonPN on 2009-04-05
I am running 8.10 on a Hybrid I picked up on clearance for a song at Staples... it runs like a charm... no screen blanking or anything, however, I cannot get it to run at a high resolution (1920x1200... on a Dell 24" flat panel)... max is 1360x768.  I AM using a converter to go from DVI to a standard d-shapped plug so I can use the second input in my monitor... can anyone give me direction on how I might get it up to the high resolution?  Otherwise... this is slick... and very damn fast...

---

