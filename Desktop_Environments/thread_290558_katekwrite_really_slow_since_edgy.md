---
title: "kate/kwrite really slow since edgy?"
date: 2006-11-01
forum: Desktop Environments
---

### Post by sedd on 2006-11-01
Has anyone else notice that the katepart widget, used by kate, kwrite, kdevelop, kile... basically everything I use to work... is really slow since edgy? It's not __really__ slow, but it is noticeably sluggish, mostly when redrawing the window. It's choppy when scrolling, and if you drag another window over the katepart window, it leaves trails? Also, check the cpu when doing this. Its way high. I have a pretty fast machine, so I imagine its much worse for someone else.  Anybody notice this?

---

### Post by kerry_s on 2006-11-01
Try kedit it's much faster.

---

### Post by kkinder on 2006-11-01
It's probably that your X server is not configured right anymore and your video card isn't being taken advantage of. First try re-configuring X:

sudo dpkg-reconfigure xserver-xorg

If that doesn't work, and it didn't for me, you'll have to go further. For me -- and I'm not sure why -- having dpkg re-install X worked. Before I go on, it's best that you not re-install X while actually using X. You have seven "virtual consoles" on your computer. You can type ctrl+alt+f1 to go to the first one. Press ctrl+alt+f7 to go back to the one containing X. Backup any important data you have, even though this shouldn't be too bad and switch to the 1st console.

I ran these commands to get my X config back to normal:

sudo apt-get remove xserver-xorg-core
sudo apt-get install kubuntu-desktop
sudo dpkg-reconfigure xserver

Note that this is a lot of removing and uninstalling, so if you want to try to get it working without doing that, it might be better.

---

### Post by sedd on 2006-11-01
kkinder, I tried your suggestion (dpk-reconfigure, not a full reinstall.) and it didn't help.  My xorg setup is otherwise perfectly fine. Everything runs quick, and acceleration is working (opengl, beryl, you name it.)  

I tried a few other kde apps. Konsole seems a little slow when scrolling, but kedit is perfectly snappy. Is this just me? Anybody else notice this?

---

### Post by kkinder on 2006-11-01
That is curious. kate is usually extremely fast for me.

You could rule out your own personal configuration by creating a new user, logging in as that user, and trying kate. If it's faster then, you know it's something about your own config.

I'm a bit lost, and although I'm still suspicious about your video acceleration, I'm not knowledgeable enough to come up with a good test for that.

---

### Post by sedd on 2006-11-02
Good thinkin'.  I made a new user and everything was fine. It had something to do with the anti-alias settings. I just fidgeted with it a bit in kcontrol (probably only needed to overwrite the old settings.) and now its fine.

I had some weird dappter-to-edgy-upgrade issues with gtk anti-aliasing too. Lots of people did. This must be related.

Oh well, its fixed now. Thanks.

---

