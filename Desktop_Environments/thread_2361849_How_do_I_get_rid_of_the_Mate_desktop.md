---
title: "How do I get rid of the Mate desktop?"
date: 2017-05-21
forum: Desktop Environments
---

### Post by Odense on 2017-05-21
I have just installed the Gnome classic desktop and to test it out I decided to also install the Mate desktop (as in the thread below).

[GNOME Classic on Ubuntu 16.04]("https://askubuntu.com/questions/795301/gnome-classic-on-ubuntu-16-04")

I was a bit surprised how much more there needed to be installed with the Mate one compare to the Gnome one).

I tried switching to the Mate desktop and I like the classic Gnome better - but I am not getting the option to switch back at log in.

So I want to completely get rid of the Mate desktop again (uninstall) - how do I do that ?

If that is very difficult I will settle for switching back to the Classic desktop - how do I do that ?

---

### Post by Frogs Hair on 2017-05-21
I would recommend backing-up files before starting as removing additional desktop environments can affect packages needed for the default desktop.

 ```
sudo apt-get remove ubuntu-mate-desktop
```


```
sudo apt-get autoremove

```

---

### Post by Odense on 2017-05-21
I did not want to back up the whole partition - so I chanced it.
But you were right - now a package is missing (se the screenshot).

Any idea how I can get it back ?

And to make it even worse - I STILL do not have the Gnome desktop or a chance to get it :-(
Or maybe it is easier to do a reinstall (or is there a "repair" install option ?)

---

### Post by Frogs Hair on 2017-05-21
If you backed up your important files it would be faster to do a clean installation rather than try to figure out what's missing. I suspect there is more than one thing missing. Get the latest ISO though.  [http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/)

---

### Post by ChuangTzu on 2017-05-21
either reinstall OS Ubuntu Gnome or at grub drop down to tty and ```
sudo apt install ubuntu-gnome-desktop
```

How to tty:
[https://askubuntu.com/questions/66195/what-is-a-tty-and-how-do-i-access-a-tty](https://askubuntu.com/questions/66195/what-is-a-tty-and-how-do-i-access-a-tty)

---

### Post by Odense on 2017-05-22
Thanks.

Addition - none of the explanations I found on tty when searching told me HOW to get into a tty prompt - so can any of you clever people explain that - as simple as possible ?

It is a recent install so I still have the important files. I will try [COLOR=#000000]ChuangTzu's suggestion first though. Do I need to pick a number of the tty at the grub boot menu ? [/COLOR]

> **Frogs Hair said:**
> If you backed up your important files it would be faster to do a clean installation rather than try to figure out what's missing. I suspect there is more than one thing missing. Get the latest ISO though.  [http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/)

---

### Post by deadflowr on 2017-05-22
Do you want gnome classic or gnome flashback?
Gnome classic is actually a tweaked version of the new gnome's gnome-shell.
Gnome flashback is more akin to old gnome, much closer to what mate is.

As to why mate install so much more compared to the classic install did is because mate is a completely different desktop environment.
A desktop environment encapsulates more than just the interface, it also includes media players file managers setting utilities and more.
Mate has it's own and gnome has it's own.
Ubuntu is a gnome desktop, through and through, so it already includes many of those gnome desktop packages.
If you install mate on an Ubuntu desktop, it'll need to install it's own desktop packages.
Hope that helps make some sense of things.

---

### Post by Odense on 2017-05-22
I want one of the flashbacks (Compiz or Metacity I think). I want the one that reminds me the most of the old Ubunto desktop (and Windows 7).

Thanks for the explication - it clears up some things. :cool:

> **deadflowr said:**
> Do you want gnome classic or gnome flashback?
Gnome classic is actually a tweaked version of the new gnome's gnome-shell.
Gnome flashback is more akin to old gnome, much closer to what mate is.

As to why mate install so much more compared to the classic install did is because mate is a completely different desktop environment.
A desktop environment encapsulates more than just the interface, it also includes media players file managers setting utilities and more.
Mate has it's own and gnome has it's own.
Ubuntu is a gnome desktop, through and through, so it already includes many of those gnome desktop packages.
If you install mate on an Ubuntu desktop, it'll need to install it's own desktop packages.
Hope that helps make some sense of things.

---

### Post by deadflowr on 2017-05-22
Then all you really need to install is gnome-panel.
Nothing fancy.
Might take a gander at Kansasnoob's flashback setup here:
[https://ubuntuforums.org/showthread.php?t=2302432]("https://ubuntuforums.org/showthread.php?t=2302432")

Also, not sure whether the crash report error's package matters, but you can try installing it manually if you like
```
sudo apt install avahi-dnsconfd
```

---

### Post by Frogs Hair on 2017-05-22
> [COLOR=#000000]Do I need to pick a number of the tty at the grub boot menu ? [/COLOR] If there are no desktop sessions available you will have to work with tty . There are also recovery options in grub that might shed some light on what you need to do. reinstalling the ubuntu-desktop from tty might be an option as well.

```
sudo apt-get install --reinstall ubuntu-desktop 
```

---

### Post by Odense on 2017-05-23
I had some kind of Mate desktop available (even though I used the commands to uninstall the Mate desktop environment. 
I tried installing the Ubuntu Flashback desktop but it did not seem to help.
> **Frogs Hair said:**
> If there are no desktop sessions available you will have to work with tty . There are also recovery options in grub that might shed some light on what you need to do. reinstalling the ubuntu-desktop from tty might be an option as well.


```
sudo apt-get install --reinstall ubuntu-desktop 
```

So - thanks a lot to deadflowr, ChuangTzu, Frogs Hair and all who contributed.

I would still like to know how it SHOULD be done but it is not urgent any more as I capitulated this time and reinstalled Ubunto + the Flashback desktop.

---

