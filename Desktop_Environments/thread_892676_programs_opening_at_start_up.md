---
title: "programs opening at start up"
date: 2008-08-17
forum: Desktop Environments
---

### Post by geovino on 2008-08-17
I recently installed Xubuntu 8.04 and I've noticed that when I boot up kaffeine opens and orage and calendar all pop up on he desktop. How do I turn them off in XFCE so they don't open on boot.

---

### Post by dje on 2008-08-17
It's in the Applications >> settings >> settings manager >> autostarted applications (i cant quite remember exactly i havent used xfce for a while ;) )

dje

---

### Post by geovino on 2008-08-20
Thanks, I looked in there but the items that are on auto-start aren't the ones that are opening up at start up. Also Firefox opens at start up and I don't remember this ever happening.

---

### Post by Magimog on 2008-08-20
Maybe it has to do with unticking "Save last session" on the logout screen?

---

### Post by mali2297 on 2008-08-20
Remove the hidden directory **.cache** in your home folder. It contains saved sessions.

---

### Post by jimmy the saint on 2008-08-20
[http://ubuntuforums.org/showthread.php?t=854557](http://ubuntuforums.org/showthread.php?t=854557)

Check out post # 4.

---

### Post by jack009 on 2008-08-20
The longer you own a Windows PC, the slower it boots up. This is because you will likely install numerous applications on your computer over time. Some of these applications will be boxed software purchased from Office Depot or Staples, but most will probably be applications you've bought online after downloading free trial versions for evaluation. The problem is that many programs you buy from stores or download from the Internet will install programs or services that start up automatically whenever Windows starts. 
===============================================================
jack009

[ Rhode Island Drug Treatment]("http://www.drugtreatments.com/rhode-island")

---

### Post by Cheesehead on 2008-08-20
If you logged out in the past with all those apps open,
and you happened to click 'save this session' just once,
then that's how you got them.

If so, then they are very easy to get rid of:
1) Close all your apps.
2) Logout, saving your session.
3) Log back in...see if any reappear.

Logging out/in is sufficient - you don't need to reboot.

---

### Post by geovino on 2008-08-21
I tried that, but Orage keeps coming up and I tried a couple options. I never seen this come up before when I used Xubuntu last year. I must be missing something.

---

### Post by kidux on 2008-08-21
Did you delete the .cache folder as mentioned above? I was having a similar problem until I deleted that.

---

### Post by geovino on 2008-08-21
> **kidux said:**
> Did you delete the .cache folder as mentioned above? I was having a similar problem until I deleted that.


That's right. Where is the .cache folder located?

---

### Post by Cheesehead on 2008-08-21
Hey, I remember this!

Orage Preferences --> Display
Calendar Start section, you want 'Hide'. It often defaults to 'Show'

---

### Post by kidux on 2008-08-22
> **geovino said:**
> That's right. Where is the .cache folder located?

It's in your /home/[username] dir. When you get there, press [ctrl]+h show hidden files/folders, then delete it.

---

### Post by geovino on 2008-08-23
> **kidux said:**
> It's in your /home/[username] dir. When you get there, press [ctrl]+h show hidden files/folders, then delete it.

Got it. Thanks. :)

---

