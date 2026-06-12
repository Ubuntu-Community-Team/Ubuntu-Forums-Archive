---
title: "cannot log in to desktop"
date: 2012-08-10
forum: Desktop Environments
---

### Post by Tijn1978 on 2012-08-10
Hi guys,

I can't seem to open my desktop anymore. After powering on my 64 bit ubuntu asus laptop I see the login screen and I can reach a desktop as guest (no password). However, using my normal user name and password brings me back to that same login page I just entered my password in.
Things I've tried: I have removed in my home: .metacity and the other hidden dirs. I have removed /tmp/X0rg-lock file. I have done unity --reset. I really went through a lotta forums to find a command to use. None worked so far. I also tried sudo apt-get install --reinstall ubuntu-desktop. It is almost a fresh install of ubuntu 64 bit (12.04). The only thing I've done is installing virtualbox. Within virtualbox I have a windows XP and an Ubuntu server. The ubuntu server was removed from within virtualbox and remade using virtualbox standard configurations. I am pretty sure virtualbox isn't doing this to me.
Are there maybe other files I can remove? So that everything gets configured again?
Do I just boot from a stick or cd and do a rescue? I am not very familiar with rescue cd's. I don't want to reinstall everything, there must be another way of doing this. Also noting that guest account still works and logs into desktop. It has to be a setting.

Hope someone can point me into the right direction. I will post whatever works underneath in the bottom of this thread.

Greetz

---

### Post by steeldriver on 2012-08-10
have you looked at the ownership of your ~/.Xauthority file yet? that's the #1 cause of getting bounced back to the greeter screen in my experience

---

### Post by Tijn1978 on 2012-08-10
You are my hero, I chmod'ded it 777 (not good practice i know) and it logs into desktop.
I thank thee very much, I'll be looking what read/write rights this file should be given. Until then Im back in.

ps )  root root -rw* *** *** (that's what it was)

and now: root root -rwx rwx rwx (now)

Hope this helps someone

Greetz,
Tijn1978:guitar:

---

### Post by steeldriver on 2012-08-10
it should be

```
-rw------- 1 *user*  *user*
```

the easiest way is just to rm it and let X recreate it on your next session start

---

### Post by Tijn1978 on 2012-08-10
```
-rw------- 1 *user*  *user*
```the easiest way is just to rm it and let X recreate it on your next session start[/QUOTE]
Did as you asked and it worked. It might be an idea to have script in lets say /tmp when and while changing and configuring. This script would rm -rf the .[configstuff] and afterwards all you have to de is re-log in. Thanks again.
Greetz,
Tijn1978:popcorn:

---

### Post by Altacus on 2013-02-17
I think chown may be easier.

sudo chown user.usergroup ~/.Xauthority

example
sudo chown fred.fred ~/.Xauthority


> **Tijn1978 said:**
> You are my hero, I chmod'ded it 777 (not good practice i know) and it logs into desktop.
I thank thee very much, I'll be looking what read/write rights this file should be given. Until then Im back in.

ps )  root root -rw* *** *** (that's what it was)

and now: root root -rwx rwx rwx (now)

Hope this helps someone

Greetz,
Tijn1978:guitar:

---

