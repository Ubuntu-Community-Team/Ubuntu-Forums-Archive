---
title: "Burning an ISO to DVD in Ubuntu"
date: 2006-08-29
forum: Desktop Environments
---

### Post by mjpatey on 2006-08-29
Hi, all-

I have an ISO file that I'd like to burn to a DVD in Ubuntu.  I'm familiar with burning an ISO to DVD in Windows, but I don't see an obvious way to do it in Ubuntu... the usual "burning" dialogs don't seem to include this option.

Anybody know how to do this?

Thanks!

---

### Post by randell6564 on 2006-08-29
> **mjpatey said:**
> Hi, all-

I have an ISO file that I'd like to burn to a DVD in Ubuntu.  I'm familiar with burning an ISO to DVD in Windows, but I don't see an obvious way to do it in Ubuntu... the usual "burning" dialogs don't seem to include this option.

Anybody know how to do this?

Thanks!

HI!  Try 'Acidrip'.  You can find it in Synaptic Package Manager.

There is literally TONS of software for burning DVD's!

As long as you have DVD burning hardware, you're good to go My Friend!

---

### Post by superm1 on 2006-08-29
> **mjpatey said:**
> Hi, all-

I have an ISO file that I'd like to burn to a DVD in Ubuntu.  I'm familiar with burning an ISO to DVD in Windows, but I don't see an obvious way to do it in Ubuntu... the usual "burning" dialogs don't seem to include this option.

Anybody know how to do this?

Thanks!
Try right clicking on the ISO.  There should be a write to disk option.

---

### Post by randell6564 on 2006-08-29
[QUOTE=superm1;1435434]Try right clicking on the ISO.  There should be a write to disk option.[/QUOTE

Yeah, but not for DVD's.]

---

### Post by superm1 on 2006-08-29
> **randell6564 said:**
> [quote=superm1;1435434]Try right clicking on the ISO.  There should be a write to disk option.[/QUOTE

Yeah, but not for DVD's.]

I'm actually doing it right this minute.  Ripped the image from DVD shrink under Wine to an ISO.  Right clicked the ISO and hit write to disk.

---

### Post by mjpatey on 2006-08-29
Can't seem to find Acidrip in Synaptic... is it spelled differently, maybe?  I tried it as 2 words, as well... no dice.

---

### Post by mjpatey on 2006-08-29
Regarding the "write to disc" option, won't this just burn the ISO file to a disc as a file, as opposed to burning it as an image?  The context menu and dialog that come up really aren't clear...

---

### Post by randell6564 on 2006-08-29
> **mjpatey said:**
> Can't seem to find Acidrip in Synaptic... is it spelled differently, maybe?  I tried it as 2 words, as well... no dice.

Spelled, 'acidrip'.  you will probably need to enable 'multiverse' in your /etc/apt/sources.list to get it.

I just checked my package manager and it's there!

Also...why are you using 'Wine' to run DVD shrink?  Thats not necessary!

---

### Post by superm1 on 2006-08-29
> **randell6564 said:**
> Spelled, 'acidrip'.  you will probably need to enable 'multiverse' in your /etc/apt/sources.list to get it.

I just checked my package manager and it's there!

Also...why are you using 'Wine' to run DVD shrink?  Thats not necessary!

Using Wine w/ shrink because I had horrible luck with K9copy.  Couldn't get a build that would work to actually rip anything on my amd64 box.  When this improves, I'll be glad to switch, but at this point i'd prefer functionality :).

That option write to disk burns the ISO file as an image.  As in if you rip a movie, and burn the ISO image in this fashion - you have a DVD playable in standard DVD players.

---

### Post by liorwohl on 2006-08-29
> **mjpatey said:**
> Regarding the "write to disc" option, won't this just burn the ISO file to a disc as a file, as opposed to burning it as an image?  The context menu and dialog that come up really aren't clear...

the "write to disk" option will write the iso as an image and not as a file.

there is "write to disk" option only for iso files, because ubuntu knows what iso files is..

to superm1:
to copy a dvd to iso you don't need wine..
just right click on the DVD icon on the desktop and select the "copy disk" option. in the "copy disk" window that will appear just select "copy disk to: File image"

---

### Post by superm1 on 2006-08-29
The problem lies in when you are copying an encrypted DVD.  That method will work with anything that doesn't have CSS on it to my understanding.

---

### Post by ddales on 2006-08-29
Even though it's not intended for Gnome, I use K9Copy and K3B.

The only problems I've had so far is that K9Copy sometimes confuses the audio tracks when ripping DVDs.  It's only happened with 2 so far but very strange.

---

