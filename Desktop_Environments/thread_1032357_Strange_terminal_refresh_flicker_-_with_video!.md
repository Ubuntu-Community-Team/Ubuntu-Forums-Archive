---
title: "Strange terminal refresh flicker - with video!"
date: 2009-01-06
forum: Desktop Environments
---

### Post by tomstrummer on 2009-01-06
The easiest way to describe this problem is to watch this video:
[http://video.google.com/videoplay?docid=-3493635213808586898](http://video.google.com/videoplay?docid=-3493635213808586898)

Basically if the gnome-terminal is scrolling and I switch to Eclipse (I think it actually happens whenever the terminal is out of focus) it will start to flicker -- the background disappears and text becomes all garbled.  If I return focus to the terminal window and refresh it, it clears up again.  It also has something to do w/ the size of the terminal window -- if the window is smaller than, say 1/4 of the screen it doesn't seem to happen.

Environment:
[LIST]
[*]Ubuntu Intrepid (I think it happened in Hardy too), kernel 2.6.27-9
[*]AMD x64 workstation w/ Nvidia Quadro FX 1500 GPU
[*]NV binary drivers v177.80
[*]Dual display
[/LIST]

I don't think this is a Compiz problem; it occurs even if Compiz is disabled.  

I have searched everywhere for this behavior with no results...  Any ideas??  If anyone else can even *confirm* that they've seen this behaivor, I'd be thrilled.  Thanks.

---

### Post by tomstrummer on 2009-01-07
Follow up -- here are two screenshots of what it looks like when it 'flickers' - 

[ATTACH]99063[/ATTACH]

[ATTACH]99064[/ATTACH]

---

### Post by Bucky Ball on 2009-01-07
Tried a different driver? nvidia-glx-new?

---

### Post by tomstrummer on 2009-01-09
> **Bucky Ball said:**
> Tried a different driver? nvidia-glx-new?

Hmm no I don't believe I've tried that (although it sounds familiar)...  What is the difference between nvidia-glx-new and nvidia-glx-177?  

If I install "new" and use the "hardware drivers" console to switch between them, do I have to worry about backing up xorg.conf or any other files?

Thanks in advance...

---

### Post by tomstrummer on 2009-01-21
> **Bucky Ball said:**
> Tried a different driver? nvidia-glx-new?

I just installed nvidia-glx-180 (maybe this used to be the "-new" driver?)

Anyway, I haven't really thought about it all day but I think that might have fixed it...

---

### Post by Bucky Ball on 2009-01-21
That is good news. You will find 'nvidia-glx-new' in Synaptics. The driver to use depends on the age of your card. 177 I think is the oldest. You are probably using 'nvidia-glx' with the 180. Not really sure but check with a search in Synaptics for 'nvidia-glx' maybe.

Basically though, if it ain't broke, don't fix it! Sounds like you might have fixed it.

---

