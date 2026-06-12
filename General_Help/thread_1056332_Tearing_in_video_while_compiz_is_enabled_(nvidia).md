---
title: "Tearing in video while compiz is enabled (nvidia)"
date: 2009-01-31
forum: General Help
---

### Post by reesje on 2009-01-31
Hi guys,

Searching the forums surgest that this is a problem, however not an issue that has gotten a lot of attention. I hope the issue will get attention, because it is really anoying!

I have two PCs both with nvidia graphics adaptor. A desktop with a Geforce 8600GT and a laptop with a Geforce Go 7400.

On both machines I can see tearing, however it is _much_ more noticable on the laptop than on the desktop. I have tried with different drivers and some solutions I have found in various threads in ubuntuforums. Nothing helps other than turning compiz off (actually I believe it is the compositing rather than compiz itself that causes the problem, if I turn on compositing in metacity I see the same thing).

The fact that it is very clearly visible on the one PC and barely noticable on the other surgest to me that the problem exists on all PCs with nvidia and compiz, but many people does not notice it.

I hope this thread can put some focus on the issue - it is very annoying to have to switch off compiz everytime I want to watch a video. This I do alot, since my PC is actually also my VCR.

BR,
René

---

### Post by Gizenshya on 2009-01-31
the problem is that the video card refresh rate and monitor refresh rate are not matched, or 'synced.'

Go to your compiz settings manager, then general options, then display settings.

look for "Sync to VBlank" and check it.

and this also Syncs the video for everything else while Compiz is running (including video).

---

### Post by reesje on 2009-02-01
> **Gizenshya said:**
> Go to your compiz settings manager, then general options, then display settings.

look for "Sync to VBlank" and check it.
Been there done that. No change whatsoever. Video playback still tears.

Are there any foolproof guide as to how to remove this tearing? I cannot believe that I am the only one trying to fix it.

Another thing, what forum is best for this topic? I was very much in doubt, there seemed to be three obvious forums, Multimedia and Video, Hardware and Laptops, or Desktop Effects and Customization. So I put it under general :-)
BR,
René

---

### Post by fooman on 2009-02-01
here is how i fixed mine (not sure which is actually responsible for fixing the issue,  but these are all the things i tried):

in a terminal, run:

```
sudo nvidia-settings
```

in there,  go to "xserver xvideo settings" and put a check next to "sync to vblank".  close the nvidia-settings manager.

open compizconfig settings manager and clcik on general > general options.

under display settings, put a check next to "sync to vblank" (which you already did appearently) and set the refresh rate to the correct rate that you are using (mine is 60).  i also set the "outputs" to match my screen size (1680x1050).  the default output was "640x480+0+0"....by double clicking in that box,  it opens up an edit box.  in the edit box i typed: 1680x1050+0+0

close that box and close the compizconfig settings manager and see if there is any improvement.

hope that helps.

---

### Post by reesje on 2009-02-01
Thanks for the suggestions. Sadly it did nothing. I admit that the problem isn't that evident, but as soon as I am "locked" on it I can not see anything else. It is most obvious at slow panning left or right.

BR,
René

---

### Post by iconfat on 2009-02-06
> **Gizenshya said:**
> the problem is that the video card refresh rate and monitor refresh rate are not matched, or 'synced.'

Go to your compiz settings manager, then general options, then display settings.

look for "Sync to VBlank" and check it.

and this also Syncs the video for everything else while Compiz is running (including video).

Thanks, this fixed my issue.

iCON

---

### Post by reesje on 2009-02-11
> **reesje said:**
> 
On both machines I can see tearing, however it is _much_ more noticable on the laptop than on the desktop. I have tried with different drivers and some solutions I have found in various threads in ubuntuforums. Nothing helps other than turning compiz off (actually I believe it is the compositing rather than compiz itself that causes the problem, if I turn on compositing in metacity I see the same thing).

I would have to take some of this back. Actually I have no tearing on my desktop PC with a 8600GT. Only on the laptop with the Go7400. I am wondering why.
BR,
René

---

### Post by GriFF3n on 2009-02-11
> **Gizenshya said:**
> the problem is that the video card refresh rate and monitor refresh rate are not matched, or 'synced.'

Go to your compiz settings manager, then general options, then display settings.

look for "Sync to VBlank" and check it.

and this also Syncs the video for everything else while Compiz is running (including video).

Fixed my tearing. Thanks Gizenshya!

---

