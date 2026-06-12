---
title: "[SOLVED] a small list of problems - might be all related?"
date: 2008-12-28
forum: General Help
---

### Post by bluepowder7 on 2008-12-28
hi all,

ok, so i'm noticing a trend with my two machines (desktop & server) - the more updates i do, the worse things get.  my desktop is running xubuntu 8.04-64, and my file server is running 7.10-32

my problems, from most to least annoying, are like this (and they might all be related so one fix could cure it all)

item 1 is no longer an issue
[COLOR="Cyan"]1 - ssh is buggered, but works.  when i try to ssh connect to my file server, i get errors about keys not matching up and being invalid, but then i get asked for a password and things seem to be ok.  i updated the ssh on the server some time ago, and just got my computers set up again (i was moving and left that until the end).  anyhoo, i hand-copied the key from the server and edited the key file on the desktop.  maybe i did it wrong, or missed a digit, so what's the best way to fix the keys?[/COLOR]

2 - file server's storage drive gets mounted to desktop pc (using nfs), and a lot of the times trying to browse the mounted drive gets me "loading folder contents" which takes a long time to finish, regardless how far into the subfolders i am or how many files are at that level.  sometimes, once it's done, double-clicking a file to run it (movie, music, whatever) takes a while for it to open.  file server is using lvm with 3 hard drives (2 ide and 1 sata), all formatted to jfs.  it's at 1.1TB total, with around 40G free space.  not sure if it's choked, overly fragmented, or the B+ tree is hosed.  sometimes reboots help, sometimes just waiting a few mins helps, but it's horribly annoying since it didn't happen before.

items 3, 4, and 5 are no longer an issue
[COLOR="Cyan"]3 - wicd is buggered.  it coughs up errors during "sudo aptitude update" and other similar actions, and won't remove itself when i do "sudo aptitude install network-manager".  it also doesn't actually open when i click on the wicd item in the menu (using Xubuntu)

4 - one CPU core (have athlon x2) sometimes shoots up to 100% use, then after a few seconds the other core goes to 100% as the first unloads.  sometimes no reason, a lot of times operapluginwrapper needs to be killed to calm things down.  this normal?

