---
title: "Hardy 64 bit. Compiz. Custom setting won't stick."
date: 2008-10-12
forum: Desktop Environments
---

### Post by Roasted on 2008-10-12
I installed simple-ccsm along with the advanced manager. When I go to sys-pref-appearance and select "custom" setting, it takes it. I exit out, go back in to check it, and it's back to "normal." 

Why?? 

Note - I have a 9600GT PCIex16 2.0 graphics card. There were no restricted drivers. I have manually installed a driver via EnvyNG.

---

### Post by Roasted on 2008-10-13
Do you guys think this could be 64 bit related? I'm tempted to put 32 bit in and give it a try... I'm also a little weery of envyng. I've never used it. Why in the world wouldn't I get a restricted driver for my 9600gt?

---

### Post by brianfreytag on 2008-10-13
[http://www.nvidia.com/object/linux_display_amd64_177.80.html](http://www.nvidia.com/object/linux_display_amd64_177.80.html)

I believe that this will support your graphics card.  You can't simply "install" it.  You'll have to "do it the Ubuntu way."  Search the forums or wiki for this documentation.

A slightly older version is in the repos and I'm sure you can find them.

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#NVidia_Driver](http://ubuntuguide.org/wiki/Ubuntu:Hardy#NVidia_Driver)

This is also a good source for that.

As for your Compiz not holding, it is not a 64-bit issue that I'm aware of.  I'm running it in Hardy 8.04 LTS 64-bit, and it works like a dream.

I would venture to guess that it's the fact that your graphics drivers are poor.  I would try to get those going with the restricted drivers and then test it out.

---

### Post by Roasted on 2008-10-13
brian - thanks for the response. I was actually on the nvidia site earlier, but I ended up not doing anything just yet till I got a response cause my graphics card, 9600GT, wasn't listed there. But seeing 9500 and 9700 and all that I was like, whaaaat... how different could it be. But I didn't want to assume.

I'm in windows land now, downloading my newly purchased CS-Source. :) I'll give it a shot in Ubuntu when I travel back over to home territory. :guitar:

---

### Post by brianfreytag on 2008-10-13
Those cards listed are the ones that that they recently added support for.

You should be good.

---

### Post by Roasted on 2008-10-13
Oh, so was the 9600GT already supported previously?

I'll give it a shot regardless... once I can pull myself away from CS: Source... :lolflag:

EDIT - how exactly do I go about installing this? I ran that sh command from the terminal, but it complained about a current x server already running.

---

### Post by Roasted on 2008-10-17
bump...

---

### Post by Dsmn on 2008-10-17
[LIST=1]
[*]Press alt+ctrl+F1.
[*]Login as root.
[*]Execute: killall gdm
[*]Execute sh <nvidia_file_name>.
[*]Follow the nvidia installer's instructions (Let the installer config X when prompted).
[*]Execute: gdm
[*]Press alt+ctrl+F7.
[/LIST]

That should do the trick.

---

### Post by Roasted on 2008-10-17
Didn't work.

This is getting really, really old. Considering how popular Nvidia is, let alone the 9600GT, I find it hard to believe that this thing would be this much of a pain in the rear to install.

Anybody have this card?
Anybody with it running 64 bit?
Compiz?

There has to be an easy solution to this...

---

### Post by Roasted on 2008-10-18
When I posted before saying it didn't work, I mean that installing the nvidia driver didn't work. I found that I was to do /etc/init.d/gdm stop instead of killall gdm.

So, I installed the driver. It yielded no different results. So I kicked Envy back into gear. Now, I don't know if there's a way to uninstall the nvidia driver I manually installed, but I just reinstalled Envy and installed the latest driver there.

But even still, it doesn't work. 

Basically, I have a 9600 GT with Envy and I can't get my custom setting to work with compiz. How can I fix it, before I go insane?

EDIT - Now I'm getting "desktop effects could not be enabled"

---

### Post by Roasted on 2008-10-19
Hi.
I'm about to lose it.
Anybody?

---

### Post by Roasted on 2008-10-23
I upgraded to 64 bit Intrepid 8.10 Beta. It's running really smooth and all. I installed 177 Nvidia drivers and installed simple ccsm + advanced ccsm. And even still, my setting reverts back to normal.

Come on, what did I miss? I can't iron this one out.

---

### Post by Roasted on 2008-10-29
Is there ANYBODY else out there having this issue?

Did I forget to install something?

If it's a problem with compiz itself, will it be fixed upon final release?

---

### Post by Roasted on 2008-10-30
I'm stupid.

Really, really stupid.

Turns out it reverted my settings back to normal because my custom settings were all default. Once I changed a default setting in the compiz manager, then selected custom, the custom option stuck. I guess with them being previously defaulted across the board, it just kicked them to normal.

Fixed. Duur.

EDIT - However, I do have a question. With custom effects enabled, I lose my ctrl w and ctrl t in firefox (which closes tabs as well as opens a new tab, I use these keys all the time). The thing is, when I hit ctrl t, it doesn't do anything... like compiz wise... it doesn't do anything for me to track down which setting it may be that's interfering. I dont' know, I just need my ctrl w and ctrl t back for firefox! I can't even copy text from an IM... I guess it's my ctrl key?

---

