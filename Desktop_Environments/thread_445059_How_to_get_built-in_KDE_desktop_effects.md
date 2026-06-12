---
title: "How to get built-in KDE desktop effects?"
date: 2007-05-15
forum: Desktop Environments
---

### Post by Happy_Man on 2007-05-15
So I'm running Kubuntu Feisty, and I see the "desktop effects." Oh great! Fun without Beryl! Great...why won't it work? Is it my drivers? Me on GeForce MX 420 (ok, stop laughing now.). Do I need to install the new drivers? If so, how do I do that on Kubuntu? Any help is greatly appreciated.

---

### Post by Rashid584 on 2007-05-15
> **Happy_Man said:**
> So I'm running Kubuntu Feisty, and I see the "desktop effects." Oh great! Fun without Beryl! Great...why won't it work? Is it my drivers? Me on GeForce MX 420 (ok, stop laughing now.). Do I need to install the new drivers? If so, how do I do that on Kubuntu? Any help is greatly appreciated.

As far as I know, the "desktop effects" feature I think you're talking about only exists on Ubuntu not Kubuntu...but imho its pretty crap I dunno why you'd use it.

You have to install nvidia-legacy drivers for 3D to work...follow the guide [here](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) closely for drivers.

Do you NOT want to use beryl? If so, may I ask why? If beryl is not gonna work on your computer, than I assume compiz ("desktop effects") will give you the same problems.

Personally I prefer beryl because for some (unknown) reasons it feels lighter, faster, and slicker. I also prefer their attitude although I hope the upcoming merge of the projects is beneficial.

-Rashid

---

### Post by Happy_Man on 2007-05-15
No, dude, I'm on Kubuntu, and they give you desktop effects w/o beryl as part of the DE. I have nothing against beryl, it's just that i don't feel like installing it today.

---

### Post by hardyn on 2007-05-15
you will have to install the binary nvidia drivers.

you may need to use the nvidia-legacy package, as i believe that the MX-4xx have been depreciated from the nvidia-glx and glx-new packages.

---

### Post by Rashid584 on 2007-05-16
> **Happy_Man said:**
> No, dude, I'm on Kubuntu, and they give you desktop effects w/o beryl as part of the DE. I have nothing against beryl, it's just that i don't feel like installing it today.

As far as I know people are working on cool new effects for Kwin, but it hasn't been released yet in any way for KDE. Some effects exist such as the click feedback I think maybe...but I don't think thats what you're talking about.

What kind of features are you talking about/do you think KDE provides built in?

-Rashid

---

### Post by Happy_Man on 2007-05-16
The translucency stuff... and I did install the nvidia-legacy drivers, and the thing made my desktop so dang slow I turned them off immediately. Thanks for all the help though!

---

### Post by Rashid584 on 2007-05-17
> **Happy_Man said:**
> The translucency stuff... and I did install the nvidia-legacy drivers, and the thing made my desktop so dang slow I turned them off immediately. Thanks for all the help though!

You mean the fake transparency KDE has had for ages? If so I'm not aware that you really need any 3d drivers...the normal nv drivers should work fine?

Just enable them in Kcontrol under style....if thats what you're talking about.

-Rashid

---

### Post by jamboarder on 2007-05-18
> **Rashid584 said:**
> You mean the fake transparency KDE has had for ages? If so I'm not aware that you really need any 3d drivers...the normal nv drivers should work fine?

Just enable them in Kcontrol under style....if thats what you're talking about.

-Rashid

What you've mentioned above is *menu* drop-shadow and translucency effects. KDE's kwin window manager has had *real* window composition features built-in for a while now.  It's just basic composition like translucency and drop shadows which may be all some people are interested in.  This not the berylled-out wobbly windows with rain, snow and fire effects (which I kinda like too).  It is under Window Behaviour control module, the Translucency tab.  Your graphics card must have 3D acceleration working in Xorg otherwise it'll be dog slow.  Better to check if 3D accelleration is working first (try glxgears -printfps as a test and search the forums for help) before turning on the KDE composite effects.  On some distros you may also have to add
```
Section "Extensions"
Option "Composite" Enable
End Section
``` to your xorg.conf.

good luck

---

### Post by bunker on 2007-05-18
Just as an addition to the note above: kwin's composite features (Desktop-> Window Behavior-> Translucency) conflict with the 'fake' translucency and shadows (Appearance and Themes ->, Style -> Effects) so make sure you disable whichever you are not using or things will look rather strange.  It took me a bit of head-scratching to work out what the hell was going on when I accidentally turned them both on.

Also, for me the whole composite stuff in kwin made the desktop slow and buggy, which I suppose I should have expected given the dire warning dialog that you get when you turn translucency on in the first place.

---

### Post by Rashid584 on 2007-05-19
Hmm I didn't know kwin had real translucency built on...thats cool.

The newer features being added in (search kwin on youtube) are very cool (scale, magnify, zoom, fade, wall etc)

-Rashid

---

