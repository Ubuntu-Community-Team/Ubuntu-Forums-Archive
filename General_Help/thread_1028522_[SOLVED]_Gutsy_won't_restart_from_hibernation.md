---
title: "[SOLVED] Gutsy won't restart from hibernation"
date: 2009-01-02
forum: General Help
---

### Post by shelbyvision on 2009-01-02
I use hibernate all the time on my Gateway desktop computer, but for some reason, on my HP laptop, the very same OS, with all the latest updates, will not start back up after hibernating. It hangs up on a screen that I see for a fraction of a second when it's starting normally. It's a screen with lots of colors distributed in a banded or tiled pattern. I think it's the Ubuntu logo trying to materialize against a black background. I suspect a video card problem, but I have no idea what to do. I like to be able to hibernate my laptop since it tends to overheat if left on too long. Can anyone help me with this?
Thank you,
Steve

---

### Post by shelbyvision on 2009-01-03
I've been looking at other threads on this kind of problem, and haven't found an answer yet. It appears to be a video card issue, but I've been reading conflicting advice on what to do. I checked my /etc/x11/xorg.conf file and here's what it has on the video card:

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"ati"
	BusID		"PCI:1:0:0"

Should I be using a different driver?

---

### Post by shelbyvision on 2009-01-03
I did some further reading and saw a mention that it could be a swap file issue. I found this: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq), and followed the instructions for creating and installing a swap file. After restarting, my shut down screen no longer included the "Hibernate" option :-?, but it still has "Suspend" which works! (Now, I'm not 100% sure, but I don't think suspend worked before.)Suspend does what I want: idles the computer and leaves programs open, but keeps the computer from heating up. Please correct me if I'm wrong.
Steve

---

### Post by ByKeLaO on 2009-01-03
You may well have already done this, but I'm gonna suggest it anyway:
Your swap partition needs to be twice as big (at least) as the amount of RAM you have in your system in order to hibernate successfully. For example, I have 2GB of RAM and therefore a 4GB swap partition.
The reason you need to do this is because the contents of your RAM are saved into your swap partition when you hibernate the computer.

---

### Post by shelbyvision on 2009-01-03
> **robinjam said:**
> You may well have already done this, but I'm gonna suggest it anyway:
Your swap partition needs to be twice as big (at least) as the amount of RAM you have in your system in order to hibernate successfully. For example, I have 2GB of RAM and therefore a 4GB swap partition.
The reason you need to do this is because the contents of your RAM are saved into your swap partition when you hibernate the computer.

Yes, thanks, I did that. 
I just discovered a new problem: suspend works ok, but for some reason, when I close the lid, it restarts! Now I have to figure that out. :confused:

---

