---
title: "Ubuntu Installation Errors"
date: 2006-02-12
forum: Desktop Environments
---

### Post by nephesh on 2006-02-12
Sorry guys I'm yet another linux newbie here to ask for help on an install.  I have two errors so far, one of which is probably my fault, the other...well I don't know what's up with it.

The first error:
When it gets to setting up a username/password I follow the directions, type in my full name, let it auto pick the username as my first name, and then enter the password and confirm it.  The problem here is that after I've confirmed the password it just automatically goes straight back to the "Enter your full name" screen and starts the username/password process over.  It will do this over and over indefinitely.  Finaly I decided to just continue without setting up a username password figuring I could just fix it by logging in as root later on.  So I continued on and the machine rebooted and told me to remove the CD, I do so, it boots up and runs some more setup stuff, then yet again I get to the username/password portion and try again to get past it.  This time as I confirm the password for a very brief second an error message displays, I had to do this many times to finally be able to read and write down the whole error.  This is what it shows.

groupdel: group <username> does not exist
chpassword: line1: unknown user <username>
chpassword: error detected, changes, ignored

When I cancelled and left this part of the setup I went back and it asked me to setup a root password, this works just fine for me so I just skipped the other user hoping I could fix it later.

The second error(this one is most likely my ignorance at work):

This error is about configuring the graphics adapter.  It's asking what PCI port I'm using or something.  The format is this:

PCI:1:0:0

I have tried leaving it blank like the instructions say, I have tried leaving it at the default.  Every time I've tried to load X windows it fails.  So I don't know what is up with this or how to fix it.

I am using a Radeon 9800 pro in the agp port.

If you actually took the time to read all this I really appreciate it.  I will appreciate it even more if anyone can help me!  Thanks in advance.

Nephesh

---

### Post by nephesh on 2006-02-12
I'm not going to claim I figured it out.  I do however have ubuntu working now.

I tried one last install and miracle of miracles the username/password error disapeared.  Then it went through installing and didn't ask me for any setup options..
Now I'm typing this on the ubuntu desktop..
I did absolutely nothing different than before.  Just one of those weird things.

Feel free to delete this thread if you like mods, and thanks.

---

### Post by zxee on 2006-02-13
I'm thinking that getting the xserver running is probably the first order, but if you wanted to create a regular user from the commandline you would just do 'adduser username' where 'username' is whatever you want.
To see if you can get x going do 'dpkg-reconfigure xserver-xorg' which should run through the xserver setup. Choose ati for a video driver. Hope that helps.

---

### Post by gazj on 2006-02-13
X get my ATI card wrong when ubuntu was installed, it detected it as the ATI driver, but i had to change the driver to r128 which i think is the ATI Rage 128 driver, then everything worked fine, this could or could not be your problem, just thought i might shed some light on the problem, and theres more driver choices than just ATI

---

