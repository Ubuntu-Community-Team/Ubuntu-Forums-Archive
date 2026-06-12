---
title: "no software updates with enlightenment"
date: 2013-06-17
forum: Desktop Environments
---

### Post by theDaveTheRave on 2013-06-17
Hi all,

I hope that the title say it all,..

I recently started using e17, and the only thing that bugs me is that I don't seem to get any sofware update notification messages?

I know that this is the case because if I change to LXDE or any other desktop environment I have a little note on the dock to tell me that there are updates to install.

I tried adding the software updated to the enlightenment iBar, but when I open it it needs 'sudo' priviledges, and I can't see how to tell the launcher to launcher this with sudo.

I don't mind having to launch it manually once a week to check for updates.
However as I can't open it and tell it to run as root, it doesn't ask for my sudo login, then it fails to start up as it can't access the required files, it looks in the wrong place if you run it without sudo, or so it would seem.

posible solution:

Create my own launcher that will run update manager in 'sudo', but as I say above I can't see in the 'create launcher' how to set the launch command to include sudo.

I guess I'm missing something?

Anyone got any suggestions?

David

---

### Post by ajgreeny on 2013-06-17
> **theDaveTheRave said:**
> posible solution:

Create my own launcher that will run update manager in 'sudo', but as I say above I can't see in the 'create launcher' how to set the launch command to include sudo.

I guess I'm missing something?

Anyone got any suggestions?

David
It should really be **gksudo update-manager** not sudo, but I do not know E17 well enough to understand how to create a launcher for any application nor how to edit the command it uses.

I will try later tonight when I get a chance with my multiboot live USB which has Bodhi 2.3.0 amongst other OSs on it.

---

### Post by Frogs Hair on 2013-06-17
I used the terminal for updates, but a launcher would have been nice.  

The E17 packages in the Ubuntu repository are bare bones do not receive  updates. The modules that come with fully functional E17 are not even available in the Ubuntu repository. To get a full E17  experience you need to install the svn PPA or an E17 distro like the Ubuntu based Bodhi Linux.[http://www.bodhilinux.com/](http://www.bodhilinux.com/)
 
If you choose to add the linked PPA you have to _remove all currently installed E17 packages_ and the .e folder in home hidden folders or the result will be broken packages. [https://launchpad.net/~hannes-janetzek/+archive/enlightenment-svn](https://launchpad.net/~hannes-janetzek/+archive/enlightenment-svn)

The PPA is bleeding edge and use at your own risk so you may want to keep things as they are , but E17 has much more functionality than you are currently seeing if you only have the Ubuntu repository version. The synaptic package manager is helpful for installing modules if you choose to use the PPA.

---

### Post by theDaveTheRave on 2013-06-17
In fact I am using the ppa version. All the docs seem to suggest that this should be stable, after all this is the 'official e17 release ppa'. if I realy wanted super stability I would go for enlightenment that is based on debian.

I did have the 'old' e16, but I upgraded.

The old .e directory I simply renamed and removed the '.' and this forced the new version to do its 'stuff' during its first login. It does ask if you want notifications, but if I understand correctly it is only for updates to e17 itself.

I've just noticed also that my shortcut to turn off the touchpad isn't working either... it was in e16!

---

### Post by Frogs Hair on 2013-06-17
This PPA is also without modules, but is more up to date than the repoitory version. [https://launchpad.net/~efl/+archive/trunk](https://launchpad.net/~efl/+archive/trunk)

---

### Post by theDaveTheRave on 2013-07-04
I get the impression that this thread, and my other investigations aren't exactly getting me anywhere.

Updates to e17 are not the problem, I understand that it is 'experimental' and so I look for the updates as required.

It is all the other software that is on my ubuntu netbook that I want to get the updates for, this is the stuff that , when using gnome / kde / lxde etc, I have a little 'exclamation mark' icon. I click on this and it shows a list of all the potential updates.

I know that I can do this 'manually' using apt-get, but I want a method where it will notify me once a week, so as I don't have to remember.... although I guess I could run it as a CRON job. But I like to see what I am updating first. So as I can more easily debug any error that I get afterward.

David

---

### Post by Frogs Hair on 2013-07-04
E17 introduced the notification module last year which can work with notify osd , however discussion of update managers seems to be confined to E17 distros.

[http://jeffhoogland.blogspot.com/2012/01/introducing-e17s-notification-module.html](http://jeffhoogland.blogspot.com/2012/01/introducing-e17s-notification-module.html)

---

### Post by theDaveTheRave on 2014-01-11
Hello again all.

So late last year there where so many updates to everything, preparing for e18 I assume, that eventually e17 came to an almost standstill... so I gave it up with a heavy heart and went back to lxde.

Now christmas has come and gone... and a search for e18 showed that it was now available as a propper ppa.

After a few issue with dependencies (there seems to be a requirement for libpoppler19, but the latest livpoppler is version 29) so added a repo that contained the required packages, and 
> 
Sugar honey Ice Tea

all was happy and glorious again.

I'm investigation the libpoppler thing (message on the enlightenment users list). I'll post back when I get any info.

David

---

