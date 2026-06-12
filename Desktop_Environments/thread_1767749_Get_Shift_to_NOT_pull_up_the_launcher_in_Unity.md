---
title: "Get Shift to NOT pull up the launcher in Unity?"
date: 2011-05-26
forum: Desktop Environments
---

### Post by AliceKingsley on 2011-05-26
I use the shift key a lot. I don't want it to do anything extra. Is there a way to stop it from pulling up the launcher? I'm using Natty, and I like Unity in general, but this is driving me crazy. (Specifically, I'm going through my entire music collection and cleaning it up, and I capitalize song names correctly in the file names. The launcher opens an average of 3 times while editing each file name, and obscures the window I'm using.)

I've gone through the system settings and the CompizConfig settings, but I can't find anything that's mapped to just shift.

The super key is the only shortcut I need to the launcher, so I don't want to remap shift, just disable it. Does anyone know how to change this? Thanks.

---

### Post by coffeecat on 2011-05-26
The shift key has never opened the dash/launcher/whatever it's called in the several Natty installations I've made on 5 different machines. Are you sure you are not accidentally catching the super key with another finger when you press shift? Easily done when typing quickly. Since the super key did nothing by default in earlier Ubuntu releases (if I remember correctly) you would not have noticed this before.

**EDIT**: sorry that "dash/launcher/whatever it's called" comment is because of some confusion in terminology in the Unity plugin itself - or in me! The super key normally opens the dash, but can also reveal the launcher if you have that set to autohide in the Unity plugin in ccsm. Whatever, I don't think the shift key is doing anything.

---

### Post by AliceKingsley on 2011-05-27
I double-checked what's happening, and it is absolutely the shift key, but apparently only while I'm in nautilus. If my music folder is the active window, when I hold shift (it does take a moment) the launcher/dock/whatever slides out the same way it does when your mouse hovers at the side of the screen. (There aren't shortcut keys overlaid on the icons, so it's not the same as hitting the super key.) It happens regardless of where the mouse is, where the nautilus window is, and whether the window is maximized or not. 

Thanks for the reply, as I wouldn't have realized it was only that program otherwise. I certainly can rearrange my windows so that when that pops out it's not obscuring what I'm working on. I was just hoping I wouldn't have to, it seems silly.

EDIT: What I meant by launcher is the bar along the left side of my screen full of icons, and it auto-hides. (I'm not great on terminology. I've only been using linux for about 9 months, & most of that was Kubuntu. This is my 1st experience w/ 'regular' Ubuntu.)

---

### Post by wildmanne39 on 2011-05-27
> **AliceKingsley said:**
> I double-checked what's happening, and it is absolutely the shift key, but apparently only while I'm in nautilus. If my music folder is the active window, when I hold shift (it does take a moment) the launcher/dock/whatever slides out the same way it does when your mouse hovers at the side of the screen. (There aren't shortcut keys overlaid on the icons, so it's not the same as hitting the super key.) It happens regardless of where the mouse is, where the nautilus window is, and whether the window is maximized or not. 

Thanks for the reply, as I wouldn't have realized it was only that program otherwise. I certainly can rearrange my windows so that when that pops out it's not obscuring what I'm working on. I was just hoping I wouldn't have to, it seems silly.

EDIT: What I meant by launcher is the bar along the left side of my screen full of icons, and it auto-hides. (I'm not great on terminology. I've only been using linux for about 9 months, & most of that was Kubuntu. This is my 1st experience w/ 'regular' Ubuntu.)
Hi, your terminology is no worse then ours, I hope you enjoy ubuntu.

---

### Post by coffeecat on 2011-05-27
@AliceKingsley, when it comes to the terminology of the new Unity desktop, I think most of us are a bit lost! For instance, the launcher is exactly what you describe, but most people (I guess) would call it the dock and call the individual launcher items simply launchers. Here's a link for Unity terminology:

[http://askubuntu.com/questions/10228/whats-the-right-terminology-for-unitys-ui-elements/19166#19166](http://askubuntu.com/questions/10228/whats-the-right-terminology-for-unitys-ui-elements/19166#19166)

Anyway, to your shift key issue. That's interesting. I tried setting the launcher to autohide in ccsm and closing all applications except a lone Nautilus window, but I still couldn't get the shift key to reveal the launcher. Only the super key will do that on my system. It's perplexing. That's only on one system though. I'll try the others when I get a chance and let you know if I find anything.

One thing to try perhaps. Set the "Hide Launcher" function in the Unity Plugin in ccsm to dodge windows, and then push the launcher out of the way with a nautilus window. Does the launcher slide out when you press shift now? I realise this may not be the way you want to work, but it might be interesting to see what happens.

---

### Post by AliceKingsley on 2011-05-27
@coffeecat, that 'fixed' it. I'm still perplexed, I don't know why it was doing something that strange in the first place. But I'm satisfied w/ that as a result. Thanks! It makes fixing my music library about 50% as annoying. 
:guitar:
And I do really like Unity & Natty in general. [SIZE="1"](Now if only I can keep my graphics card under 90°C, I'll be all set...)[/SIZE]

---

### Post by coffeecat on 2011-05-27
> **AliceKingsley said:**
> [SIZE=1](Now if only I can keep my graphics card under 90°C, I'll be all set...)[/SIZE]

You could always boil a kettle on it to make yourself some tea/coffee to sustain yourself while fixing your music library. :)

Good luck!

---

### Post by Maverick_Fa on 2011-10-20
Hi there, 
I'm also experiencing this problem whereby I use the shift key and the menu keeps on appearing, quite annoying when I have to use the Shift key. Maybe try uninstall Unity? Then reinstall?

---

