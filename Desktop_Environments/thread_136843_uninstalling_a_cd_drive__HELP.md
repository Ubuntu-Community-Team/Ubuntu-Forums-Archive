---
title: "uninstalling a cd drive  HELP"
date: 2006-02-26
forum: Desktop Environments
---

### Post by amunimanghi on 2006-02-26
Hi

i was wondering if anyone knew how to uninstall a cd-drive. i have two cd drives. my sister has xp (:evil:), but her dvd drive broke and i want to give her my second one. i know it has something to do with the fstab, but i dont know what an fstab is. im such a newb. :-p.   so can anyone get me a step by step tutorial or something.

---

### Post by Ramses de Norre on 2006-02-26
fstab is a text file used to mount file systems at start up, to edit it type "sudo gedit /etc/fstab" in a terminal.

But I think you can actually just unplug the drive without editing it.
If it would be necessary (if you get errors), you'd want to delete or comment out (typing a # before it) the line which mentions /dev/xxx with xxx the device name of the error massage.
Commenting out is better when you're placing it back soon.

But again I don't think it's necessary to change anything, just unplug it.

---

### Post by amunimanghi on 2006-02-26
i asked my brother, and he said it would f-up the fstab if i did that.

---

### Post by Ramses de Norre on 2006-02-26
If you just unplugged it?
Then delete the line mentioning the dvd drive.

---

### Post by amunimanghi on 2006-02-26
if i just put  # in front of the line, will the line still be there if i unplugg it

---

### Post by stuporglue on 2006-02-26
It'll break something:

IF the drive removed is the master drive drive AND there is a secondary drive on that cable which is in slave mode.

ie. If the drive you're removing is /dev/hdc and you have something on /dev/hdd, then when you remove the master, I'm pretty sure that the slave won't work by itself. 

If that's the case, I think you can just put the jumper on "CS" or "Cable select" for the drive that stays in the box, and it'll still work. 

The added line in fstab shouldn't mess anything up since it only gets called by HAL/gnome-automount when a disk is detected. No drive, no disk --> no detection. I don't think it'll be a problem.

---

### Post by amunimanghi on 2006-02-26
okay thanks for you help. ill try it and post back

---

