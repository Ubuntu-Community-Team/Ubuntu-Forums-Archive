---
title: "routine check of hard drives"
date: 2008-12-11
forum: General Help
---

### Post by krysia on 2008-12-11
when turning on the computer it wants to do the usual h/d check
which normally is no problem but in the last couple of days it 
only get to 66% (1.5/1754/1842) before it stalls and won't go
any further so I have to re-boot and click on Esc.to carry on.
I recently installed a second hard drive to run windows on,could
this be causing some conflict with the checking system or something
else.I have never had this problem before so any advice would be
helpful.

---

### Post by Peter09 on 2008-12-11
How long have you waited for the 'stall' before aborting, might be worth leaving it for some time to see if you get an error message.

---

### Post by blazemore on 2008-12-11
Bit of a hack

```
sudo nano /etc/fstab
```

At the end of every entry there's 2 numbers
Change them all to 0

And make sure you always shut down, cos it wont check your disks on startup after this!

---

### Post by kpkeerthi on 2008-12-11
DO NOT blindly set everything to 0 in /etc/fstab. **Thats risky!**. Post the content of your FSTAB and we'll suggest you what you could do.

(At this point, I'm guessing that you have disc check flag turned ON for NTFS, which you should NOT do).

---

### Post by krysia on 2008-12-12
thanks kpkeerthi,
sorry to be dim where would I find fstab ?? and I have never
loaded ntfs.so more advise would be good.

---

### Post by Peter09 on 2008-12-12
Hi,
can you do in a terminal

```
sudo fdisk -l
```

and post the output.

That should show your current partition tables.

---

### Post by kpkeerthi on 2008-12-12
Also post the output of:
```
cat /etc/fstab
```

---

### Post by krysia on 2008-12-13
thanks for all your help with my problem !! but it 
seems that I was just being impatient,when I turned
on the computer this morning and went for a cup of tea
it completed it's h/d check and booted as normall.
that will teach me to be patient,thanks again for all
the help.

---

