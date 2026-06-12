---
title: "Can't switch to terminal anymore"
date: 2015-12-19
forum: Desktop Environments
---

### Post by gtozzi on 2015-12-19
Hi there,

since last update, I can't switch to temrinal anymore. Here is what happens when I try hitting CTRL+ALT+F1:

[http://picpaste.com/z8RMB0Ny.jpg](http://picpaste.com/z8RMB0Ny.jpg)

the black bar seems to contain a blinking cursor, and some form of "malformed" text.

If i cycle terminal (F1-F5), the noise changes... any ideas?

Thank you

---

### Post by sudodus on 2015-12-19
Which version are you running (which released version or the developing version Xenial Xerus)?

---

### Post by gtozzi on 2015-12-20
Thank you for your reply. I am running 15.10, it used to work in 15.04.

---

### Post by sudodus on 2015-12-20
It *should* work in 15.10, so that's a bug. I found this one:

[Bug #1520059](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1520059)

If you recognize it, I suggest that you click on the green text and mark 'Affects me too'.

---

### Post by gtozzi on 2015-12-20
Mhhh... i think it's a different problem because Nathan can't switch to terminal at all, while I can switch, but get scrambled output instead.
Also, the suggested fix "sudo chvt 2' does produce the desired effect" does not work for me: it still produces the scramble effect.

---

### Post by sudodus on 2015-12-20
In that case I suggest that you make an own bug report at Launchpad. If you don't know against which package, I suggest that you try with 'ubuntu' or 'linux' and we can hope someone else can find the failing package.

```
ubuntu-bug ubuntu
```

You might refer to bug #1520059 and say why you think it is another bug.

---

### Post by kc1di on 2015-12-20
What is your video Card?  and which driver are you using?
and does ```
Crtl=Alt+t
```  bring up the terminal?

---

### Post by gtozzi on 2015-12-20
The card is a NVIDIA Corporation GT218 [GeForce 210].

At the moment I'm using nvidia-340-updates, but i've been trying nvidia-304, nvidia-304-updates, nvidia-340, nvidia-352, nvidia-352-updates and all have the same issue.

I've been using nvidia-340 for many years and it worked correctly before the upgrade, so I do not think it's a driver issue.

ctrl+alt+t does not do anything.

---

### Post by flocculant on 2015-12-21
well - it's definitely not geforce210+nvidia-340-updates causing the problem in themselves, same card/driver worked fine in wily for me and are working fine still in xenial

what happens if you revert to nouveau?

Also - maybe try creating a new user - does that user see the same issue? If they don't then I would assume the issue to be in 'your' config files. You can rename .config to config and login - should clear your personal settings. You'll need to somehow do that outside the normal desktop. If necessary from a recovery root terminal or a booted livesession

---

### Post by gtozzi on 2015-12-21
I have the same problem also when on lightdm, even before any user logs in.

Mhhh... nouveau doesn't seem to work at all, but maybe I didn't insist enough... but even if I manage to get it work, then it will be nothing done, because I need the native driver's capabilities and stability.

---

### Post by flocculant on 2015-12-21
and the rest?

---

### Post by gtozzi on 2015-12-21
no, it happens also with a new user :(

---

### Post by flocculant on 2015-12-22
mmm - what updated prior to the problem? 

/var/log/apt/history.log

Do you get the same with previous kernel?

You'll likely need to report it - but better that you do so with more information than 'I updated and it doesn't work now'

---