5 - opera got updated to the newest one (9.63), but i found 9.50 more stable (doesn't close on its own or freeze up for no reason).  how can i roll back to 9.50 ?  my typical way of installing and updating stuff is "sudo aptitude ...."[/COLOR]

6 - file associaltions (open with...) keep getting reset and it's annoying.  mp3 and avi and mpg and whatnot keep getting reset to open with "Movie Player", so i have to keep resetting the right-click properties to open with VLC / Audacious.  why does it keep resetting every so often, and is there a central file that i can edit to keep it from doing that?

---

### Post by albinootje on 2008-12-28
> **bluepowder7 said:**
> 
1 - ssh is buggered, but works.  when i try to ssh connect to my file server, i get errors about keys not matching up and being invalid, but then i get asked for a password and things seem to be ok.  i updated the ssh on the server some time ago, and just got my computers set up again (i was moving and left that until the end).  anyhoo, i hand-copied the key from the server and edited the key file on the desktop.  maybe i did it wrong, or missed a digit, so what's the best way to fix the keys?


Edit your ~/.ssh/known_hosts accordingly.
The error-message should tell you which line in ~/.ssh/known_hosts is the problem.

---

### Post by bluepowder7 on 2008-12-31
when i do "ssh myfileserver", this is the error message(s) that i get.  the key is one that i manually copied over from the server and manually entered into the known_hosts file.

what's the proper way to (1) find the keys on the server, and (2) paste them into the known_hosts file on the desktop machine?  i can easily run two side-by-side terminals to do it, but do i just edit & overwrite the existing keys, or is there a special way of adding them?


```

greg@greg-desktop:~$ ssh server1
buffer_get_bignum2_ret: negative numbers not supported
key_from_blob: can't read rsa key
key_read: key_from_blob AAAAB3NzaC1yc2EAAAABlwAAAQEAtXyJfxKwKWqVLje07rLpiyOJU35X7N1CsQ2Xyr19e4DZIKfgrv4YRz9SA5bkJpjTBLIlP2qc78q41i6/VMpTQxgDTnGvE9nnN31Gw7Ye8CyR2D/fdS2kSQJ3i+UgdlcVii6gg32dfa+n3TjXfo+kaFRsBNb+ThOcIeCmVkRfFAScU4pkjMRIU00RkIPZWNYiyo49jk4Pygy2RhAbw0qRTZsTFYJjC0LjmlkRBHJbUAYx0SuJfEOi75yKp7X4G8WD6jmTfhZk2LFHLRgV124eWGVwJBkn8zcwPFv7K+mXRFaBhdydIgzPvS98D1NOoE2w84gtZIHHWGfXWf+m29HnaQ==
 failed
key_read: uudecode AAAB3NzaC1yc2EAAAABlwAAAQEAtXyJfxKwKWqVLje07rLpiyOJU35X7N1CsQ2Xyr19e4DZIKfgrv4YRz9SA5bkJpjTBLIlP2qc78q41i6/VMpTQxgDTnGvE9nnN31Gw7Ye8CyR2D/fdS2kSQJ3i+UgdlcVii6gg32dfa+n3TjXfo+kaFRsBNb+ThOcIeCmVkRfFAScU4pkjMRIU00RkIPZWNYiyo49jk4Pygy2RhAbw0qRTZsTFYJjC0LjmlkRBHJbUAYx0SuJfEOi75yKp7X4G8WD6jmTfhZk2LFHLRgV124eWGVwJBkn8zcwPFv7K+mXRFaBhdydIgzPvS98D1NOoE2w84gtZIHHWGfXWf+m29HnaQ==
 failed
greg@server1's password: 
Linux server1 2.6.22-15-server #1 SMP Wed Oct 22 00:24:38 GMT 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Mon Dec 29 10:39:25 2008 from desktop
greg@server1:~$ 

```

---

### Post by albinootje on 2008-12-31
> **bluepowder7 said:**
> when i do "ssh myfileserver", this is the error message(s) that i get.  the key is one that i manually copied over from the server and manually entered into the known_hosts file.


Normally you would not edit ~/.ssh/known_hosts at all, only to remove or comment out lines.
Please undo the changes, or remove ~/.ssh/known_hosts

Do you want to use ssh with public key authentication perhaps ?

[http://tombuntu.com/index.php/2008/02/20/public-key-authentication-for-ssh-made-easy/](http://tombuntu.com/index.php/2008/02/20/public-key-authentication-for-ssh-made-easy/)

---

### Post by jamesisin on 2008-12-31
Why do the words Opera and Freeze appear in your post?

I ask because I am having trouble with my system freezing and I happen to run Opera:

[http://ubuntuforums.org/showthread.php?p=6471803](http://ubuntuforums.org/showthread.php?p=6471803)

---

### Post by jamesisin on 2008-12-31
Oh, I see.  You hid some text.  May not be related to what I'm seeing on my system.  Let me know if you think differently.

---

### Post by bluepowder7 on 2008-12-31
i solved my opera issues (at least so far) by disabling java and plugins, but still allowing javascript.  i use firefox for the flash stuff, but opera for my main browsing simply cuz i'm hooked on the wicked mouse gestures / speed dial / etc features of opera.  i'm back to opera 9.50 though since it was dead-stable for me, and i've put a hold on the revision so future upgrades won't shove me into 9.6x or anything like that.

---

### Post by jamesisin on 2009-01-01
You may want to take a look at my Opera tutorial:

[http://www.soundunreason.com/InkWell/?p=197](http://www.soundunreason.com/InkWell/?p=197)

I have Java disabled, but it's mostly because I don't care for Java.  I've not seen any problems with my Opera (and I'm using the latest Debian version).

---

### Post by bluepowder7 on 2009-01-04
> **albinootje said:**
> Normally you would not edit ~/.ssh/known_hosts at all, only to remove or comment out lines.
Please undo the changes, or remove ~/.ssh/known_hosts

Do you want to use ssh with public key authentication perhaps ?

[http://tombuntu.com/index.php/2008/02/20/public-key-authentication-for-ssh-made-easy/](http://tombuntu.com/index.php/2008/02/20/public-key-authentication-for-ssh-made-easy/)



ah, perfect!  thanks!  that did the trick beautifully.  now i just have one problem left (item 2), which got MUCH worse last night, so that's a new thread i think...

---

