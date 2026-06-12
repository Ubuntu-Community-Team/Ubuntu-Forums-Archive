---
title: "Stuck before login"
date: 2009-04-26
forum: General Help
---

### Post by LieToPurify3 on 2009-04-26
I dont know what I did, but now when I boot up, I get the waiting cursor before the login screen and it just stays like that.  I can boot into a terminal if I choose recovery mode at Grub, but I dont know what to do from there.  If i try to startx, i get a grey screen with a cursor that I can't move, and it plays the login sound, but nothing happens. Any ideas?

---

### Post by jwbrase on 2009-04-26
Did you just upgrade to Jaunty?

---

### Post by Bucky Ball on 2009-04-26
After the sound and the grey screen, could you drop to a shell again (ctl/alt/F1), type:
```

dmesg
```... and check the last few events in the list. That should give us some idea of what is crashing. Sounds like a video/monitor problem. Please provide whatever details you can regarding machine, graphics card and monitor. You can get info about what's in the box in a shell by typing:

```
lspci
```You will find your graphics card/onboard graphics in the output somewhere. 

:)

---

### Post by LieToPurify3 on 2009-04-27
Yes, I recently upgraded, but this happened a few days later.

I got it to boot by using recovery mode and choosing repair broken packages.  However, when I boot up, I can still see it listing some errors.  If you tell me some commands to be able to view and post those errors, I will.  Thanks

---

### Post by Bucky Ball on 2009-04-28
Post result of:

```
dmesg
```Copy and paste into your post.

Also, have you gotten your updates and you are online? If not, plug an ethernet cable in and boot up Ubuntu.

*

In System->Admin->Hardware Drivers

... what is there? Anything for you graphics card?

Re my last post; can't do a lot without knowing what hardware (graphics card, monitor, resolution expected etc). Again, reference my last post (follow the instructions) and post details, please.

---

### Post by LieToPurify3 on 2009-04-28
When I try to post the output, the forum is saying i'm posting 16 images adn the limit is 8. Obviously i'm not posting images so i guess i can just split the response into 2 replies. However, I might just reinstall the new ubuntu version and have a nice clean install and also install another distro, but if you think this is a problem that's worthwhile to have on the forums, then I'll fix it first. Let me know what you think

---

### Post by Bucky Ball on 2009-04-30
You'll probably end up in the same place. Not much point setting up a dual-boot unless you can get the first OS stable before installing the second.

Run 'lspci', find your graphics card in there, write it on a piece of paper and then type that in a post here.

You could try a reinstall, but if you are talking 9.10, it is 'testing' and not as stable as 8.04! The one you have, 9.04, has just been released and there will be bugs to iron out of that also, and is also not LTS (long term support). 8.04 is and will be supported for the next three years or so from memory.

So, the choice is yours.

---

