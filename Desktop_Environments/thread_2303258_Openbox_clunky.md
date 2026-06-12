---
title: "Openbox clunky"
date: 2015-11-17
forum: Desktop Environments
---

### Post by steve234 on 2015-11-17
Hi there,

I've tried Openbox because I want faster (LXDE with openbox as WM is pretty fast, but wanted to go super-minimal) 

I'm using a wallpaper setter (nitrogen), launcher (kupfer), panel (fbpanel) and browser (Midori).

Midori is slow and super-clunky compared with using the Lubuntu LXDE desktop environment, so are things like the file manager (PCmanfm).

Surely it shoud be a smaller footprint and therefore faster no? Is it the composite manager doing something weird?

I've looked on goodle and found many theming guides for OB, but no "speed" guides - am I missing something?

Steve

---

### Post by buzzingrobot on 2015-11-17
Openbox is LXDE's window manager -- creates and controls windows on screen -- so using only Openbox may not produce an obvious speed increase.

A smaller footprint does not necessarily mean faster. A browser could, for example, cache everything on disk rather than RAM.  It's memory footprint would shrink, but performance would suffer.

---

### Post by vasa1 on 2015-11-17
> **steve234 said:**
> ... Is it the composite manager doing something weird?
...
Which compositor have you installed? There's none by default.

---

### Post by steve234 on 2015-11-17
I have this line pre-installed in my autostart file:

```
  # Run a Composite managerxcompmgr -c -t-5 -l-5 -r4.2 -o.55 &

```

If I try to load it it says "not installed" so I guess that's a red herring.

---

### Post by steve234 on 2015-11-17
saying that - tint2 is transparent - so something must be doing it?

---

### Post by vasa1 on 2015-11-17
> **steve234 said:**
> I have this line pre-installed in my autostart file:

```
  # Run a Composite managerxcompmgr -c -t-5 -l-5 -r4.2 -o.55 &

```

If I try to load it it says "not installed" so I guess that's a red herring.

What exactly is your set-up? I was surprised by your finding Openbox "clunky" but what your system is and what you started off with  isn't clear, at least to me. An example is the code in your autostart. How did that get there? The compositor mentioned there is quite old and no DE that I know of uses it currently by default.

---

### Post by vasa1 on 2015-11-17
> **buzzingrobot said:**
> Openbox is LXDE's window manager -- creates and controls windows on screen -- so using only Openbox may not produce an obvious speed increase.

A smaller footprint does not necessarily mean faster. A browser could, for example, cache everything on disk rather than RAM.  It's memory footprint would shrink, but performance would suffer.
Well, it maybe possible to see some benefit on machines strapped for resources. Isn't it possible that if the "system" uses fewer resources, correspondingly more resources are available for applications?

OP has issues that I haven't noticed or read about elsewhere since I started using Openbox (~ Sep 2013). It seems it's not just Op's browser that runs better on a DE+WM combination but also the file manager.

Elsewhere, the OP mentioned the presence of a line in "autostart" that I haven't seen before. So it's possible that some changes to the user's set-up are responsible for the poor performance and it may need some head-scratching to get things back to "normal".

---

### Post by vasa1 on 2015-11-17
> **steve234 said:**
> saying that - tint2 is transparent - so something must be doing it?
Not necessary that that something is a compositing manager.

Some applications offer "fake" transparency. LXTerminal is an example.

---

### Post by steve234 on 2015-11-19
Hi there,

I am using the Openbox login option of Lubuntu - the compositor is not installed but was present in the stock autostart file.

I'm on a fairly low horsepower netbook - Atom processor with 1gb ram - still finding it clunky especially in browsers (FF and Chromium) It's better with Midori, but Midori doesn't do flash.

I guess there is something in the LXDE setup that optimises everything better - some kind of ram / processor management perhaps?

---

### Post by vasa1 on 2015-11-19
> **steve234 said:**
> Hi there,

I am using the Openbox login option of Lubuntu - the compositor is not installed but was present in the stock autostart file.
...
I guess there is something in the LXDE setup that optimises everything better - some kind of ram / processor management perhaps?
There was mention of zRAM. I don't know much about that. It's quite possible that zRAM isn't involved in an Openbox session.
Here's a link to a mailing list post: [https://lists.ubuntu.com/archives/lubuntu-users/2013-October/005831.html](https://lists.ubuntu.com/archives/lubuntu-users/2013-October/005831.html)

Can you post the contents _and_ path of this autostart file?

---

### Post by steve234 on 2015-11-20
The Zram post is an interesting read I've changed my swappiness to 60 - I can confirm that zram is working (2 zram partitions shown) in Openbox.

Config file has been edited by me but is living at:

```
  ~/.config/openbox/autostart 
```
and contains

```

# Programs that will run after Openbox has started

#panels below
tint2 &




#launcher
kupfer &




# Set the wallpaper with feh
sh ~/.fehbg &


# Run a Composite manager
xcompmgr -c -t-5 -l-5 -r4.2 -o.55 &


# SCIM support (for typing non-english characters)
scim -d &



```


I note there are other things starting (Dropbox client, nm-applet etc) in my system tray - are these listed in some separare user-config file that applies to all desktop environments? as I don't need a few of them (bluetooth manager for one).

---

