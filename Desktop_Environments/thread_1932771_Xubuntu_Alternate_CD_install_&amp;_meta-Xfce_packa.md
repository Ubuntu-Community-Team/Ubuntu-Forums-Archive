---
title: "Xubuntu Alternate CD install &amp; meta-Xfce package: How to decide which packages?"
date: 2012-02-28
forum: Desktop Environments
---

### Post by mikodo on 2012-02-28
When installing Xubuntu, using the Alternate CD Install, with the[ Meta-package for the Xfce Lightweight Desktop Environmen]("http://packages.ubuntu.com/oneiric/xfce4")t, does the installer ask, which of the depends, recommended and suggests, one wishes to install? 

If so, I have a lot of reading, to figure out which ones, I will want, to install!

Thanks.

---

### Post by Krytarik on 2012-02-28
> **mikodo said:**
> When installing Xubuntu, using the Alternate CD Install ...
Step 1 - from the CD; no selection of packages possible.

> **mikodo said:**
> ... with the[ Meta-package for the Xfce Lightweight Desktop Environmen]("http://packages.ubuntu.com/oneiric/xfce4")t, does the installer ask, which of the depends, recommended and suggests, one wishes to install?
Step 2 - from the CLI of the already (half) installed system; "apt-get" will automatically install 'recommends', but not 'suggests' - by default; this can be tweaked:

[http://manpages.ubuntu.com/manpages/oneiric/en/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/oneiric/en/man8/apt-get.8.html)

Regards.

---

### Post by mikodo on 2012-02-28
Hi Krytarik, 

Thanks for responding again. So, I will have to read through which of the suggests, I might want, and then tweak, as you say.

Like:  
 ```
--install-suggests   
```etc....

I have been taught to use aptitude and not apt-get, but will not use aptitude, after reading your next post, for the install.

I need to go to bed in Canada now, so I will read more about your directions later, and apt-get!

Thanks.

---

### Post by mikodo on 2012-02-28
I forget how to report spam, like that previous post...

Oh, I think I found it and requested it to be deleted.

---

### Post by Krytarik on 2012-02-28
> **mikodo said:**
> So, I will have to read through which of the suggests, I might want, and then tweak, as you say.
I definitely wouldn't apply the "--install-suggests" option, as that would install *all* 'suggests' of *all *'dependencies', 'recommends', and 'suggests'! You would end up with the very thing you are trying to avoid: a system mixed out of XFCE and Gnome packages, plus many many more that aren't even installed by a regular Ubuntu or Xubuntu CD!

> **mikodo said:**
> I have been taught to use aptitude. Is that OK too?
I, myself, wouldn't use "aptitude", as I don't have any experience with it, and it seems like it isn't really needed anymore, for intelligently solving dependency conflicts; "apt-get" does that well enough, it seems.

Addition: Oh, I see you've decided to go with "apt-get" now, better that is. :P

---

### Post by mikodo on 2012-02-28
> **Krytarik said:**
> I definitely wouldn't apply the "--install-suggests" option, as that would install *all* 'suggests' of *all *'dependencies', 'recommends', and 'suggests'! You would end up with the very thing you are trying to avoid: a system mixed out of XFCE and Gnome packages, plus many many more that aren't even installed by a regular Ubuntu or Xubuntu CD!


I, myself, wouldn't use "aptitude", as I don't have any experience with it, and it seems like it isn't really needed anymore, for intelligently solving dependency conflicts; "apt-get" does that well enough, it seems.OK, with the apt-get

I will do as you say, and stay away from the "universal --install-suggests", as you are right...

I do not want it all; but a more "vanilla install", without Gnome packages.

I will read up more closely, on the following, later:

  [http://manpages.ubuntu.com/manpages/...apt-get.8.html]("http://manpages.ubuntu.com/manpages/oneiric/en/man8/apt-get.8.html")

:>)

---

### Post by Dr Watts On on 2012-02-28
Hello! Just found this post, will be acting upon the data here. This makes me feel much more confident about what to expect. I just posted more questions to that Unity appearing on desktop thread.
Does GTK mean Gnome Tool Kit?? If so, then I take it vanilla + Xfce means no Gnome progs will run. I am hoping that's ok for this laptop that's supposed to be a tool for a 17yr old kid to use for school? He should be getting it back next weekend when my neighbor visits him (I don't know him and don't expect further involvements).
Will subscribe to stay alert to this thread till I get stuff rolling.
You folks have been great.
DrWattsOn

---

### Post by snowpine on 2012-02-28
GTK is not really a "Gnome package" and nothing to be scared of. If you are in doubt just install **xubuntu-desktop** and you will have a fully functional Xfce system. :)

---

### Post by Dr Watts On on 2012-02-28
if ur still watching: could you post resp also to my latest (other questions) in the thread on "Unity appeared suddenly" thread? If not, still need confirmed: what the GTK letters stand for, and what the X in Xubuntu stands for (that's why I
'm asking you to ref my ??? in the other thread. Also re the diff btwn XFCE and Xubuntu Logons offered by stock Xubuntu install / live cd
DrWattsOn

---

### Post by snowpine on 2012-02-28
> **Dr Watts On said:**
> if ur still watching: could you post resp also to my latest (other questions) in the thread on "Unity appeared suddenly" thread? If not, still need confirmed: what the GTK letters stand for, and what the X in Xubuntu stands for (that's why I
'm asking you to ref my ??? in the other thread.
DrWattsOn

GTK = GIMP Took Kit
X in Xubuntu = Xfce

The wikipedia pages on each of these projects will give you more info. :)

---

