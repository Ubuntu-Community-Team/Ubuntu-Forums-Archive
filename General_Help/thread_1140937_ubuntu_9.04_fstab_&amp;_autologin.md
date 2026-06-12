---
title: "ubuntu 9.04 fstab &amp; autologin"
date: 2009-04-28
forum: General Help
---

### Post by the-madman on 2009-04-28
Hi all,

is it just me? I have the feeling the 9.04 is not as good as the 8.10 version is.

I'm missing some nice things or some are not working any more. "It's not a Bug it's a Feature"
I just installed the final release on a spare system and I cant see a big performance increase so far. But what I got now is:

I use the 9.04 alternate installer because one main feature for me is still not ported into the "normal" installer (and I don't understand why). It's the "use guided encrypted lvm" partitioning.

one issue is:
In the last version 8.10 I was very used to the fine feature, that the installer ask me when creating the username (a tick box down there) if I like this user to logon automatically when the systems start. OK, it might not be the most secure option but it was optional. But now its completely removed.
Setting my user now after the installation to auto login results in a black frozen screen on of my tried machines (I additional build in virtualbox a new ubuntu to compare the issues I have and they are the same).
I wonder if it's removed because of security reasons or because the release date was close to ship the version without fixing the feature (bug)?

Is anyone out there able to set a user to logon automatically after a boot or also having a black screen after the boot instead of a login or a Desktop?

2) very nice was the "automount" feature in 8.10 that allowed every fstab entry be mounted whenever the mount becomes available. Useful for Wifi cards that used to load the drive or build the connection later than the fstab is run down.
I wonder if this is now again disabled or if something with
//IP.AD.RE.SS/data    /home/sme/mount    cifs    username=xxx,password=xxx    0    0
is wrong.
After the boot a sudo mount -a is working fine so the values itself seem fine. Nothing in the messages for the boot, so it seems its just ignored.

Was anyone able to make use / install the nbr version?
I downloaded the .img but neither with unetbootin, nor with the win32 disk imager or the ubuntu image writer I was able to boot from the USB stick. Every time it was not able to find the kernel. Not even my Virtualbox was able to boot from a new downloaded disk Image (just to rule download issues out). 
 
If someone was able to install the nbr are you able to tell if there is the guided encrypted lvm available?

Would make sense since the Netbook remix might be considered for Netbooks.
One main feature every Netbook should have is a encrypted filesystem, not to give your data to anyone who will find or steal your netbook.

Anyone out there having the same or can tell me that what I need to change if its a "chair - keyboard interface error"
cheers

---

### Post by Abhinavhardikar on 2009-04-28
Same here. I selected auto login and it freezes with a black screen with the mouse pointer. Some more problems

Keyboard and mouse do not work when you log in the root account. 

ctrl+alt+backspace does not restart X server.

I wish it gets rectified soon

Abhinav:(

---

### Post by the-madman on 2009-05-14
I've filled a bug report for this
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/376439](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/376439)
its very reproduceable

---

