---
title: "Help with Adminstrative Password"
date: 2009-05-20
forum: General Help
---

### Post by stokebob on 2009-05-20
Hi,

Having a problem with a password... It's a fairly new install, only one user and subsequently only one password has been set during install. When I try to access synaptic from the GUI menus I'm asked for the admin password, I enter my login password and I'm told it's wrong. It also happens on using Update Manager from the menus.

If i try to run synaptic from the command line using sudo, it acepts my password and loads!! Shouldn't the adminitrative password and sudo be the same?

Being a bit new to linux I'm a bit clueless as to what's going on here, any help you can offer would be much appriciated.

Thanks in advance

---

### Post by Joeb454 on 2009-05-20
They should be the same thing.

So you can use sudo on the command line (which accepts your password and works?) but not via the graphical interface?

I suppose we'd better make sure you're getting your password correct when using the GUI? (I'm sure you are, but first thing's first ;))

---

### Post by stokebob on 2009-05-20
> **Joeb454 said:**
> They should be the same thing.

So you can use sudo on the command line (which accepts your password and works?) but not via the graphical interface?

I suppose we'd better make sure you're getting your password correct when using the GUI? (I'm sure you are, but first thing's first ;))

Yeap, tried it loads of times, one after the other.. checked caps lock. everything i can think of.

But that seems to be it, GUI a no go where as sudo works

---

### Post by stokebob on 2009-05-21
OK, now I've found that when I download a .deb and try to install, the package installer is launched.. which then asks for a password, and guess what, wrong password! Anyway I can get around this??

Cheers

---

### Post by stokebob on 2009-05-22
Anyone any ideas before I re-install? seems su command doesn't work aswell.. but only ever used that on other distros, unsure if ubuntu uses that command anyway.

Cheers

---

### Post by Alias1407 on 2009-05-22
Open up a terminal and type....

```
sudo passwd
```

Try that and see if that works, if you haven't done it before it will set the root password.

If it doesn't work post the output of the message.

---

### Post by stokebob on 2009-05-22
Mint!! That worked! Cheers Alias, no idea how i managed to cock it up.. nothing to do with my constat messing lol

---

### Post by Alias1407 on 2009-05-22
That's ok,

I had the same problem when I first started to use Ubuntu.


Happy free travels!!

---

