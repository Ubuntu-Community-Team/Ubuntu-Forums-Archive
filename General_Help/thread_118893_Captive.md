---
title: "Captive"
date: 2006-01-17
forum: General Help
---

### Post by angeleyes on 2006-01-17
:confused: 
Im still new to Ubuntu..I need to fix my XP.
I saw in my other post about Captive -I downloaded but I dont really know how to install it. 
Can anyone tell me how?
Thanks (yet again)..You all are a blessing to a Ubuntu newbie..

---

### Post by angeleyes on 2006-01-18
umm is anyone around who can help me do this???

---

### Post by Miguel on 2006-01-18
What have you tried?

It seems a bit tough, but doable.

---

### Post by Killgore on 2006-01-18
Do you actually need to edit or change the files on the Windows XP drive? Because if you only need to recover files Ubuntu has native NTFS support for read-only. 

Just mount the drives: 

```
sudo mkdir /media/windows
```

```
sudo mount /dev/hda1 /media/windows/
```

(taken from Unofficail ubuntu starter guide)

Then you should be able to either burn the files you want copy them to another partition or a usb drive.

Hope this helps.

---

### Post by newuser111 on 2006-01-18
is angeleyes talking about captive ntfs, im not sure

---

### Post by angeleyes on 2006-01-18
I need to try and reinstall a boot file so my Windows XP will boot --so I can run it(hubby and kids like it better then Ubuntu)

---

### Post by izzydahedgehog on 2006-01-28
[https://wiki.ubuntu.com/CaptiveHowTo](https://wiki.ubuntu.com/CaptiveHowTo)

This is a howto I just wrote (because I just got it running myself, and I'm at work and bored) that should work out alright.  And if anyone feels like editing it/cleaning it up, that's cool too.

---

