---
title: "Changing Orta settings removed text box for password login"
date: 2011-03-27
forum: Desktop Environments
---

### Post by lifelike27 on 2011-03-27
Hey,

I was just doing some basic changes really for Orta and now when I try to login to Ubuntu, the text box for entering my password at the login screen. Can anyone help me find a quick fix? I really need Ubuntu working to finish my assignments.

Thanks all!

---

### Post by Krytarik on 2011-03-27
I don't know right now, what all Orta changes at the login screen, maybe in addition to the settings I mention below.

But try this:
- press Ctrl+Alt+F1 to switch to a console
- login there
- stop GDM
```
sudo service gdm stop
```- reset all theme settings to their defaults
```
sudo -u gdm gconftool-2 --recursive-unset /desktop/gnome/interface
sudo -u gdm gconftool-2 -unset /apps/metacity/general/theme
sudo -u gdm gconftool-2 --recursive-unset /desktop/gnome/background
```- start GDM again
```
sudo service gdm start
```To change the appearance of the login screen, see the first part of my earlier post:
[http://ubuntuforums.org/showthread.php?p=10468340](http://ubuntuforums.org/showthread.php?p=10468340)

---

### Post by lifelike27 on 2011-03-27
I'm getting this error when trying to stop gdm, but it doesn't seem gdm related.

```
sudo: /etc/sudoers is owned by uid 1000, should be 0
sudo: no valid sudoers sources found, quitting
```

---

### Post by Krytarik on 2011-03-27
I hope that there are not more files which are usually owned by root but are now owned by you.

At first, let's re-install sudo/gksu:
- boot into "recovery mode"
- choose "root shell prompt"
- purge sudo/gksu
```
apt-get purge sudo gksu
```- install them again
```
apt-get install sudo gksu
```
- press Ctrl+Alt+Del to reboot

---

### Post by lifelike27 on 2011-03-27
I'm getting a bunch of errors saying that it cannot connect to the host update servers. Is there any way to do this with a live CD?

> **Krytarik said:**
> I hope that there are not more files which are usually owned by root but are now owned by you.

At first, let's re-install sudo/gksu:
- boot into "recovery mode"
- choose "root shell prompt"
- purge sudo/gksu
```
apt-get purge sudo gksu
```- install them again
```
apt-get install sudo gksu
```
- press Ctrl+Alt+Del to reboot

---

### Post by Krytarik on 2011-03-27
Did it purge those packages then?

There should be an option named "Drop to the root shell prompt with networking", choose that.

---

### Post by lifelike27 on 2011-03-27
Tried that too. It couldn't connect to any network. So would the live CD work?

---

### Post by Krytarik on 2011-03-27
Again, did it remove those packages, and if you confirmed it, some additional packages too?

---

### Post by lifelike27 on 2011-03-27
Sorry I didn't reply to that earlier, I was running to find my live CD. Unfortunately it doesn't reach the process of removing the packages. It apparently needs an internet connection and 'netroot' doesn't work either.

---

### Post by Krytarik on 2011-03-27
Ok, puh, it's really better that way! Because I didn't take into account the removal of packages dependend on them, a simple re-install should also do it.

Since you have no internet connection, we first try to reconfigure "sudo", that may fix it too:
- boot into "root shell prompt" again
- run this command:
```
dpkg-reconfigure sudo
```
- reboot

---

### Post by lifelike27 on 2011-03-27
Right, so that last command didn't give any errors, but when I restart and try to stop gdm or purge sudo, I'm still not able to. Same errors.

---

### Post by Krytarik on 2011-03-27
Don't try purging "sudo" anymore! Because it would remove quite a lot dependend packages as well, like I said. Sorry for confusing you!

Also, please check the ownerships of other files meant to be owned by root, for example by```

ls -al /etc |more
ls -al /usr/bin |more
```If it turns out that there are indeed more files which are owned by you instead, we can stop right now. Then you need to re-install Ubuntu.

If that is not the case, download the deb-package of "sudo" here:
[http://packages.ubuntu.com/maverick-updates/sudo](http://packages.ubuntu.com/maverick-updates/sudo)

And re-install it with dpkg:
- boot into "root shell prompt" again
- change to the location of the deb-package
- enter
```
dpkg -i FILENAME
```I'm not quite sure if those command is sufficient to re-install the package.

---

### Post by lifelike27 on 2011-03-27
Purging surprise wasn't working either way. Trying the rest now. So there isn't anyway to reinstall gdm from a live CD? =\ I used to fix grub like that.

---

### Post by lifelike27 on 2011-03-27
In etc there are a bunch of files owned by me, like conky, computer-janitor etc. It's a long list. In bin, only jedit. I really don't want to do a fresh install. ANY hope? =\

---

### Post by Krytarik on 2011-03-27
> **lifelike27 said:**
> In etc there are a bunch of files owned by me, like conky, computer-janitor etc. It's a long list. In bin, only jedit. I really don't want to do a fresh install. ANY hope? =\
You somehow screwed up the ownerships of many files. Of course you could try to simply change them back to root, if doesn't look like the ownerships of whole directories are changed. But "root" is just a guess, because many files are indeed usually owned by other system 'users'.

To try it, one-by-one (!), boot into "root shell prompt" again, and run commands like this:
```
chown root.root FILENAME
```
But it may well be necessary to re-install.

---

### Post by lifelike27 on 2011-03-27
To fix grub I'd enter:
```
sudo mount /dev/sda3 /mnt 
```Then:
```
sudo grub-install --recheck --root-directory=/mnt /dev/sda 
```

That would reinstall grub to my Ubuntu partition. Is there a way to do the same for gdm? Replace that last command with gdm?

I tried:
```
sudo apt-get remove gdm --root-directory=/mnt /dev/sda
```

But that doesn't work. 


I'm too noobish to figure out how it works. =\

---

### Post by Krytarik on 2011-03-27
You can't compare those both things. And your Grub is fine.

Of course you could try to re-install gdm like described before for sudo: download the package, use dpkg to install it.

---

### Post by lifelike27 on 2011-03-27
I tried installing the gdm by dpkg. Didn't work. =\

---

### Post by Krytarik on 2011-03-27
> **lifelike27 said:**
> I tried installing the gdm by dpkg. Didn't work. =\
Did the installation process work at least?

---

### Post by lifelike27 on 2011-03-27
Yeah, it installed successfully.

---

### Post by Krytarik on 2011-03-27
Did you try to fix the ownerships?

---

### Post by lifelike27 on 2011-03-27
Ok, after recursively changing the ownership and some setuid error I was finally able to use sudo!

I followed your initial commands, but it just changed the background to default. I purged gsm and installed it. That just changed my user account picture to default as well. The password textbook is still missing. 
=\

---

### Post by Krytarik on 2011-03-27
> **lifelike27 said:**
> Ok, after recursively changing the ownership and some setuid error I was finally able to use sudo!
I believe you made it only worse by doing so. Like I said, one-by-one.
> **lifelike27 said:**
> I followed your initial commands, but it just changed the background to default. I purged gsm and installed it. That just changed my user account picture to default as well. The password textbook is still missing. 
=\
Anyway, was worth a try.

You may want to install Natty 11.04 by that way, after upgrading all its packages it should run fairly stable, since it is set for final release in roughly one month time. This way all that has at least something good.
[http://www.ubuntu.com/testing/natty/alpha3](http://www.ubuntu.com/testing/natty/alpha3)

Boot with the InstallCD and backup your home directory before installation. You may try to restore it after the installation. But some of the its contents may well cause errors, therefore restore as few as possible.

---

### Post by lifelike27 on 2011-03-27
I figured there was a reason you said one-by-one, but i wasn't ready to do that for hundreds of files. Thanks a bunch either way. I feel like I've learned tons. I'll try to avoid the same mistakes again.

---

### Post by Krytarik on 2011-03-27
> **lifelike27 said:**
> I figured there was a reason you said one-by-one, but i wasn't ready to do that for hundreds of files.
Ok, I already thought of something like that. The only other option you had after discovering *that* amount of affected files, was to not try it at all.

---

