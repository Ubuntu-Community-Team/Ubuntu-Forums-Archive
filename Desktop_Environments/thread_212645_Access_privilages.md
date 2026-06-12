---
title: "Access privilages"
date: 2006-07-10
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-07-10
I went away on holiday and took my laptop with me so that mates could transfer digital pics onto it wihlst on holiday.  I set up a 'guest' account specifically for this.

On return to holiday I wanted to copy the photos into my own home profile.  I logged in as root as did a "mv /home/guest/pics /home/ME/pics/holiday".

Of course, this meant that I would need root access to view the photos, which was not what I wanted, so I did 'chmod 666 /home/ME/pics/holiday', and now it's all gone a little wrong.  I can't view the photos as I can't open the folder in nautilus (i can view the pics as root from the terminal of course).  Trying as normal user to change to the directory in my own home directory that contains the pics tells me that permission is denied.

What should I do to fix this?

---

### Post by bartbes on 2006-07-10
eehm.. as far as I know you need 7 for full access not 6, try it
(so 777, 755, or even 700)
because 6 means only write and execute no read :p

---

### Post by Lunar_Lamp on 2006-07-10
I just tried all of those, and whilst I can now view the files and see that they are there, I cannot open them as a normal user!  I really don't get this :s

---

### Post by diepruis on 2006-07-10
chmod 777 only gives the owner and users in the file's group access to it. You might not own it. Try chown <yourusername>:<yourusername>

---

### Post by Lunar_Lamp on 2006-07-10
root@PMSEH:/home/ed# chmod 777 /home/ed/pics/holiday/
root@PMSEH:/home/ed# chown ed:ed /home/ed/pics/holiday/

I tried that and still cannot access files via nautilus as normal user 'ed'.

---

### Post by bartbes on 2006-07-10
maybe you want to try to chmod recursive
```

chmod -R 777 /home/ed/pics/holidays

```

---

### Post by Lunar_Lamp on 2006-07-10
Thanks, that worked a treat.  I hadn't realised it was possible (or necessary) to do recursive chmods.

---

