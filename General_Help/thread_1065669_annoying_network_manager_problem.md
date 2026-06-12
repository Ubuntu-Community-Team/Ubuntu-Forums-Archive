---
title: "annoying network manager problem"
date: 2009-02-10
forum: General Help
---

### Post by -jay- on 2009-02-10
hi it seems like every day several times every few hours the network manager pops up saying disconnected a second later im connected again then it goes back to disconnected it keeps doing this for 10 mins at a time what can i do to make this from happening again

---

### Post by x33a on 2009-02-10
it might be a problem with your isp.

what connection do you connect to? wired, wireless?

---

### Post by -jay- on 2009-02-10
wired no router

---

### Post by x33a on 2009-02-10
post the output of /var/log/syslog.

---

### Post by SeanTater on 2009-02-10
Sorry, my browser had troubles posting...

Anyway, note this the next few times it disconnects:
```
pidof NetworkManager
```

If the numbers change, it's crashing.
To see why, skim over/post this:

```
sudo grep -riC 2 networkmanager /var/log | tail -n 500
```

---

### Post by -jay- on 2009-02-10
ok i will post back when it happens again

edit how do i post the log everytime i do it errors out trying to post

---

### Post by Iowan on 2009-02-11
Are you trying to paste or attach... what kind of error message when trying to post?

---

### Post by -jay- on 2009-02-12
here is my syslog in a file hope somebody can pinpoint the issue im having

---

### Post by -jay- on 2009-02-13
bump this is getting very annoying seems its getting worse now

---

### Post by -jay- on 2009-02-15
so does anybody know ?

---

### Post by -jay- on 2009-02-16
bump

---

### Post by -jay- on 2009-10-13
after several months i still have this issue

ok each time is diff numbers so def crashing

---

