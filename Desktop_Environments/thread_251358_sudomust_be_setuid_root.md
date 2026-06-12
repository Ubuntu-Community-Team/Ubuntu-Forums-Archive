---
title: "sudo:must be setuid root"
date: 2006-09-05
forum: Desktop Environments
---

### Post by ferd on 2006-09-05
Above is the message I get when trying to bring up gedit in console. I am also not allowed to use synaptic or the updater and get "su returned with an error" when I try to use them. That is, I am not allowed to enter my password and get this message instead. If this is fixable, how is it done? Thanks in advance.:confused:

---

### Post by Najand on 2006-09-05
> **ferd said:**
> Above is the message I get when trying to bring up gedit in console. I am also not allowed to use synaptic or the updater and get "su returned with an error" when I try to use them. That is, I am not allowed to enter my password and get this message instead. If this is fixable, how is it done? Thanks in advance.:confused:

There is no root account by default at Ubuntu. You can use sudo with your user account to do administrative tusks and gksudo for GUI tusks. If still you need the root accout you can make it using the command:
```
sudo passwd
```
For more information see:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by ferd on 2006-09-05
I am sorry that I did not make myself understood. When I try to use sudo I get "must be setuid root". That is, I cannot go any further than that message. Any function requiring the sudo command cannot be accessed. Thank you for your fast reply.](*,)

---

### Post by Najand on 2006-09-05
> **ferd said:**
> I am sorry that I did not make myself understood. When I try to use sudo I get "must be setuid root". That is, I cannot go any further than that message. Any function requiring the sudo command cannot be accessed. Thank you for your fast reply.](*,)

Have you erased your user ID you are inteding to sudo at the /etc/sudoers file by mistake?
If not and if you are able to su, please check out this command and see if it can solve your problem or not:
```
chown root:root /usr/bin/sudo
chmod 4111 /usr/bin/sudo
```

---

### Post by ferd on 2006-09-05
I booted into rescue to access su. When I ran the commands you suggested I got, "cannot access /bin/sudo no such file or directory" as the reply to both commands.](*,)  Thanks again for your help.

---

### Post by BLTicklemonster on 2006-09-05
Me too. I was trying to get access to my ntfs drive (and there is no thread anywhere that I can find that has the exact answer on how this is done. Look it up, no one who started a thread asking how to access their ntfs drive has said that they got it to work)

So now, I can't do anything with sudo, and I can't access system > administration > disks, and I can't run synapic, and I have an icon telling me I have updates. 


What to do, what to do?

---

### Post by ferd on 2006-09-05
Well, I finally reinstalled and reconfigured. It solves the problem and I have the process down to 4 hours. Good luck to you.

---

### Post by Najand on 2006-09-05
> **BLTicklemonster said:**
> Me too. I was trying to get access to my ntfs drive (and there is no thread anywhere that I can find that has the exact answer on how this is done. Look it up, no one who started a thread asking how to access their ntfs drive has said that they got it to work)

So now, I can't do anything with sudo, and I can't access system > administration > disks, and I can't run synapic, and I have an icon telling me I have updates. 


What to do, what to do?

Well, if you guys cannot find sudo in /usr/bin just
```
$ locate sudo
```
or search for it. and then change the chmod and chown.

---

### Post by BLTicklemonster on 2006-09-05
```
ticklemonster@ticklemonster:~$ locate sudo
locate: fatal error: Could not find user database '/var/lib/slocate/slocate.db':  Permission denied

```

There's sudo in /usr/bin but it's got a red x on it, and a lock.

Now I can go to recovery mode, type chmod 4111 /usr/bin/sudo and it comes back to $ like it took, then what do I do, startx? I boot into the desktop, but can't use anything. And to top it off, I get an error that message something isn't working, and that until I get dbus system service started, not to reboot. No idea where that is, and it doesn't matter anyway, because if I try to reboot, I get the same error, and the desktop locks up. 

Probably ought to maybe go back to recovery, type

chown root:root /usr/bin/sudo
chmod 4111 /usr/bin/sudo

startx


and when I get to the desktop, ctrl+alt+backspace or F1? Would that not bring me to a log in screen again, and maybe then I'd have sudo working again? 


(this is why I dropped out of ubuntu for so long, because it was always doing something totally unexpected, and when you sought answers, it was really hard to find the right answer. that and I was working on something and didn't want to be distracted. Now I'm back and by golly here we go again! I'd lmao but it hurts meh pride a wee bit :) )



FIXED!

Okay here's the deal:

I went into the recovery console (reboot, and chose recovery console in case you didn't catch on to how to do that), and typed 

ls -l usr/bin/sudo 

and the readout looked fine, like this 

```
-rwsr-xr-x 1 root root 93844 2006-05-17 08:41 /usr/bin/sudo
```

but I knew better...


so I put 

chwon root:root /usr/bin/sudo
then
chmod 4755 /usr/bin/sudo

then I typed 

reboot


and I now have sudo again.

---

### Post by DorianScholz on 2007-10-12
I had a similar problem and even after trying your solution I got:
```

$ sudo
sudo: must be setuid root
$ su
setgid: Operation not permitted

```

I had to do one more thing to get sudo and su back:
```

chmod 4755 /bin/su

```
this changed the permissions of su:
```

from
-rwxr-xr-x 1 root root  27140 2006-12-19 21:35 su
to ^here
-rwsr-xr-x 1 root root  27140 2006-12-19 21:35 su

```
see the 'x' vs. the 's'...

hope that helps!
cheers

---

### Post by Pyrollis Ah Firos on 2007-10-13
This is the same error message I got recently. 

It's strange that I got it just now. I was doing my usual business last night and the network was fine and all. Today, I saw that my computer has shut down from a different distro and I tried to boot it back in that distro but the GDM error came up so I decided to go back to my usual distro; Ubuntu 6.06. When I went back in and for some reason the network isn't working right, I can't sudo for anything, and I can't even get some programs (synaptic, network configuration, programs that requires sudo to be executed) to run. I double clicked on one program. It would either not appear at all, or shows up then disappears after a while. The not appear at all part is the most common problem. So far what I did last night was delete some files and I didn't think it would be that harmful to Ubuntu. It was some general files and not of any importance to the Ubuntu kernel. Could it be because I accidentally deleted something critical? I can log in my account but no network, can't do sudo (I keep getting the same message, sudo: must be setuid root) and I have tried the method mentioned above but no luck. I'm not sure if this is important but when I logged in my account in recovery mode, I saw this message, "-bash: no job control in this shell". I'm not sure if I'm supposed to have job control or is it just the default message? Also, when I tried to go from my user account to root, su root, I typed in the password but it said, invalid password, sorry. 

Oh yeah, I also tinkered with the /etc/fstab file to make the usb device from nouser to user so I can automatically have my USB drive mounted when I plug it in. Could it be part of the reason why I'm experiencing this?

---

### Post by fannus on 2007-10-29
I ran into this problem doing the following:

cd /opt
sudo chown -R <username> * .*

I know I've done this before in other linux distros (and I swear on previous versions of ubuntu), but this time it seemed to think that ".*" also includes "."  *and* "..", so it cascaded backwards a directory and then started clobbering all the ownership in /.

Can anyone verify that this is standard behavior, maybe a recent change in bash?  I've done similar things before, like in my home directory, where you have lots of hidden files that start with '.', there really isn't an easy way to wildcard them other than .*

It also sucks that you pretty much have to boot to a livecd to  fix this problem once it happens.  I know, with great power (Unix) comes great responsibility, but it would be cool if things were designed to avoid accidental catastrophic failure..

---

