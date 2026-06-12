---
title: "Firefox not showing some text until I point the mouse over"
date: 2006-09-24
forum: Desktop Environments
---

### Post by five2one on 2006-09-24
Hi, 
I actually have 2 problems, which are not critical, but do drive me mad sometimes.
First one: in firefox(it's firefox32 on ubuntu dapper 64) I sometimes don't see the whole sentence(that is if the sentence ends near the right border of the screen). And if this sentence is, for example in the middle of the page, then I can just point with a mouse to it and the rest of the text will show up.
Second one is general(not just firefox): when I type and want to correct something , but do not want to use backspace, I use the right/left arrows - I start seeing black lines after every letter I pass, which makes it impossible for use, as I stop seeing the cursor.

So, if anyone knows a solution to these 2 problems - I'd really appreciate it!

Thanks!

---

### Post by five2one on 2006-09-28
anyone? plz help!

---

### Post by MacMan on 2006-09-28
I'm not sure, I've never had this kind of problems, but to me they look like video driver issues.

What video-card do you have in your system and which driver are you using in Xorg?

Ciao.

---

### Post by five2one on 2006-09-28
thanks for the reply.
I think it's the video card too, but I couldn't find an answer to this proble m so far...
it's Nvidia 6200 and I'm using the latest driver(loaded by automatix)

---

### Post by MacMan on 2006-09-28
I'd try disabling the 2D acceleration. I did on my system: I didn't notice a performance drop but stability has increased a little bit. OpenGL will work as usual, no need to worry. ;-)

Add this line to /etc/X11/xorg.conf:
```
        Option          "RenderAccel" "0"
```

You should put it in the [device] section where your video card is listed. For example, **my** xorg.conf is like this:
```
Section "Device"
        Identifier      "NVIDIA Corporation NV17 [GeForce4 MX 440]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel" "0"
EndSection

```

I hope this helps.

Ciao.

---

### Post by five2one on 2006-09-28
ok, thanks a lot, man! I'll try it a bit later.

---

### Post by five2one on 2006-10-02
hi again, 
well, I did as u suggested, but unfortunately it didn't help:(
any other suggestions?

---

### Post by MacMan on 2006-10-02
> **five2one said:**
> well, I did as u suggested, but unfortunately it didn't help:(
any other suggestions?

No, sorry, I don't know what else you could do.

I can only suggest you to browse [this forum](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14) and see if you can find something similar to your problem.

If you don't, maybe you can post there your question.

I'm sorry I can't be more helpful.
Ciao.

---

