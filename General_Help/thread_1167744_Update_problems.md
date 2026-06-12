---
title: "Update problems"
date: 2009-05-23
forum: General Help
---

### Post by simes2510 on 2009-05-23
When I try to look for Jaunty updates, I always get the following error message;

Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, Eproblem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'



Help please?

---

### Post by KhurramM on 2009-05-23
are all options uncommented in:

/etc/apt/sources.list

whats the output of:

sudo apt-get --fix-missing

---

### Post by mahboop on 2009-05-25
Hi, 
I have the same problem as well.
Regards

---

### Post by mahboop on 2009-05-25
> **KhurramM said:**
> are all options uncommented in:

/etc/apt/sources.list

I don't know
here's my **sources.list**
```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://sa.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://sa.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://sa.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://sa.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://sa.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://sa.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://sa.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://sa.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://sa.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://sa.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://sa.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://sa.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://sa.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://sa.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse


```

> **KhurramM said:**
> 
whats the output of:

sudo apt-get --fix-missing


this command didn't work for me. I don't know why. It may not be valid
-
waiting for reply...
Regards

---

### Post by Soul-Sing on 2009-05-25
Most user uncomment this line:

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

should be:

  deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
  deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by mahboop on 2009-05-26
Dear friend,
Thanks for replying

> **leoquant said:**
> Most user uncomment this line:

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

should be:

  deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
  deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

I did this exactly and then restarted my system but the problem is still there. I can't update due to the error message (given above).
--
Regards

---

### Post by Soul-Sing on 2009-05-26
I think this will do the trick, but i'am not sure:

```
sudo rm /var/lib/apt/lists/* -vf
```
```
sudo apt-get update
```

---

### Post by mahboop on 2009-05-26
[COLOR="Green"]Thanks my friend (leoquant)
the problem is solved now. 
But [COLOR="DarkRed"]can you explain to me what was the problem and how did you figure out the solution???[/COLOR]

--
Regards[/COLOR]

---

### Post by Dizanbot on 2009-05-26
Thanks! Worked like a charm.

---

### Post by Peter J Cooke on 2009-05-29
> **leoquant said:**
> I think this will do the trick, but i'am not sure:

```
sudo rm /var/lib/apt/lists/* -vf
``````
sudo apt-get update
```

Thank you this tip worked like a charn

very impressed

---

### Post by simes2510 on 2009-05-30
Thank you, that's cured my problems!

I really believe in the linux concept but as a non-geek, I don't find it that user friendly.
Your help has restored a bit of my faith in it. Once again, thanks!

---

### Post by otchie1 on 2009-06-12
The error message told you all you needed to know,

*E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages*

That means there was a corruption in that file called in my case,
*gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages*

*sudo rm -rf /var/lib/apt/lists/**

just removes all files in that directory and

*sudo apt-get update*

gets Ubuntu to re-write them.

Clear? :D

---

### Post by mahboop on 2009-06-12
[COLOR="Green"]Thanks, 
somehow clear :)
-
Regards[/COLOR]

---

### Post by BoredOutOfMyMind on 2009-06-23
> **otchie1 said:**
> The error message told you all you needed to know,

*E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages*

That means there was a corruption in that file called in my case,
*gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages*

*sudo rm -rf /var/lib/apt/lists/**

just removes all files in that directory and

*sudo apt-get update*

gets Ubuntu to re-write them.

Clear? :D

Ursa-Major:~$ sudo apt-get update
E: Lists directory /var/lib/apt/lists/partial is missing.

:confused:

---

### Post by Soul-Sing on 2009-06-23
> **BoredOutOfMyMind said:**
> Ursa-Major:~$ sudo apt-get update
E: Lists directory /var/lib/apt/lists/partial is missing.

:confused:
```

sudo mkdir -p /var/lib/apt/lists/partial
```
```
sudo apt-get update
```

---

### Post by BoredOutOfMyMind on 2009-06-23
> **leoquant said:**
> ```

sudo mkdir -p /var/lib/apt/lists/partial
```
```
sudo apt-get update
```

Still no access to Repositories in Synaptic or System>Administration>Software Sources

:(

---

### Post by JayKay3000 on 2009-08-08
That code solved my first ubuntu failure. Had same prob, corrupt package updating and that worked a trick. Thanks for the otchie1 for telling uss how it works too.

---

