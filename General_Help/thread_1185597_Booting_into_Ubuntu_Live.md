---
title: "Booting into Ubuntu Live"
date: 2009-06-12
forum: General Help
---

### Post by Nickeline on 2009-06-12
I can't do it. The menu appears after I boot to the CD, I can do everything apart from click enter, I've tried two working keyboards and the numerical enter and it will not work. So all I'm left with is a pretty looking logo :(

The version is 9.04, I'm on a Dell Dimension 5000. P4 processor, 2GB RAM etc.

What do I do?

---

### Post by Nickeline on 2009-06-12
guys?

---

### Post by Therion on 2009-06-12
Does booting with the LiveCD bring you to the Ubuntu Desktop?

---

### Post by Nickeline on 2009-06-12
No, I'm stuck at the menu where you can decide to install , try, memory test or boot.

---

### Post by Therion on 2009-06-12
Ah, okay...  I can see the screen you're talking about (in my head).  When you're on that screen can you use the Arrow keys or Tab to highlight a selection?  

What I'm trying to figure out is if the keyboard is responding *AT ALL*.

---

### Post by user sam on 2009-06-12
I had this problem on my mac mini once. I never figured it out, but sometimes it works if you just wait. Did you wait for the 60 seconds before it boots the cd automatically? Sometimes that works.

---

### Post by Nickeline on 2009-06-12
yep the arrow keys work and tab works, and it doesn't auto boot.

---

### Post by Nickeline on 2009-06-12
wait, tab doesn't do anything

---

### Post by Therion on 2009-06-12
Okey doke.  Methinks the problem lies with your install media.  

When you burned this install CD did you burn it slooooowly, say around 16x or so, or did you just let the burning app have at it?

Edit:  Okay so tab does NOT work...  Do the arrow keys?  

Like I said, I'm trying to figure out if your keyboard is at all responsive at this point.

---

### Post by Nickeline on 2009-06-12
I burned it at 22x

---

### Post by merlinus on 2009-06-12
Far too fast. 4x or slower is best.  Also, you might run a checksum on your .iso as there may be errors.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Nickeline on 2009-06-12
I guess I should reburn it?

---

### Post by Nickeline on 2009-06-12
k thanks for the help ;)

---

### Post by merlinus on 2009-06-12
Yes, but do a checksum first,  The link in my post gives info on how to do it.

---

### Post by Therion on 2009-06-12
> **Nickeline said:**
> I burned it at 22x
Mmmm... Yeah, I'd re-burn it.  Slow it down to 8x or so this time.  This isn't a race and we need accuracy, not speed.

---

### Post by user sam on 2009-06-12
Okay, let me get this straight. You get to the live cd menu. Did you get past language selection? What I understand is that you did, and you can highlight different selections in the menu with the arrow keys, but cannot hit enter to boot into one them. Is that right?
Hopefully, reburning the cd should work.

---

### Post by zebsdad on 2009-06-12
I had the exact problem for 3 days. I finally stumbled across the MD5 check program and I had to download again to get it right.

I burned the .iso cd with Imgburn at 4X and it all worked from then on.....

See post #11 for the link to MD5 checking.

---

### Post by Nickeline on 2009-06-12
I re-burned another, at 2x and it still ain't working. Any thoughts?

---

### Post by Nickeline on 2009-06-12
Interestingly I can choose the option to boot into the first hard disk

---

### Post by basiix on 2009-06-12
have you tried re-downloading the .iso?

---

### Post by synapsys on 2009-06-12
Yeah you burned it slower and that's fine but did you run a checksum to see if your download was corrupted like everybody is telling you?

---

