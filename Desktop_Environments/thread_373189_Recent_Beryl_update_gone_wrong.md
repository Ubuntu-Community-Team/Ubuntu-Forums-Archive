---
title: "Recent Beryl update gone wrong"
date: 2007-03-01
forum: Desktop Environments
---

### Post by sdmike on 2007-03-01
So I updated beryl like 2 weeks ago. Then when I used my computer again. The whole screen is white but get this, when I flip the cube to a top view my picture shows that I put to replace the red beryl diamond.

I'm using an ati 1800xl card.

Plus I can still log back into gnome which tells me hey beryl crashed.

So what should I do to get it back up and running?

---

### Post by Scotty562 on 2007-03-01
Join the club :).

---

### Post by vtron on 2007-03-01
I posted this to another white screen of death thread.  Not sure if it will work for everyone, but it worked for me. I had the same dreaded white screen of death and the following solved it:

Use ctrl+alt+f1 to open a virtual terminal

Backup then edit your .beryl-managerrc file

```
cp ~/.beryl-managerrc ~/.beryl-managerrc.backup
vim ~/.beryl-managerrc
```

Make the beryl-settings section look like this:

```
[beryl-settings] 
render_path=2
cow_mode=0
rendering_mode=0
platform=0
binding=0

```

Some of these settings may not work for you, but playing with some of the settings will probably fix the white screen problem.

---

### Post by MaximB on 2007-03-01
if you still have this problem, you should go back to the old Beryl version as I did.
search Beryl forum for more info on that.

---

### Post by Scotty562 on 2007-03-01
Actually, I just found this today and it solved my problem. It involves downgrading like was mentioned in the previous reply.

[http://forum.beryl-project.org/viewtopic.php?f=43&t=70&st=0&sk=t&sd=a&start=330](http://forum.beryl-project.org/viewtopic.php?f=43&t=70&st=0&sk=t&sd=a&start=330)

Good luck.

---

