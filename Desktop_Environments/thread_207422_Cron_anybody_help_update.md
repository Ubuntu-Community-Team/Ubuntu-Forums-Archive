---
title: "Cron anybody help update?"
date: 2006-07-01
forum: Desktop Environments
---

### Post by woodboy on 2006-07-01
Howdy.... and thanks for any interest and advice. I know just enough to be dangerous.
I am trying to figure out how to set up crontab to run apt-get update.  I am on dial up and would like to be able to set up the update to run in the early a.m. I have the date, time,month etc figured out and I can get it to get online(pon) and it will get offline(poff) what it won't do yet is update. 
Here is my example:  
15 4 29 6 4   pon
17 4 29 6 4   sudo apt-get update && poff

Now I think the problem comes when apt-get scrolls through all the stuff I need to upgade and then says something about wanting to continue, You have to answer yes for it to continue and I don't how to answer that request in the crontab.
Is what I am trying to do...doable?
Thanks

---

### Post by Indras on 2006-07-01
I'm no expert, but I imagine it gets stuck when you try to run as sudo... since it asks for your password.

As far as asking for confirmation, you can simply add "-y" to the apt-get command to assume Yes to all questions.

```
sudo apt-get -y update && poff
```

---

### Post by scxtt on 2006-07-01
try "forcing" it:```
       --force-yes
              Force  yes;  This  is  a dangerous option that will cause apt to
              continue without prompting if it is doing something  potentially
              harmful.  It  should  not  be used except in very special situa-
              tions. Using force-yes can potentially destroy your system! Con-
              figuration Item: APT::Get::force-yes.
```read up on "man apt-get" and give that a shot ... something like "sudo apt-get update --force-yes" ...

sudo shouldn't be a problem if you're using anacron (where you can specify which user to run it as - even root, since you'd have to sudo to even edit the file) and /etc/crontab ...

---

### Post by Indras on 2006-07-01
[QUOTE=scxtt]sudo shouldn't be a problem if you're using anacron (where you can specify which user to run it as - even root, since you'd have to sudo to even edit the file) and /etc/crontab ...[/QUOTE]

Neat, I always wondered about that.

---

### Post by scxtt on 2006-07-01
[QUOTE=Indras]Neat, I always wondered about that.[/QUOTE]yeah, anacron is magical :D

---

### Post by woodboy on 2006-07-01
Thanks for the replys.  So perhaps something like...
sudo apt-get -y update --force-yes && poff

---

### Post by scxtt on 2006-07-01
sure, tho i don't think you'll need both, try the "-y" first ...

---

### Post by woodboy on 2006-07-01
I'll give a try, Thanks for the help. Like I said just enough to be dangerous, but I continue to learn.

---

