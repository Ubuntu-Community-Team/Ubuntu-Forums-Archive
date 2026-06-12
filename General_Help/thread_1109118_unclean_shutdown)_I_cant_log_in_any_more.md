---
title: "unclean shutdown) I cant log in any more"
date: 2009-03-28
forum: General Help
---

### Post by grappler_toto on 2009-03-28
i just put ubuntu on my computer yesterday(3/26/09)and i was downloading the updates and downloading falsh and it just stoped so i tryed to restart the computer and from there it said unclean shut down.it made me type in fsck and then from there i had to corecct files? im all new to this but after some kinda of break threw it came back to the log in screen and i typed in my login name and it says use the correct case over and over again my log in name is tyler. just like that so i know im not typeing it wrong.so if some one know the problem it would be great if you could help me out thank you.

---

### Post by Yownanymous on 2009-03-28
> **grappler_toto said:**
> **use the correct case**

...

---

### Post by cariboo on 2009-03-28
Linux is case sensetive, you have to enter your username and password exactly as you typed them when you setup Ubuntu.

edit: Yownanymous beat me to it. :)

Jim

---

### Post by grappler_toto on 2009-03-28
i am i used all lower case letters to type tyler

---

### Post by grappler_toto on 2009-03-28
oh and there is a timer saying loging in user tyler in 10 secs and after thos 10 secs pass it pops to a black screen and then gos back to the login screen again....im so lost

---

### Post by Yownanymous on 2009-03-28
> **grappler_toto said:**
> oh and there is a timer saying loging in user tyler in 10 secs and after thos 10 secs pass it pops to a black screen and then gos back to the login screen again....im so lost

Oh dear... This happened to me with Mint once... I can't for the life of me figure out what to do with it though...:(

Edit: That's not to say I don't think there is a fix, there's bound to be.

---

### Post by grappler_toto on 2009-03-28
should i just try and upload ubuntu again?

---

### Post by Yownanymous on 2009-03-28
> **grappler_toto said:**
> should i just try and upload ubuntu again?

Well, it depends if you want to save any important documents first...

---

### Post by grappler_toto on 2009-03-28
no not really so you think that would do the trick?

---

### Post by Yownanymous on 2009-03-28
Well, I'd wait another little while to see if anyone who knows about this stumbles on this thread tbh...

Are you using Wubi/Dual-booting with Windows?

---

### Post by grappler_toto on 2009-03-28
no just wiped my hard drive and put ubuntu on tryed downloading flash and the updates and things just got crazy so i rtryed to restart it and it said the file system cheak failed and i had to do it by myself(i had no idea what i was doing) and i finaly managed to get back to the login screen. and im stuck there

---

### Post by lisati on 2009-03-28
I had the looping "ubuntu will log on in 10 seconds" message once after a fresh install. I eventually solved it by doing a fresh install, wiping out the existing installation

---

### Post by grappler_toto on 2009-03-28
i hope theres another way to fix it.

---

### Post by grappler_toto on 2009-03-28
ttt

---

### Post by ethoxyethaan on 2009-03-28
Hello,

try hitting ctrl+alt+F1


Log in as root or as normal user, then su to root, (this should work)

try:

```

apt-get install --fix-broken
apt-get update
apt-get upgrade 
apt-get install gnome

```

---

### Post by grappler_toto on 2009-03-28
so i just type that in?

---

### Post by grappler_toto on 2009-03-28
it wouldent let me log in as root it says log-in failed where do i go from hear? it said TYLER tty1: where i was trying to ever root or normal user.

---

### Post by grappler_toto on 2009-03-28
ttt

---

### Post by grappler_toto on 2009-03-29
at the bottem of the looping screen it shows my name in all caps like this TYLER // and then the time and date and stuff.

---

