---
title: "can only use use terminal"
date: 2011-02-24
forum: Desktop Environments
---

### Post by f4rm0r on 2011-02-24
Hi, I tried to change from gdm to xdm, but now It won't work to start, and since I don't have an X-environment I can't connect to internet (this is my game computer i'm on right now...)
so I hope that you guys could help me.

first I tried to switch so that gdm opens with fluxbox, that worked brilliantly.
by using this script in both .xinitrc and .xsession:

#! /bin/bash
gdm session &&
exec fluxbox

but then I thinked: but I want to play minecraftwhen I'm travelling, but I need more power to do that...

so I tried to install and use xdm as default, but then it didn't work to startup, so I tried this:
change in .xinitrc and .xsession:

#! /bin/bash
xdm session &&
exec fluxbox

but it still does not work. so I can only terminal on my Liux computer...

So can anyone help me with this?

---

### Post by Krytarik on 2011-02-24
First remove those entries from the files, since it is imo an unusual way to choose a default DE. You can use the "nano" editor for that, it's fairly intuitive compared to the other command line editors:
```
nano .xinitrc
```Then the other.

If you restart after this, XDM should come up with the usual login options, there you can choose a "Session", after entering/clicking your name, and those choice should be remembered the next time you login. No need to manually modify any files then.

If you use autologin, just logout after the autologin to get those options. Alternatively you can specify your default DE manually in "~.dmrc".

---

### Post by f4rm0r on 2011-02-24
I tried to do what told me to, nut it still does not start up, I even tried to remove those files, but it just did not work

---

### Post by Krytarik on 2011-02-24
Then try:
```
sudo dpkg-reconfigure xdm
```
or "gdm" if that doesn't work.

---

### Post by f4rm0r on 2011-02-25
Hi, i've tried what you told, but I only get this message: system start/stop links for /etc/init.d/xdm already exist.

about a week ago I tried to reinstall gdm by typing;

sudo apt-get remove gdm
sudo apt-get install gdm

I can't install it again since I need to download 741 kb of archives

---

### Post by Krytarik on 2011-02-25
Is "gdm" then installed currently?
```
dpkg -l |grep gdm
```
If so, then try the mentioned command.

---

### Post by f4rm0r on 2011-02-26
As I said, Can't reinstall gdm, so it is not installed....

---

### Post by Krytarik on 2011-02-26
Try to get to the console with network access by following the first steps of this guide:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

You could also download it from here:
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=gdm](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=gdm)

and install it with "dpkg":
```
sudo dpkg -i package_name.deb
```
If you issue the command from the "root shell prompt", then run it without "sudo".

---

### Post by f4rm0r on 2011-02-26
thanks alot, now I can finally use my computer wise again. because now it works as it were supposed to work - with X-server up and running

but do you guys know how to switch to XDM without this to happen?

---

### Post by f4rm0r on 2011-02-26
sorry for dubbel post, but I must tell U this

it worked fine, that will say, until I reboot computer, because then I get an init error;

init: ureadahead main process (51) terminated with status (5)

and then it tries to boot, but it can't since it having massive amounts of problems with apparmor, and then it still want to start xdm, but it fail with doing so, so it freezes, (I can only have teminals now, again...)

shall I write what it says (only the thing I can see) on the screen when it freezes?

---

### Post by Krytarik on 2011-02-26
A log would be great, if you can pull it out there: "/var/log/messages".

Please post it in code-tags, the #-button in the editor.

But it worked before, after installing GDM?

---

