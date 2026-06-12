---
title: "Gutsy GNOME Hangs with Compiz"
date: 2007-11-01
forum: Desktop Environments
---

### Post by akshayas1986 on 2007-11-01
Hi everyone.

I have been using Ubuntu Gutsy for over 3 days and as long as Compiz Fusion is enabled, my computer just hangs randomly. Its very irritating as you would be in the middle of something only to realize that all the work has been wasted.

I have disabled all effects now and it has not hung as of now. Is there any way out of this problem?? Please help me. I have a Winfast PX7300LE (GeForce 7300 LE) with 256 MB DDR2 dedicated RAM working on a AMD X2 3800+ Dual core

Thanks

PS: I had a small doubt. How do I use the Tracker Search engine that comes with Gutsy??

---

### Post by akshayas1986 on 2007-11-02
Guys
There is an easy way out

Just disable the restricted drivers.

Install Envy
> sudo apt-get install envy

Run envy from command terminal
> envy -g and follow instuctions. And mostly it should work without hanging anymore

---

### Post by malmjako on 2007-11-06
I have problems with freezes as well. I'm still able to move the mouse, but without any response from the programs. Using Ctrl-Alt-Backspace to kill the session or Alt-F1 to switch to a console doesn't work either.

It seems like the freezes come when I do some window manipulation. For example, I've had freezes when resizing a window (without "live change", just the blue square changing size) and putting a window to the background (with middle mouse button).

I have an ATI Radeon X600, with the open source radeon driver. In Feisty, using packages from Compiz-Fusion (not from the Ubuntu repos), I didn't have any freezes. I've also tried with the proprietary driver, fglrx, but the effects were very slow using that driver with my graphics card.

Any ideas?

---

### Post by akshayas1986 on 2007-11-09
Hi malmjako,
Did you try what I have posted in this thread?

---

