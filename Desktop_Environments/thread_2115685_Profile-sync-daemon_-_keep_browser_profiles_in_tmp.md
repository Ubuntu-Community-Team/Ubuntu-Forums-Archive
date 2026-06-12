---
title: "Profile-sync-daemon - keep browser profiles in tmpfs"
date: 2013-02-13
forum: Desktop Environments
---

### Post by graysky on 2013-02-13
Wrote my own daemonized version of a script that will symlink your browser's profile directories to tmpfs and keep them sync'ed using rsync.  My stuff is based on [this script](http://www.verot.net/firefox_tmpfs.htm) which I've been using for years except my version is both daemonized and has recovery protection, and also handles the following browsers automatically:

*Chromium
*Conkeror
*Firefox
*Firefox-trunk
*Google-chrome
*Heftig's Aurora
*Midori
*Opera
*Opera-next
*QupZilla

Try running psd in 'parse' mode which will show you exactly what it plans to sync and manage for you based on your /etc/psd.conf
[[img]http://s19.postimage.org/5m8o23cvj/parse.jpg[/img]](http://postimage.org/image/5m8o23cvj/)

Source: [https://github.com/graysky2/profile-sync-daemon](https://github.com/graysky2/profile-sync-daemon)
Wiki:  [https://wiki.archlinux.org/index.php/Profile-sync-daemon](https://wiki.archlinux.org/index.php/Profile-sync-daemon)

To add the PPA (personal package archive) to your Ubuntu (packages available for Lucid and newer) system, and to install psd:

```
$ sudo add-apt-repository ppa:graysky/utils
$ sudo apt-get update
$ sudo apt-get install profile-sync-daemon
```

---

### Post by nilarimogard on 2013-02-13
Great work, thanks! Would it be possible to add support for Firefox Nightly also known as Firefox Trunk? There's an Ubuntu PPA that lets you install it without overwriting Firefox stable or beta and it creates the profile in ~/.mozilla/firefox-trunk (so that's the only change required compared to Firefox).

Edit: and one more thing: "systemctl enable psd.service" doesn't work in Ubuntu since it doesn't use systemd, so how can Ubuntu users add it to startup (I guess you can modify the Upstart script to run on runlevel [2345] or something like that, but maybe it's an easier way that's already available in profile-sync-daemon?)?

---

### Post by graysky on 2013-02-13
> **nilarimogard said:**
> "systemctl enable psd.service" doesn't work in Ubuntu since it doesn't use systemd

The Ubuntu package should not include the systemd init file (although the manpage was written to cover all distros).  Please verify that you have /etc/init.d/psd on your filesystem.  Also, would you mind posting the output of:

```
mount | grep tmpfs
```
and
```
df -h | grep tmpfs
```

---

### Post by nilarimogard on 2013-02-14
Mm it is running on startup in Ubuntu, sorry, I didn't check, I thought it may need some changes.

---

### Post by graysky on 2013-02-14
> **nilarimogard said:**
> Mm it is running on startup in Ubuntu, sorry, I didn't check, I thought it may need some changes.


Not sure I understand.  What changes would you propose?  The Ubuntu init script is installed.  See the [build log](https://launchpadlibrarian.net/131163944/buildlog_ubuntu-quantal-i386.profile-sync-daemon_5.19.3-1_UPLOADING.txt.gz) from launchpad.

---

### Post by nilarimogard on 2013-02-14
Nothing, it works great, we didn't understand each other it seems. The only thing I would like is support for Firefox Nightly (the profile is under ~/.mozilla/firefox-trunk) :)

---

### Post by graysky on 2013-02-14
> **nilarimogard said:**
> Nothing, it works great, we didn't understand each other it seems. The only thing I would like is support for Firefox Nightly (the profile is under ~/.mozilla/firefox-trunk) :)

Fork me on github; pull requests are welcome.

---

### Post by nilarimogard on 2013-02-14
Done! By the way, I wrote about PSD: [http://www.webupd8.org/2013/02/keep-your-browser-profiles-in-tmpfs-ram.html](http://www.webupd8.org/2013/02/keep-your-browser-profiles-in-tmpfs-ram.html)

---

### Post by graysky on 2013-02-14
> **nilarimogard said:**
> Done! By the way, I wrote about PSD: [http://www.webupd8.org/2013/02/keep-your-browser-profiles-in-tmpfs-ram.html](http://www.webupd8.org/2013/02/keep-your-browser-profiles-in-tmpfs-ram.html)

Wow, that was quick.  Merged.  Thanks for the publicity, btw :)

EDIT: You might want to add to the sentence on your article:

> See if you need to change anything else in this file (Ubuntu users don't need to change anything else; Debian users should change VOLATILE="/run/shm" to VOLATILE="/dev/shm"), then save it.

Actually, the postinst I wrote auto-detects if you are running Ubuntu or Debian and makes this change accordingly... but this assumes the Debian user is using my PPA.

See: [https://github.com/graysky2/profile-sync-daemon/blob/master/common/debian/postinst](https://github.com/graysky2/profile-sync-daemon/blob/master/common/debian/postinst)

---

### Post by nilarimogard on 2013-02-15
I've assumed it's auto-detected, but I've only tested it in Ubuntu so I wasn't sure. Post updated, thanks! :)

---

### Post by maggie85 on 2013-02-16
I am new to Ubuntu and just found this util. All I can say is WOW! This makes chromium start up nearly as fast as I can click the icon.  Amazing tool. Thank you, graysky for it.

---

### Post by graysky on 2013-02-17
> **maggie85 said:**
> I am new to Ubuntu and just found this util. All I can say is WOW! This makes chromium start up nearly as fast as I can click the icon.  Amazing tool. Thank you, graysky for it.

You're welcome.  Enjoy.

---

### Post by Hodevah on 2013-02-19
Hi graysky ;) 
Does your script run auto or does one have to manually start it up in some way.

**EDIT:**

> Processing triggers for ureadahead ...
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

user@user-desktop:~$ sudo gedit /etc/psd.conf
user@user-desktop:~$ sudo gedit /etc/psd.conf
user@user-desktop:~$ mount | grep tmpfs
udev on /dev type devtmpfs (rw,mode=0755)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
user@user-desktop:~$ df -h | grep tmpfs
df: `/root/.gvfs': Permission denied
tmpfs           3.2G  984K  3.2G   1% /run
user@user-desktop:~$ sudo df -h | grep tmpfs
tmpfs           3.2G  984K  3.2G   1% /run


Where specifically will it show that it will run if I might ask please?

---

### Post by graysky on 2013-02-21
> **Hodevah said:**
> Hi graysky ;) 
Does your script run auto or does one have to manually start it up in some way.

Where specifically will it show that it will run if I might ask please?

No, you will need to start the daemon.

1) Edit /etc/psd.conf to define your user(s) and optionally your browsers.
2) To preview what profiles will be managed, run ```
$ psd p
```
3) When happy, start the daemon ```
$ sudo service psd start
```

It will autorun on reboot.  Enjoy.

---

### Post by Hodevah on 2013-02-23
Is this the correct output that I should have recieved?

```
user@user-desktop:~$ sudo service psd start
user@user-desktop:~$ 

```

---

### Post by graysky on 2013-02-24
> **Hodevah said:**
> Is this the correct output that I should have recieved?

Yes.  Query status:
```
% service psd status
 * profile-sync-daemon is running
```

You may also ask psd directly:
```
% psd p
Profile-sync-daemon v5.27.1 on Ubuntu 12.10.

Daemon file /var/run/psd is present.

Psd will manage the following per /etc/psd.conf settings:

 browser/psname:  chromium/chromium
 owner/group:     graysky/users
 sync target:     /home/graysky/.config/chromium
 tmpfs dir:       /tmp/graysky-chromium
 profile size:    46M
```

---

### Post by Hodevah on 2013-02-24
I have the same now



```
user@user-desktop:~$ service psd status
 * profile-sync-daemon is running
user@user-desktop:~$ psd p
/etc/psd.conf: line 18: chromium: command not found
Profile-sync-daemon v5.24

Psd will manage the following per /etc/psd.conf settings:

 browser/psname:  chromium/chromium
 owner/group:     user/user
 sync target:     /home/user/.config/chromium
 tmpfs dir:       /run/shm/user-chromium
 profile size:    77M

 browser/psname:  firefox/firefox
 owner/group:     user/user
 sync target:     /home/user/.mozilla/firefox/xixrznrk.default
 tmpfs dir:       /run/shm/user-firefox-xixrznrk.default
 profile size:    189M



```So the above output is good. But for some reason it tells me 

```
/etc/psd.conf: line 18: chromium: command not found
```As far as I know everything in the .conf file is as it should be

> 

# List browsers separated by spaces to include in the sync. Useful if you do not
# wish to have all possible browser profiles sync'ed
#
[B]# Possible values:
        chromium
#        conkeror.mozdev.org
        firefox
#        firefox-trunk
#        google-chrome[/B]
#        heftig-aurora
#        midori
#        opera
#        opera-next
#        qupzilla
#
  Also I think that there is something missing here. Isnt there? Or am I wrong?

```
user@user-desktop:~$ mount | grep tmpfs
udev on /dev type devtmpfs (rw,mode=0755)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)



user@user-desktop:~$ df -h |grep tmpfs
tmpfs           3.2G  984K  3.2G   1% /run
```

---

### Post by graysky on 2013-02-24
> **Hodevah said:**
> ...for some reason it tells me 

```
/etc/psd.conf: line 18: chromium: command not found
```As far as I know everything in the .conf file is as it should be

  Also I think that there is something missing here. Isnt there? Or am I wrong?

That error is caused by you modifying the instructional section of /etc/psd.conf - add a # to those lines to fix; you only need to define the browsers of choice in the line that starts with, "BROWSERS=" - the commented part before it is purely informational.

> **Hodevah said:**
> ```
...

 browser/psname:  firefox/firefox
 owner/group:     user/user
 sync target:     /home/user/.mozilla/firefox/xixrznrk.default
 tmpfs dir:       /run/shm/user-firefox-xixrznrk.default
 profile size:    189M
```

As an aside, you have tried running [profile-cleaner](http://ubuntuforums.org/showthread.php?t=2116412)?  189M seems kind of big to me.

> **Hodevah said:**
> ```
user@user-desktop:~$ mount | grep tmpfs
udev on /dev type devtmpfs (rw,mode=0755)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)

user@user-desktop:~$ df -h |grep tmpfs
tmpfs           3.2G  984K  3.2G   1% /run
```

That is normal. On my box:

```
% mount | grep tmpfs
udev on /dev type devtmpfs (rw,mode=0755)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)

% df -h |grep tmpfs
tmpfs           401M  736K  400M   1% /run
```

---

### Post by Hodevah on 2013-02-24
Ok. So I ran the profile cleaner from your other thread. Cleaned out some mess and I think this is better is it not?

```
user@user-desktop:~$ service psd status
 * profile-sync-daemon is running
user@user-desktop:~$ psd p
Profile-sync-daemon v5.27.1 on Ubuntu 12.10.

Daemon file /var/run/psd is present.

Psd will manage the following per /etc/psd.conf settings:

 browser/psname:  chromium/chromium
 owner/group:     user/user
 sync target:     /home/user/.config/chromium
 tmpfs dir:       /run/shm/user-chromium
 profile size:    78M

 browser/psname:  firefox/firefox
 owner/group:     user/user
 sync target:     /home/user/.mozilla/firefox/xixrznrk.default
 tmpfs dir:       /run/shm/user-firefox-xixrznrk.default
 profile size:    102M

user@user-desktop:~$ 
```

One final thing. 

> # USERS="facade happy"
USERS="**user**"

That is correct, is it not since I need to define a user.


.

---

### Post by graysky on 2013-02-24
You should be good to go.

---

### Post by svo on 2013-02-25
First post here folks, so please be tolerant, I was flying along with profile sync daemon until this morning - went to start firefox and got "your firefox profile cannot be loaded. it may be missing or inaccessible" It appears my psd.conf file is missing. I've tried to remove the ppa and reinstall but no luck. I am relative new to ubuntu ( highly likely operator error here) about 2years. Any help greatly appreciated

---

### Post by graysky on 2013-02-25
> **svo said:**
> First post here folks, so please be tolerant, I was flying along with profile sync daemon until this morning - went to start firefox and got "your firefox profile cannot be loaded. it may be missing or inaccessible" It appears my psd.conf file is missing. I've tried to remove the ppa and reinstall but no luck. I am relative new to ubuntu ( highly likely operator error here) about 2years. Any help greatly appreciated

One step at a time... what is the output of:
```
$ psd p
```

---

### Post by svo on 2013-02-25
[QUOTE=graysky;12530128]One step at a time... what is the output of:
```
$ psd p
```[/QUOTE

Cannot find  so bailing.	Reinstall package to use Profile-sync-daemon.

---

### Post by graysky on 2013-02-25
> **svo said:**
> ```
Cannot find  so bailing.	Reinstall package to use Profile-sync-daemon.
```

OK... do this:

```
sudo apt-get purge profile-sync-daemon
sudo apt-get update
sudo apt-get install profile-sync-daemon
```

Now edit /etc/psd.conf adding your user(s) to the USERS array.  When finished:

```
$ sudo service psd start
```

Finally, post the output of:
```
psd p
```

---

### Post by svo on 2013-02-25
psd p
Profile-sync-daemon v5.27.1 on Ubuntu 12.04.2 LTS.

Daemon file /var/run/psd is present.

Psd will manage the following per /etc/psd.conf settings:

 browser/psname:  chromium/chromium
 owner/group:     david/david
 sync target:     /home/david/.config/chromium
 tmpfs dir:       /run/shm/david-chromium
 profile size:    49M

 browser/psname:  firefox/firefox
 owner/group:     david/david
 sync target:     /home/david/.mozilla/firefox/o4ki1lo4.default
 tmpfs dir:       /run/shm/david-firefox-o4ki1lo4.default
 profile size:    404M

---

### Post by graysky on 2013-02-25
@svo - OK.  This looks good.  You should be running just fine now.  Are you able to use your browsers?

---

### Post by svo on 2013-02-25
Thanks so much for your great help graysky. Up and running, this is the beauty and reason why I love linux.

---

### Post by graysky on 2013-02-25
> **svo said:**
> Thanks so much for your great help graysky. Up and running, this is the beauty and reason why I love linux.

Glad to hear it.  Can you verify that the daemon starts automatically when you reboot?  Just reboot and post the output of:

```
service psd status
```

---

### Post by svo on 2013-02-25
$ service psd status
 * profile-sync-daemon is running

---

### Post by graysky on 2013-02-25
> **svo said:**
> $ service psd status
 * profile-sync-daemon is running

Good.  Enjoy.

---

### Post by dbtmro on 2013-11-27
Hi graysky. After a update of psd from ppa and problems with firefox profile, I've managed to get firefox to work but psd p doesn't list firefox anymore only chromium wich was installed before psd update and worked and still works great also beeing listed ok by psd p. Can you please make psd p list and sync firefox again. I want to mention that I've searched for solution on forums, man page, wiki, etc. since psd's last update and couldn't find a solution. Thank you.

---

### Post by graysky2 on 2013-11-27
> **dbtmro said:**
> Hi graysky. After a update of psd from ppa and problems with firefox profile, I've managed to get firefox to work but psd p doesn't list firefox anymore only chromium wich was installed before psd update and worked and still works great also beeing listed ok by psd p. Can you please make psd p list and sync firefox again. I want to mention that I've searched for solution on forums, man page, wiki, etc. since psd's last update and couldn't find a solution. Thank you.

Hmm... I need more info.  Post the output of:
```
psd p
```

Also of:
```
cat ~/.mozilla/firefox/profiles.ini
```

---

### Post by dbtmro on 2013-11-27
> **graysky2 said:**
> Hmm... I need more info.  Post the output of:
```
psd p
```

kitty@kitty-RV515:~$ psd p
Profile-sync-daemon v5.44 on Ubuntu 12.04.3 LTS.

 Daemon pid file is present.
 Resync cronjob is present.

Psd will manage the following per /etc/psd.conf settings:

 browser/psname:  chromium/chromium
 owner/group id:  kitty/1000
 sync target:     /home/kitty/.config/chromium
 tmpfs dir:       /run/shm/kitty-chromium
 profile size:    47M

Also of:
```
cat ~/.mozilla/firefox/profiles.ini
```

kitty@kitty-RV515:~$ cat ~/.mozilla/firefox/profiles.ini
[General]
StartWithLastProfile=1

[Profile0]
Name=Default User
IsRelative=1
Path=k767dng8.Default User
Default=1

---

### Post by dbtmro on 2013-12-02
...any clue anyone?

---

### Post by dbtmro on 2014-03-16
I had to reinstall my system (Ubuntu 12.04 LTS) to be able to use the browsers again :( Now after the last update of psd (today) my browsers are not working anymore and I'm pretty sure that I'll end up reinstalling my system again :( I'll never use psd or any other [COLOR=#000000]graysky2's apps ever again. [/COLOR]

---

### Post by graysky2 on 2014-12-23
> **dbtmro said:**
> I had to reinstall my system (Ubuntu 12.04 LTS) to be able to use the browsers again :( Now after the last update of psd (today) my browsers are not working anymore and I'm pretty sure that I'll end up reinstalling my system again :( I'll never use psd or any other [COLOR=#000000]graysky2's apps ever again. [/COLOR]

Sorry about your bad experience.  For some reason I stopped getting notification that this thread was updated, so didn't see your replies until months later.  All I can tell you is that psd is pretty mature and adopted on almost a dozen distros now.  Likely a total reinstall of your system was not needed.  A simple restore if your backup data should have been sufficient.  The Ubuntu post install script should print out:
```
ALWAYS backup your profiles data before using utils like psd
```

Anyway, glad you're back up and running.

---

### Post by graysky2 on 2014-12-24
Version 5.60 has just been released which offers the ability to use overlayfs to improve sync/unsync operations as well as lower the memory footprint. Typical speed ups are modest based on this HDD-based system. These times are on a fresh boot while systemd is loading up all other services, YMMV.

WIthout overlayfs:
```
% systemd-analyze blame | grep psd
          6.560s psd.service
           177ms psd-resync.service
```


With overlayfs:
```
% systemd-analyze blame | grep psd
          1.388s psd.service
           283ms psd-resync.service
```


The lower memory footprint is due how overlayfs works, only syncing to tmpfs what has changed in the profile. Here is an example running psd in parse mode, note the "overlayfs size" report compared to the total "profile size" report for each profile:

```

% psd p
Profile-sync-daemon v5.60 on Ubuntu 14.10

 Daemon pid file is present.
 Resync cronjob is present.
 Overlayfs v22 is currently active.

Psd will manage the following per /var/run/psd.conf settings:

 browser/psname:  chromium/chromium
 owner/group id:  facade/100
 sync target:     /home/facade/.config/chromium
 tmpfs dir:       /run/shm/facade-chromium
 profile size:    93M
 overlayfs size:  7.3M


 browser/psname:  firefox/firefox
 owner/group id:  facade/100
 sync target:     /home/facade/.mozilla/firefox/f8cv8bfu.default
 tmpfs dir:       /run/shm/facade-firefox-f8cv8bfu.default
 profile size:    145M
 overlayfs size:  13M

 browser/psname:  firefox/firefox
 owner/group id:  facade/1000
 sync target:     /home/facade/.mozilla/firefox/vd1iqcbn.default-1395954548178
 tmpfs dir:       /run/shm/facade-firefox-vd1iqcbn.default-1395954548178
 profile size:    14M
 overlayfs size:  13M
```

These numbers will change depending on just how much data is written to the profile, but you get the idea. Just update and enable the option in /etc/psd.conf. Note that you MUST `modprobe overlayfs` if you wish to use this feature. To load it automatically on boot, simply add "overlayfs" to /etc/modules-load.d/loadme.conf and you're all set.

---

### Post by tjk on 2015-05-19
I've been trying to get profile-sync-daemon to work.  But it appears that overlayfs isn't working as the file sizes are 0.  Here's some info:

$ profile-sync-daemon parse
Profile-sync-daemon v5.73 on Ubuntu 14.04.1 LTS

 Daemon pid file is present.
 Resync cronjob is present.
 Overlayfs v22 is currently active.

Psd will manage the following per /var/run/psd.conf settings:

 browser/psname:  firefox/firefox
 owner/group id:  tim/1000
 sync target:     /home/tim/.mozilla/firefox/mwad0hks.default
                   Permissions are 755 on this profile.
                   Recommend a setting of 700 for increased privacy!
 tmpfs dir:       /run/shm/tim-firefox-mwad0hks.default
 profile size:    175M
 overlayfs size:  81M
 recovery dirs:   none

 browser/psname:  google-chrome/chrome
 owner/group id:  tim/1000
 sync target:     /home/tim/.config/google-chrome
 tmpfs dir:       /run/shm/tim-google-chrome
 profile size:    91M
 overlayfs size:  0
 recovery dirs:   none
----------------------------------------
$ mount | grep tmpfs
none on /sys/fs/cgroup type tmpfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
tmpfs on /tmp type tmpfs (rw,noatime,mode=1777)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
--------------------------------------------
$ df -h | grep tmpfs
tmpfs           2.8G  3.3M  2.8G   1% /tmp
tmpfs           555M  1.4M  553M   1% /run

---

### Post by tjk on 2015-05-19
EDIT: I'm embarrassed.  I hadn't run the browsers before I ran the parse command...  Everything is working fine now that I'm using the browsers.

---

