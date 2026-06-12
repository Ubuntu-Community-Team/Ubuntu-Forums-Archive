---
title: "Inspiron 1720 webcam in Ubuntu"
date: 2008-07-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by PinkFloyd102489 on 2008-07-10
Ive gotten everything else to work, including wireless. Now time for the webcam. I cant find anything on the forums or in the Wiki about it. Ive got the driver CD but I have no idea how to install it.

Any ideas?

---

### Post by LeoSolaris on 2008-07-10
[http://ubuntuforums.org/showthread.php?t=828504&highlight=cam](http://ubuntuforums.org/showthread.php?t=828504&highlight=cam)

It isn't for the 1720, but I bet the integrated webcam is the same. Like linuxwizard said, check the cam in Ekiga and see if it works. If it works there, then it is at least being recognized. If not then post the results of:
```

lsusb
(in terminal)

```

It will most likely come up as "Omnivision Technologies, Inc" 

Hopefully it works with Ekiga. That would make things much easier. Snag Camorama and Cheese! from the repos, and check them. You may have to fiddle a little with the settings to get it right. Cheese works perfectly with my 1520, as does Skype.

Leo

---

### Post by PinkFloyd102489 on 2008-07-10
Alright thanks. Im in Vista now, but I'll check it out in a bit when I switch over to Ubuntu.

---

### Post by PinkFloyd102489 on 2008-07-11
Ekiga doesnt pick it up. It's the model you said it would be, though. The cam light flashes on for a second then goes off. It does that during boot, too.

---

### Post by Crafty Kisses on 2008-08-30
You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2) if working with the settings does not work or help.
Post the results of the command > lsusb

---

