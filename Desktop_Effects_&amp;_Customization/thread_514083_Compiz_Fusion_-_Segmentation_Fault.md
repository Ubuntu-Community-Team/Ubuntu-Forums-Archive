---
title: "Compiz Fusion - Segmentation Fault?"
date: 2007-07-31
forum: Desktop Effects &amp; Customization
---

### Post by kieranjones on 2007-07-31
Hello,

I am a new convert to Ubuntu from openSuSE and would really like some help with an issue I'm having with Compiz Fusion.

I followed the following instructions to install the relavant packages and what not, [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/) and everything happened without a glitch. However, when actually issuing the command "compiz --replace" the windows all flicker but nothing happens.

I ran the command from a terminal and got the following error:

/usr/bin/compiz: line 777:  5857 Segmentation fault      (core dumped) $*

Any ideas?

Sorry if this has been asked before, I don't mean to duplicate. I googled it but didn't find anything overly useful.

I look forward t o getting it all pretty-fied :)

---

### Post by kieranjones on 2007-07-31
I have discovered what is potentially the cause of the problem, well... I'm certain it is the cause.

I neglected to mention in my previous post that I am running a dual monitor setup with Xinerama enabled. This it seems is the cause of the problem.

If I disable Xinerama and use TwinView instead it works perfectly fine, the problem here though is that I really don't like TwinView, I hate how Windows appear between two screens, and how when you maximise they go all over both.

But yes, the problem is solved kind of, at least in regard to the segmentation fault.

---

### Post by kieranjones on 2007-08-06
I was hoping that someone really smart would reply to my post and shed some light on my little problem and how to solve my dual screen with xinerama setup.

Tell me, someone... does Compiz Fusion work with two X screens with Xinerama enabled? If not, is it going too?

I've been searching around Google and various forums for ages and so far have found nothing much useful out, I mean I've read lots but learnt nothing, in fact the more I read the less I seem to know! :S

Some help would be great, thanks.

---

### Post by CompShrink on 2007-08-15
Yes, i can confirm Compiz Fusion does work on nvidia with dual monitor using xinerama.

I have that set up at work on my dual screens, but unfortunately my home dualscreens are getting a segmentation fault on line 777 like you are. If i find a fix, I'll let you know.

---

### Post by matemargo on 2007-08-21
I'm having exactly the same problem (and I don't have dual monitor). Just a standard Nvidia card.

---

### Post by Unstuck on 2007-08-28
Same problem here...running single monitor with nVidia card.
```

@desktop:~$ compiz --replace
/usr/bin/compiz: line 777:  7570 Segmentation fault      (core dumped) $*
Window manager warning: "" found in configuration database is not a valid value                  for keybinding "toggle_shaded"
```

---

