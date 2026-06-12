---
title: "[Ubuntu 23.10 / Wayland] Disabling/customizing display scaling on a per-app basis?"
date: 2023-11-06
forum: Desktop Environments
---

### Post by andi-mcc on 2023-11-06
I have recently installed 23.10 with whatever the default DE is (I think this is mutter/Gnome). I run with Wayland.

Because of the DPI of my laptop screen, for things to look good I need to run at about 150% scale. In Settings, I have ["Fractional Scaling" turned on and "Scale" set to 150%](https://files.mastodon.social/media_attachments/files/111/365/911/886/773/784/original/b320d4ffc38fa3c9.png). (I notice there is also a "Fonts->Scaling Factor" setting in gnome-tweaks but I have not touched it.) This works great in most applications, but is catastrophically bad— displaying blurry, such that text is not readable— in a few, either because the application does not support scaling or it supports scaling but only at "integer" multiples.

My understanding is if an app does not support fractional scaling it must be rewritten to support it and so there is no easy fix for the blur. Therefore, I wish to simply turn off the scaling (or increase it to 200%, which may produce better results) for some of my scaling-not-supported apps. My questions:

* Whatever the "Scaling:" box in Settings is doing— how can I disable it, or set it to a different value, for just one application? (Assume for starters I'm just trying to do this from the command line.)

* In general, what exactly is the "Scaling:" box *doing?* (That is, what value is it setting and with what system component?)

* A separate but related question: According to [Arch Wiki]("https://wiki.archlinux.org/title/HiDPI"), the "text scaling" option in gnome-tweaks is setting `gsettings set org.gnome.desktop.interface text-scaling-factor`. Is there a way to run one application with different gsettings values from the other processes in the same Ubuntu login session? If I could do this, would this allow me to run different applications "as if" the gnome text-scaling-factor were different?

Note my worst offender (IE the app I am most interested in disabling scaling for) is a closed-source IDE that runs in xwayland, so if I get a solution that works but only for xwayland apps, this helps significantly.

I am desperate enough I am willing to consider "absurd" situations like running a second, subsidiary Wayland or second xwayland. However I would prefer not to have to switch to a different desktop environment just to get this one feature.

---

### Post by norvel4 on 2023-12-24
[https://zzzcode.ai/answer-question?id=1d50a996-a162-4af5-a993-1ba50793a9a8](https://zzzcode.ai/answer-question?id=1d50a996-a162-4af5-a993-1ba50793a9a8)
Stuff like this: "QT_SCALE_FACTOR=2 example_app" might work and that question and answer thing may be able to help you more.
Regarding the "text scaling" option in gnome-tweaks, it sets the org.gnome.desktop.interface text-scaling-factor value using the gsettings command. Unfortunately, there is no direct way to run one application with different gsettings values from other processes in the same Ubuntu login session. Keep in mind that these solutions may not work for applications running in xwayland, as they may have their own scaling mechanisms.


I am just using AI here and do not know much about this but hope this helps. All as per one might be maybe or might not be maybe, maybe or maybe not, maybe.

---

