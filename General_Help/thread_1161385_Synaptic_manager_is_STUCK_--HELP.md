---
title: "Synaptic manager is STUCK --HELP"
date: 2009-05-16
forum: General Help
---

### Post by The Saint on 2009-05-16
Hi Guys
I was playing around trying to change my desktop appearance whilst following a set of instructions online. Now my synaptic manager is stuck and wont load at all. I keep getting this error message.

[This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I have tried all newbie tricks to fix it but all to no avail. I guess I need professional help now.

Any help please

---

### Post by paradigm2 on 2009-05-16
Please copy and paste (highlight, then right click) the output of:

```

cat /etc/apt/sources.list

```

---

### Post by The Saint on 2009-05-16
> **paradigm2 said:**
> Please copy and paste (highlight, then right click) the output of:

```

cat /etc/apt/sources.list

```

Did that, came up with where I think the mistake is. What do I do now ?

---

### Post by valex on 2009-05-16
You may want to run "apt-get clean". Also try "apt-get -f update". In theory this should empty the cache and resolve any unfinished business. Then try starting Synaptic

---

### Post by The Saint on 2009-05-16
Hi paradigm2,
This is what it comes up with !

Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-proposed main universe restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
eb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy maindeb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
samuel@samuel-laptop:~$ 

waiting for the next move !

---

### Post by paradigm2 on 2009-05-16
> **The Saint said:**
> Did that, came up with where I think the mistake is. What do I do now ?

Well I assume you then edited it with something like:

sudu gedit /etc/apt/sources.list

????


After you have fixed it, then run:

```

sudo apt-get update
sudo apt-get install -f

```

---

### Post by paradigm2 on 2009-05-16
> **The Saint said:**
> Hi paradigm2,
This is what it comes up with !

Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-proposed main universe restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
eb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy maindeb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
samuel@samuel-laptop:~$ 

waiting for the next move !

What are you using?  Hardy, gutsy, or Jaunty?

I guess we should make a backup of this before messing with it more.

```

sudo cp /etc/apt/sources.list /etc/apt/sources.bak.error

```

---

### Post by The Saint on 2009-05-16
Hi Guys
I tried apt get-clean and this is what I got

samuel@samuel-laptop:~$ apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory
samuel@samuel-laptop:~$ 

What next ??? still not working

---

### Post by paradigm2 on 2009-05-16
> **The Saint said:**
> Hi Guys
I tried apt get-clean and this is what I got

samuel@samuel-laptop:~$ apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory
samuel@samuel-laptop:~$ 

What next ??? still not working

Exit out of synaptic or anything else like the update manager, if they are running.  If it still is messed up, reboot and then try it.

---

### Post by The Saint on 2009-05-16
I am running intrepid

---

### Post by Cheesemill on 2009-05-16
Try doing
```
sudo apt-get clean
```
Also if you look at the 3rd line up from the bottom of your sources.list you are missing a d at the start of the line.

Cheesemill

---

### Post by paradigm2 on 2009-05-16
> **The Saint said:**
> I am running intrepid

Wow...it really got messed up then it looks like, but it should be fixable.  Just to help us get this straightened otu and what happened do you have the link to the instructions you were following?

---

### Post by paradigm2 on 2009-05-16
> **Cheesemill said:**
> Try doing
you are missing a d at the start of the line.


Good eye. :)

---

### Post by valex on 2009-05-16
try this

```
sudo rm /var/lib/dpkg/lock
```
```
sudo rm /var/cache/apt/archives/lock
```

---

### Post by The Saint on 2009-05-16
Still no joy

Any help ?

---

### Post by The Saint on 2009-05-16
> **paradigm2 said:**
> Wow...it really got messed up then it looks like, but it should be fixable.  Just to help us get this straightened otu and what happened do you have the link to the instructions you were following?

I have rebooted my computer so many times that I have close it down.
I am trying to google for it again.

---

### Post by The Saint on 2009-05-16
Where has everyone gone ??? Help needed. So far tried all but NADA !

---

### Post by paradigm2 on 2009-05-16
Okay.  Try this:

Note: This should return your "sources.list" back to the default which would be present during a clean install for intrepid (which you indicated is what you have) .

(assuming you backed it up already as asked to)

0. Make sure you are out of synaptic, update manager, etc.
1. Open up a terminal.
2. enter:

```

sudo gedit /etc/apt/sources.list

```

3. Highlight EVERYTHING in that file and delete it.

4. Copy and paste the code below in there instead.

```

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
#deb http://archive.canonical.com/ubuntu intrepid partner
#deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse

```

5. Save it.

6. Make sure you are out of synaptic, update manager, etc.

7. do the following commands:

```

sudo apt-get clean

```

```

sudo apt-get update

```

```

sudo apt-get install -f

```

8. Reboot.

9. Cross fingers.

---

### Post by The Saint on 2009-05-16
Hey paradigm2 !!!!!

You ARE A GENIUS !!!!!! Your mother is a GENIUS !!!!  It worked..... Thanks Dude. You are a SAINT !

---

### Post by paradigm2 on 2009-05-16
> **The Saint said:**
> Hey paradigm2 !!!!!

You ARE A GENIUS !!!!!! Your mother is a GENIUS !!!!  It worked..... Thanks Dude. You are a SAINT !

Whew.  I was holding my breath!

You might want to back up the workign one now before you try to do whatever you were doing. :)

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak.working.default

```

That way if it happens again you can just copy it back. :)

---

### Post by The Saint on 2009-05-16
Thanks. All done !

---

### Post by The Saint on 2009-05-16
Thanks.
All done

The Saint is Back in business...

---

