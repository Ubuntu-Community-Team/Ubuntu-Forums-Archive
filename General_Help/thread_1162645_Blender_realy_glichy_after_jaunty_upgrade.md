---
title: "Blender realy glichy after jaunty upgrade"
date: 2009-05-17
forum: General Help
---

### Post by The-ITu on 2009-05-17
the render does not come out properly. here is a pictue.  [img=http://i674.photobucket.com/albums/vv109/the-it/Screenshot-1-1.png] [img=http://i674.photobucket.com/albums/vv109/the-it/Screenshot-5.png]  as you can see is just the bottom that is scewring up. how do i fix this?

---

### Post by nolliecrooked on 2009-05-17
graphics card=?

---

### Post by The-ITu on 2009-05-18
> **nolliecrooked said:**
> graphics card=?

it was working fine back when i had 8.10 :(

---

### Post by rizman on 2009-05-18
> **The-ITu said:**
> it was working fine back when i had 8.10 :(

It might still be related to your graphics card, or rather the drivers. A lot of older ATI card have been put on legacy support. Thus the newest catalyst drivers which are used by Jaunty do not support them anymore. If you have one of those cards, Jaunty uses the open-source ATI drivers. This drivers has 3D support, but it is not as good as with the catalyst drivers.

So, which card do you have?

---

### Post by The-ITu on 2009-05-19
> **rizman said:**
> It might still be related to your graphics card, or rather the drivers. A lot of older ATI card have been put on legacy support. Thus the newest catalyst drivers which are used by Jaunty do not support them anymore. If you have one of those cards, Jaunty uses the open-source ATI drivers. This drivers has 3D support, but it is not as good as with the catalyst drivers.

So, which card do you have?
no I don't think I have a graphics card. I think I have a chip set. I know it sucks. do think it has anything to do with that?

---

### Post by skymera on 2009-05-19
Intel graphics chips are buggy with Jaunty

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by rizman on 2009-05-19
@The-ITu: What a coincidence, I just checked the forums a minute after you replied.

You mean an Intel chipset? I read a few reports of people who have an Intel chipset that performance wasn't very good with those in Jaunty. A quick googling threw out the following:
[Troubleshooting Intel graphics performance]("https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance")

Might be helpful.
[ ]("https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance")

---

### Post by The-ITu on 2009-05-19
> **skymera said:**
> Intel graphics chips are buggy with Jaunty

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
so is there like a patch or something a i can download which will make this work?

---

### Post by The-ITu on 2009-05-19
> **rizman said:**
> @The-ITu: What a coincidence, I just checked the forums a minute after you replied
im not  surprised. this forum is PACKED!!. I have never seen a more active forum.

---

### Post by skymera on 2009-05-19
> **The-ITu said:**
> so is there like a patch or something a i can download which will make this work?

It tells you what to do! Read it.

---

### Post by rizman on 2009-05-19
> **The-ITu said:**
> so is there like a patch or something a i can download which will make this work?

The instructions on the site you posted seem pretty clear. Just follow those and you should be fine.

---

### Post by The-ITu on 2009-05-19
> **skymera said:**
> It tells you what to do! Read it.
sorry i thought you just sent a link full of information rather tan instructions.
il do it when i have time, and then I will post and tell you if blender has improved its behaviour.

---

### Post by rizman on 2009-05-19
I think we got a little confused here.

skymera posted a link to instructions on how to restore the older drivers in jaunty:
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

I posted a link to a bunch of informations regarding the performance issue:
[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance)

The link I posted links to the same page skymera posted.

So just follow the instructions on the page skymera posted and you should be fine.

---

### Post by The-ITu on 2009-05-20
blender still does not work properly.
I folowed the links you guys sent.
thanks anyway :(
EDIT: hmm it seams no one can help me. awww well :'(

---

