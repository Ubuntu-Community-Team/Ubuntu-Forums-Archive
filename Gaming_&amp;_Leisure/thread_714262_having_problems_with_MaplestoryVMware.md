---
title: "having problems with Maplestory/VMware"
date: 2008-03-03
forum: Gaming &amp; Leisure
---

### Post by Sauceror on 2008-03-03
> **rafaelpriego said:**
> Hi, i did everything according to this tutorial, and in the end, when i Hit the green button to fire up the virtual machine, it shows the following error message: 

```
Failed to construct 3-D rendering backend.  The 3-D features of the display card will be disabled.
```

I had all the requisites, and my video card is working and direct rendering is activated and all...

Got any ideas?

This was posted on the [maplestory topic]("http://ubuntuforums.org/showthread.php?t=372928") on the Wine board, I guess that doesn't make much sense since it was a VMware topic. anyways, I'm getting the same error as him, though it reads OpenGL somewhere in the error dialog. I did everything listed on the tutorial there, but adding the three lines to the .vmx file makes this error appear, and then I can't play Maplestory (the virtual machine doesn't boot).
when I try running maplestory on VMware (workstation), it just says "DLL class not found". is this the error that appears when Direct3D isn't enabled?
if it makes a big difference, the virtual machine I have was originally made for VMware player, not VMware workstation. I dunno if they have differences between them, but, yeah.

also, i'm trying to play maplestory on a private server, which means it doesn't have gameguard, so it should run on Wine, but it hangs after the Wizet logo...

---

### Post by Sauceror on 2008-03-06
bump? :(

---

### Post by alexforcefive on 2008-03-07
[QUOTE=http://communities.vmware.com/thread/43465]It simply doesn't work. The 3d acceleration requires pbuffer support which the open-source drivers don't provide - only the Nvidia and Ati drivers have it right now. There is on going to work to implement pbuffer and fbo support for Mesa/DRI but it's going to be a while before you see that in action. Sorry I can't provide better news.[/QUOTE]

Are you using the open source drivers? 

You're lucky anyway, trying to enable d3d for vmware just makes my x server restart :p

---

### Post by Sauceror on 2008-03-07
> **alexforcefive said:**
> Are you using the open source drivers? 

You're lucky anyway, trying to enable d3d for vmware just makes my x server restart :p

I tried installing a flgrx driver but the guide I was using didn't work for Gutsy Gibbons, so I guess I'm stuck. also, I guess I forgot to mention I'm on a Radeon 9200 :(

---

### Post by alexforcefive on 2008-03-07
What doesn't work? I am faaaaaar from being an expert, but I managed to get my x1950 working a few days ago (after many google searches)

---

### Post by Sauceror on 2008-03-07
everything 3D on native linux works fine, but when I try to enable 3D acceleration on VMware it gives the error mentioned in the quote.

---

