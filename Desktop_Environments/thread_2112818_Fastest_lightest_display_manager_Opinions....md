---
title: "Fastest lightest display manager? Opinions..."
date: 2013-02-05
forum: Desktop Environments
---

### Post by einstein**-7 on 2013-02-05
UBUNTU 12.04

I use a lot of software that is heavy on RAM and VRAM mainly the latter right now I'm running lightdm with unity and a cairo dock also dual screen VRAM usage is around 300mb's on startup.   

What are your opinions  on the fastest display manager that uses the least VRAM and still looks good and is customizable?

---

### Post by Frogs Hair on 2013-02-05
Still looks good and is relative to taste but I think Lubuntu is the lightest in terms resource use. E17 offers a lot of options as far as native dock/shelve support and is very light but the only easy way to have it as a stand alone desktop is to install an E17 distro.

[http://www.bodhilinux.com/](http://www.bodhilinux.com/)

Customized E17

---

### Post by Artemis3 on 2013-02-06
Enlightenment 0.17.1 (from the EFL PPA) is taking 46MiB of ram in a Xubuntu 12.04 install... Go Bodhi i say :)

Not only is that small, it surpasses KDE in features, customability and even looks; really; this is it. Use the app called "Everything" if you want tablet like interface.

[img]http://www.chimerarevo.com/wp-content/uploads/2013/01/E17-600x337.png[/img]

---

### Post by Cheesemill on 2013-02-07
You don't need to even use a display manager if you don't want to.

My system boots into a text login screen, if I want to use the GUI then I run the startx command.

---

### Post by ibjsb4 on 2013-02-07
> **Cheesemill said:**
> You don't need to even use a display manager if you don't want to.
My system boots into a text login screen, if I want to use the GUI then I run the startx command.

Hay Cheesmill :)

There is even a no display manager in the repo's, better known as [URL="http://www.enricozini.org/sw/nodm/"]nodm.  
[/URL]

---

### Post by spynappels on 2013-02-07
xmonad, simple tiling WM.

```
stefan@stefan-ssdubuntu:~$ ps -eo comm,rss,vsz | grep xmonad
xmonad-i386-lin  4140  11420
```

---

### Post by Cheesemill on 2013-02-07
Are we all talking about the same thing here?

I seem to be the only one whose suggestion has anything to do with a display manager, everyone else is talking about window managers or desktop environments.

To clarify a display manager is your login screen, and nothing else.

---

### Post by ibjsb4 on 2013-02-07
> **Cheesemill said:**
> Are we all talking about the same thing here?

Does seem to be a bit of that going around :)

Comes down to it, I think lightdm is hard to beat.

---

### Post by spynappels on 2013-02-07
> **Cheesemill said:**
> Are we all talking about the same thing here?

I seem to be the only one whose suggestion has anything to do with a display manager, everyone else is talking about window managers or desktop environments.

To clarify a display manager is your login screen, and nothing else.

Very true, but the context in which the OP asked the question suggested to me he meant the WM. Could just be me though...

---

### Post by type4corp on 2013-02-08
Well if it's a Display Manager then i would use slim as a Desktop Environment  i would use razor-qt which is openbox and a panel.

---

### Post by ibjsb4 on 2013-02-14
So is it lightdm or not?

---

