---
title: "Desktop.. Frozen!??"
date: 2009-04-02
forum: General Help
---

### Post by Ecstatic23 on 2009-04-02
Ok, I'm being forced to use my Windows XP computer to type this,

Well I think it started last night, Everything was running fine except 'appearances' where I was changing my Desktop wallpaper, every time I clicked something in the appearances thing, it took about 5 minutes to load that (including launching appearances).

Now just as I booted my computer, I found that the whole desktop is more or less frozen, if I opened firefox, it would highlight firefox, but it wouldn't launch it. After attempting to launch firefox it wouldn't let me do anything else. So I just had a frozen desktop. I restarted my computer and tried to rotate the desktop cube, it did so and kept letting me do so but it didn't let me do anything else.

Just now, about 10 minutes after trying to launch firefox, it launched, but I didn't have my wireless switched on, I turned off my computer and enabled it, then tried to open firefox again.. same problem.. What's happening!?

Please help.

Edit: Firefox just launched again and it immediately turned black and white, which means it's frozen right? It'll let me wobble the window, but it won't let me use the application menus to try and see if there's something hogging my cpu.

this really sucks =/

---

### Post by Ecstatic23 on 2009-04-02
bump...

---

### Post by Ecstatic23 on 2009-04-02
Can't anyone help me out?
This is so bad...

---

### Post by vishant65 on 2009-04-02
hi man,
i am not a linux guru, but been to linux road for some time. 
in your case what i can think of is, try unistalling compiz or any visual enhancement packages, by the way what hardware configurations u have?

---

### Post by Ecstatic23 on 2009-04-02
> **vishant65 said:**
> hi man,
i am not a linux guru, but been to linux road for some time. 
in your case what i can think of is, try unistalling compiz or any visual enhancement packages, by the way what hardware configurations u have?

eee PC 701 4G
512mb RAM (Although I just bought 2GB RAM which I should receive in a few days).

Compiz has been running fine while I've had it, I'll try uninstalling it as soon as I can get the terminal to load :mad:

---

### Post by vishant65 on 2009-04-02
can try installing ubuntu desktop again by

sudo apt-get install ubuntu-desktop


like i said earlier, i m not a linux guru. We need more senior members to have a say in this.

---

### Post by Ecstatic23 on 2009-04-02
> **vishant65 said:**
> can try installing ubuntu desktop again by

sudo apt-get install ubuntu-desktop


like i said earlier, i m not a linux guru. We need more senior members to have a say in this.

If I want to remove compiz from the terminal, what do I type?
I tried sudo apt-get remove compiz but that does nothing.

Edit:
Removed it and nothing's changed..

---

### Post by vishant65 on 2009-04-02
u might want to check this out

[http://ubuntuforums.org/showthread.php?t=533201](http://ubuntuforums.org/showthread.php?t=533201)

---

### Post by mb_webguy on 2009-04-02
Try disabling desktop effects first, before you go uninstalling things.  Go to System->Preferences->Appearance, the Visual Effects tab, and click the radio button next to None.  This will disable Compiz.

I'd be willing to bet this is a video card issue, which may or may not also involve the (relatively) low memory currently on your system.  Netbooks are popular because of their price and portability, and not for their power.  The integrated Intel GMA 900 in your netbook, like most netbook video cards, is not terribly powerful.  It certainly gets the job done as far as playing videos and such, but you'd have a hard time playing any games with 3D graphics on it.  Compiz can demand a lot from a video card, and some cards struggle to keep up.  

This is especially true for cards such as yours that don't have their own memory cache and have to use the system memory.  Since your video card *does* use system memory, you may very well see an improvement in your video card's performance after you upgrade your memory, but you'll never be able to run the fancy Compiz desktop effects as smoothly with your video card as someone with even a mid-range nVidia or ATI card.

---

### Post by Ecstatic23 on 2009-04-02
> **mb_webguy said:**
> Try disabling desktop effects first, before you go uninstalling things.  Go to System->Preferences->Appearance, the Visual Effects tab, and click the radio button next to None.  This will disable Compiz.

I'd be willing to bet this is a video card issue, which may or may not also involve the (relatively) low memory currently on your system.  Netbooks are popular because of their price and portability, and not for their power.  The integrated Intel GMA 900 in your netbook, like most netbook video cards, is not terribly powerful.  It certainly gets the job done as far as playing videos and such, but you'd have a hard time playing any games with 3D graphics on it.  Compiz can demand a lot from a video card, and some cards struggle to keep up.  

This is especially true for cards such as yours that don't have their own memory cache and have to use the system memory.  Since your video card *does* use system memory, you may very well see an improvement in your video card's performance after you upgrade your memory, but you'll never be able to run the fancy Compiz desktop effects as smoothly with your video card as someone with even a mid-range nVidia or ATI card.

I'll give that a shot.
I have no idea how to upgrade a video card. Can you?
I would if I could but..
Compiz has been working beautifully, infact, it still is. It's the only thing that works properly.

..still waiting for the systems menu to load... this is so sad. I never thought I'd have troubles like this on a non-Windows OS.

---

### Post by Ecstatic23 on 2009-04-02
It doesn't work. Setting it to none does absolutely nothing except get rid of every single effect.

---

### Post by mb_webguy on 2009-04-02
> **Ecstatic23 said:**
> I'll give that a shot.
I have no idea how to upgrade a video card. Can you?
I would if I could but..
Compiz has been working beautifully, infact, it still is. It's the only thing that works properly.

..still waiting for the systems menu to load... this is so sad. I never thought I'd have troubles like this on a non-Windows OS.

Unfortunately, since you're using a netbook and it has an integrated video card, you're pretty much stuck with the one you have.

However, after a bit of thought, it does seem rather odd that the *only* thing you seem to be able to do is play with the Compiz effects.  I was thinking that the Compiz effects were hogging your memory and causing the programs to slow or hang, but maybe there's something else going on.

The next time you reboot the computer, open a terminal first off, and type "top".  This will give you a list of current processes and resource usage.  Keep an eye on your resource usage as you use your computer, especially when things start locking up.  If your resource usage spikes, try to figure out which process is causing the problem.

---

### Post by Ecstatic23 on 2009-04-03
> **mb_webguy said:**
> Unfortunately, since you're using a netbook and it has an integrated video card, you're pretty much stuck with the one you have.

However, after a bit of thought, it does seem rather odd that the *only* thing you seem to be able to do is play with the Compiz effects.  I was thinking that the Compiz effects were hogging your memory and causing the programs to slow or hang, but maybe there's something else going on.

The next time you reboot the computer, open a terminal first off, and type "top".  This will give you a list of current processes and resource usage.  Keep an eye on your resource usage as you use your computer, especially when things start locking up.  If your resource usage spikes, try to figure out which process is causing the problem.

I don't really understand anything that shows up.
Nothing really stands out though there was 2 things at about 1500RS but i don't get it..

---

