---
title: "Synaptic Package Manager Won't Load"
date: 2006-06-30
forum: Desktop Environments
---

### Post by mmcdonnell on 2006-06-30
Hello.

I have just installed Ubuntu 6.06 Desktop but the Synaptic Package Manager won't load when I click on it.  It looks like it is starting to load for a second then nothing.  I think this is also preventing me from adding any more applications from the app list and also installing the 76 updates that it lists.  When I click install updates, nothing happens.

Is there anything that I can do to fix this?

Thanks

Marcus

---

### Post by kripkenstein on 2006-06-30
To start finding out what the problem is, run synaptic from the command line:

```
sudo synaptic
```

and tell us what error messages you get there.

---

### Post by mmcdonnell on 2006-06-30
Thanks for your reply.

I get the following error:

E: Could not open lock file /root - open (21 is a directory)

---

### Post by kripkenstein on 2006-06-30
Hmm, that isn't good...

To make sure, did you run Synaptic with sudo? And did it not give an error in validating your password?

If that isn't the issue, then let's figure our whether the problem is Synaptic or the backend. Try to run these commands:
```

sudo apt-get update
sudo apt-get upgrade

```

(one after the other). See if you get any error messages, and if so which.

---

### Post by mmcdonnell on 2006-06-30
Hi There,

Yeah I ran the command with sudo in front but don't get any password error.  I ran the commands you suggested and all looks ok but heres what I get:

Fetched 4B in 0s (8B/s)
Reading package lists... Done
alan@alan-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
alan@alan-desktop:~$ sudo synaptic
E: Could not open lock file /root - open (21 Is a directory)
alan@alan-desktop:~$

Thanks,

Marcus

---

### Post by kripkenstein on 2006-06-30
Odd. Now, you say you have 76 updates, that you can't install? Strange, since apt-get reports nothing to update.

Do ```

cat /etc/apt/sources.list

``` - what does that give you?

Assuming this doesn't give us any useful clues, it might be best to just reinstall. I've never seen errors like this. My best guess is that the installation didn't complete successfully.

---

### Post by shrift on 2006-06-30
The problem is that some other application already has a lock on the package management databases. You need to close those applications. You may have synaptic open already, OR you may have aptitude open in a console, OR you may have the dapper system updater running somewhere. 

If you cannot figure out what has the package management files open, simply restart the computer.

---

### Post by mmcdonnell on 2006-06-30
Sorry I was a bit vague in my last post.

I ran the two commands that you advised and the 76 updates installed.  

I tried the synaptic package manager again, but the same story.

Ubuntu is now telling me that there is 4 updates, one of them being linux-image-2.5.15-25-386 which is 21.6m the other 3 are small.

I think this update is being held back.  It won't install even through the terminal.

I ran cat /etc/apt/source.list and I get the following:

#deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
#deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb cdrom:[Ubuntu 6.06_Dapper_Drake_ - Release i386 (20060531)]/ dapper main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricted
deb cdrom:[Ubuntu 6.06_Dapper_Drake_ - Release i386 (20060531)]/ dapper main restricted
deb cdrom:[Ubuntu 6.06_Dapper_Drake_ - Release i386 (20060531)]/ dapper main restricted

Everything else apart from the synaptic package manager is working 100%.  I was just hoping to install some of the educational programs as I'm driving 3 hours tomorrow to give it to a family with kids.

Thanks again for your replies.

---

### Post by lowey23 on 2006-06-30
Your sources.list seems.................ratshit.

Have a look at this site

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

and it will automatically do a new one for you.

You can then update and upgrade and all should be a saucer joy.

Cheers

Lowey

---

### Post by kripkenstein on 2006-07-01
Well, at least apt-get is working. So the problem seems to be synaptic. You can try to reinstall synaptic from the command line,
```
sudo apt-get remove synaptic
```
```
sudo apt-get install synaptic
```
Also, as shrift says, perhaps a restart might help.

Regarding the 'held-back' update, tell us what message apt-get gives you for not installing it

---

### Post by randell6564 on 2006-07-01
[QUOTE=mmcdonnell]Sorry I was a bit vague in my last post.

I ran the two commands that you advised and the 76 updates installed.  

I tried the synaptic package manager again, but the same story.

Ubuntu is now telling me that there is 4 updates, one of them being linux-image-2.5.15-25-386 which is 21.6m the other 3 are small.

I think this update is being held back.  It won't install even through the terminal.

I ran cat /etc/apt/source.list and I get the following:

#deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
#deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb cdrom:[Ubuntu 6.06_Dapper_Drake_ - Release i386 (20060531)]/ dapper main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricted
deb cdrom:[Ubuntu 6.06_Dapper_Drake_ - Release i386 (20060531)]/ dapper main restricted
deb cdrom:[Ubuntu 6.06_Dapper_Drake_ - Release i386 (20060531)]/ dapper main restricted

Everything else apart from the synaptic package manager is working 100%.  I was just hoping to install some of the educational programs as I'm driving 3 hours tomorrow to give it to a family with kids.

Thanks again for your replies.[/QUOTE]


After looking at your sources.list, I noticed that you might have the same problem that I had!

Check out this thread: [http://www.ubuntuforums.org/showthread.php?t=206653](http://www.ubuntuforums.org/showthread.php?t=206653)  read the reply from 'azz'
GOOD LUCK!

---

