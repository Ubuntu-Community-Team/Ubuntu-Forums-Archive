---
title: "I think i really screwed something up"
date: 2009-04-24
forum: General Help
---

### Post by baz8771 on 2009-04-24
I was trying to get wine to install with the "sudo apt-get install wine" command and i couldnt connect to us.archive.ubuntu.com  because the connection would time out every time.  So i went and messed around with "sudo gedit /etc/apt/sources.list" and i think i really screwed something up because everytime i try and download wine again I get this in the terminal... "bret@bret-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wine
bret@bret-desktop:~$ "

What did I do, and what can I do to fix it? :confused:  Im a huuuuuuuuuuge noob at ubuntu, and im on jaunty btw.  Please try and be very specific and simple with the answers cause im just kinda dipping my toes in the water here with ubuntu.  Thanks.

---

### Post by Monotoko on 2009-04-24
paste the output of

```
gedit /etc/apt/sources.list
```

and we will have a look :)

---

### Post by baz8771 on 2009-04-24
I know i really screwed it up now... cause this is all thats in that file "deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"" :P  and how do you get those "code" boxes?   also, is us.archive.ubuntu.com down for anybody else?

---

### Post by Monotoko on 2009-04-24
These tags, also if your in the advance editor theres a little hash button above the textbox
> ```

```

And if you paste the following into your /etc/apt/sources.list it should work again

```


deb http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
```

---

### Post by baz8771 on 2009-04-24
Now when i pasted all of that into the file and try to save it, it's telling me that I dont have permission to save this file when Im the only user on this computer... Any ideas?

---

### Post by paradigm2 on 2009-04-24
> **baz8771 said:**
> I know i really screwed it up now... cause this is all thats in that file "deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"" :P  and how do you get those "code" boxes?   also, is us.archive.ubuntu.com down for anybody else?

The advice Monotoko gave you seems correct.

For the code boxes:



[c*o*d*e]
The text inside goes here
[/c*o*d*e]



Do what is in the above but remove the *'s. It is UBB code: [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

---

### Post by Monotoko on 2009-04-24
Why did the boxes not come up on mine -.-

Anyways, you need to do it as root

```
sudo gedit /etc/apt/sources.list
```

---

### Post by nyk on 2009-04-24
You will want to open the file as the super user (administrative privileges) to write your changes.
```

gksudo gedit /etc/apt/sources.list

```

---

### Post by baz8771 on 2009-04-24
oh lol, noobie me D:  So... I fixed that, but i get the same results in the terminal.  
```
bret@bret-desktop:~$ sudo apt-get install amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package amarok
bret@bret-desktop:~$ 
```

---

### Post by Monotoko on 2009-04-24
Not at all, unless its asked, you wont learn :)

---

### Post by paradigm2 on 2009-04-24
```

sudo gedit /etc/apt/sources.list

```

And save it after entering in what you were given to put in.

---

### Post by baz8771 on 2009-04-24
OK, im still having the previous problem, but now ill heap another question on you guys.  When i go and try to use the package manager, i cant install any packages and in big red letters it says "Error: dependency is not satisfiable: libcurl3" and the "install packages" button is grayed out.

---

### Post by Monotoko on 2009-04-24
hmmm, try

```
sudo apt-get install libcurl3
```

---

### Post by baz8771 on 2009-04-24
> **Monotoko said:**
> hmmm, try

```
sudo apt-get install libcurl3
```


I get the same result as when i try and install wine or amarok or anything from the terminal.

```
bret@bret-desktop:~$ sudo apt-get install libcurl3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libcurl3
```

I think that i just really messed it up bad, i might just clean install it.....

---

### Post by Monotoko on 2009-04-24
What a pain in the ****

Right, you can attempt to use this site: [http://cygwin.com/packages/libcurl3/](http://cygwin.com/packages/libcurl3/)

It has the libcurl 3 packages, but as for which one you should use and how to install, im not sure im afraid.

You could make a new topic asking, but im afraid this as far as i can help you.

---

### Post by baz8771 on 2009-04-24
yeah... im just going to clean install :P probably 8.10 actually... let 9.04 mature a little.

---

### Post by paradigm2 on 2009-04-24
> **baz8771 said:**
> yeah... im just going to clean install :P probably 8.10 actually... let 9.04 mature a little.

Your initial problem with 9.04 might have just been related to the repository servers getting hammered (at least until you or something else edited your sources.list to remove everything but the wine repository).  If i were you I would just install it and wait until tomorrow or late tonight  to update it or add any packages.

9.04 is actually pretty good but it does  have some glitches, yes.

You weren't trying ext4 were you?  If so, that's risky.  ext3 is much safer now.

---

### Post by baz8771 on 2009-04-24
Yeah, I figured that the servers are getting molested right now... :-/  Looks like ill just wait till later tonight cause I just clean installed and am still having the same problems.  Thanks a lot guys, I really appreciate it :D

---

### Post by paradigm2 on 2009-04-24
> **baz8771 said:**
> Yeah, I figured that the servers are getting molested right now... :-/  Looks like ill just wait till later tonight cause I just clean installed and am still having the same problems.  Thanks a lot guys, I really appreciate it :D

You're welcome, good luck.

Also check your hashes on the ISO (if you can) just to be sure:

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Also run the CD integrity check and perhaps consider the memtest as well.

When you do the install try to turn the computer off for an hour or so first.  ...Some people have issues installing from CD because the CD drive gets too hot on their hardware and has more errors.  Especially if they:

1. Just burned it from that computer and drive.
2. Ran the cd check.
3. Booted over the liveCD (just to test drive 9.04)
<Here is where you should ideally let it sit for an hour with the power off before installing unless you know your hardware stays cool>
4. finally they are installing it.

^ That CD drive can probably cook eggs by now if it is a laptop with stock cooling! :)

---

