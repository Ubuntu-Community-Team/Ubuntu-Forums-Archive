---
title: "129 MB hard disk used on apparently empty /home"
date: 2006-07-22
forum: Desktop Environments
---

### Post by abhidg on 2006-07-22
I just installed Dapper on my laptop (Compaq 3018TU), and everything except the mic works perfectly! I was surprised to see the scroll area work.

However, I noticed that even as a new user on an empty home, I still see 129 MB being used in /home. What could be using this?

---

### Post by taurus on 2006-07-22
How big is /home initially and you can run this from a terminal to see what directory is taking up most space in /home?

```

sudo du /home

```

---

### Post by jISh on 2006-07-22
Open up your /home folder with Nautilus and push CTRL+H.
Not so empty, eh? :)

It's application data and such.

---

### Post by abhidg on 2006-07-22
sudo du /home gives lots of output,
at the end: 37476 ( I believe that's the total)

But df gives 168684 used. 
Why the difference?

---

### Post by metalheart on 2006-07-22
Use
```
du ~ -sh
```
for your own profile size (~ for your home folder, -s option for total and -h for showing it in gigabytes).
```
man du
``` gives you more information on command.

---

### Post by abhidg on 2006-07-22
Thanks for your suggestions.

I did du ~ -sh and it showed 39M
But df -h is showing 167M in /home partition.
and I have no other user. 
:???:

---

