---
title: "Unity keeps scrambling my icons..."
date: 2013-06-16
forum: Desktop Environments
---

### Post by Inodoro Pereyra on 2013-06-16
Ok, I'm running 12.04 on a dell inspiron 1525.
Ever since I installed it, I keep rearranging Unity's icons, in a way that makes more sense to me, but, every time I restart the computer, everything gets scrambled again.
Is there a way to make it stay the way I like it?
And, while we're at it, is there a way to make the icons smaller than 32 pixels? Let's say, like 15 to 20 pixels?
Thanks in advance. :)

---

### Post by Frogs Hair on 2013-06-16
If you use the following command it will restore the icons to default.  You can add your favorites again and see what happens after reboot. 

```
unity --reset-icons
``` Another Option: ```
unity --reset
```

Change Icon size with CCSM:  [http://askubuntu.com/questions/70306/can-i-make-the-launcher-icons-smaller-than-32-pixels](http://askubuntu.com/questions/70306/can-i-make-the-launcher-icons-smaller-than-32-pixels)

---

### Post by Inodoro Pereyra on 2013-06-16
Thank you. So I can't change my icon size...:(

I will try to reset Unity, and report back.

---

### Post by Inodoro Pereyra on 2013-06-16
Damn it!
I used this code:

```
unity --reset-icons
``` 

And it screwed up everything. I lost a bunch of icons...

How do I change it back to where it was before? :(

---

### Post by Frogs Hair on 2013-06-17
As I wrote the command restores the icons to defaults and you will have to add your most used applications again. You can add the applications as before by opening them and locking them to the launcher with a right click. dragging and dropping also works. 

If you followed the link posted to Ask Ubuntu you would find that the icon size can be changed to below 32 pixels by installing the CCSM and following the instructions.

---

### Post by Inodoro Pereyra on 2013-06-17
> **Frogs Hair said:**
> 
If you followed the link posted to Ask Ubuntu you would find that the icon size can be changed to below 32 pixels by installing the CCSM and following the instructions.

I DID follow it, and I do have CCSM already installed. It only works for 13.04. I'm running 12.04 LTS, so no luck.

---

### Post by Frogs Hair on 2013-06-17
> **Inodoro Pereyra said:**
> I DID follow it, and I do have CCSM already installed. It only works for 13.04. I'm running 12.04 LTS, so no luck.

Excuse , I missed the update part.:redface:  None of the tweak tools such as MyUnity  , Ubuntu Tweak and the Uninty Tweak Tool have settings below 32 pixels and this is the case 12.10  and newer releases. The CCSM on 13.04 is currently the only way.

---

### Post by OmgItsPixelated on 2013-06-18
Ubuntu Tweak is probably the easiest way from what i've tried.

---

