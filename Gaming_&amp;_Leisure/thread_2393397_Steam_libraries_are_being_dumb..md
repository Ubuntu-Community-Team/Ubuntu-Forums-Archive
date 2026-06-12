---
title: "Steam libraries are being dumb."
date: 2018-06-03
forum: Gaming &amp; Leisure
---

### Post by iain399 on 2018-06-03
Hi, I am trying to run steam on my Samsung Chromebook that has Xubuntu 16.04.4 on it. I used the .Deb installer to get steam. I did everything and got the actual steam app. But when I click it, it asks for my password then says it is missing the libc.so.6 library. I tried to update it and it just says 0 updated, 0 installed, and 0 not installed.

---

### Post by Perfect Storm on 2018-06-03
Install it from the app store instead, it's  safer.

```
sudo apt remove --purge steam
rm -rf ~/.steam
sudo apt install steam
```

---

### Post by iain399 on 2018-06-03
Thanks, I tried it and it said:Package steam is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, oris only available from another sourceHowever the following packages replace it:  steam-launcher

---

### Post by iain399 on 2018-06-03
Also it says, E: Package 'steam' has no installation candidate

---

### Post by Perfect Storm on 2018-06-04
It should be there, lets have a look at your source list.
```
cat /etc/apt/sources.list
```

It should look like this:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse

```

---

### Post by iain399 on 2018-06-04
It says Code: deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial main restricted universe multiversedeb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial main restricted universe multiversedeb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial-updates main restricted universe multiversedeb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial-updates main restricted universe multiversedeb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial-security main restricted universe multiversedeb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial-security main restricted universe multiverse

---

### Post by Perfect Storm on 2018-06-04
Can you please copy the exactly output of that command all of it (copy/paste) and use these tags to wrap them around [code] [ /code]

---

### Post by iain399 on 2018-06-04
I don't understand. I did copy and paste the exact code. I don't know how to show it like you did. In the gray box.

---

### Post by deadflowr on 2018-06-04
> **iain399 said:**
> I don't understand. I did copy and paste the exact code. I don't know how to show it like you did. In the gray box.

We prefer output from any terminal command be posted using [bbcode]("https://ubuntuforums.org/misc.php?do=bbcode") code tags.
They will retain the proper formatting and make what is posted easy to read and understand.
Otherwise formatting can get lost in the shuffle.

---

### Post by iain399 on 2018-06-04
The code for ```
 cat /etc/apt/sources.list 
``` is ```
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial main restricted universe multiverse
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial main restricted universe multiverse
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial-updates main restricted universe multiverse
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial-updates main restricted universe multiverse
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial-security main restricted universe multiverse
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) xenial-security main restricted universe multiverse
```

---

### Post by iain399 on 2018-06-04
How to I use the bbcode tag.

---

### Post by deadflowr on 2018-06-04
I've clean it up for you.
More on code tags:
[https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")
for future reference.

---

### Post by iain399 on 2018-06-04
Thanks I figured the code tags out.

---

### Post by deadflowr on 2018-06-04
> **iain399 said:**
> Thanks I figured the code tags out.

Good.
Best of luck as I'm out.
I haven't any ideas as to using crouton? I guess (is that right?)

I do know that the ports.ubuntu.com package repositories have their own packages that may or may not fully coincide with what the regular archive.ubuntu.com repositories have.
Whether or not that would make any difference, again, I would not know.

Best of luck though. Truly.

(as I leave it more confusing than I entered it)

---

### Post by iain399 on 2018-06-04
When I input that code it said, 
```
 
deb d http://ports.ubuntu.com/ubuntu-ports/ xenial main restricted universe multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ xenial main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ xenial-updates main restricted universe multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ xenial-updates main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ xenial-security main restricted universe multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ xenial-security main restricted universe multiverse 
```

---

### Post by Perfect Storm on 2018-06-04
Have you edited your source list by any chance?

You might want to add a new source list (including multiverse where steam is)
[https://repogen.simplylinux.ch/](https://repogen.simplylinux.ch/)

you can edit by:
```
sudo nano /etc/apt/sources.list
```
<ctrl>+<o> = save
<ctrl>+<x> = exit

---

### Post by iain399 on 2018-06-04
No, I didn't. Can you explain how to edit the source list in more detail.

---

### Post by Perfect Storm on 2018-06-05
First back up the old list.
```
sudo cp -r /etc/apt/sources.list /etc/apt/sources.list.old
```

Then go to this page and make a new list: [https://repogen.simplylinux.ch/](https://repogen.simplylinux.ch/)

Select your **country**
Select your **ubuntu releases**
Select all **ubuntu branches**
and select all **ubuntu updates**
and select **Ubuntu Partner Repos**

scroll down and hit generate list button.

and now to editing the list:
```
sudo nano  /etc/apt/sources.list
```

now delete the lines in it. Then copy/paste the generated list into it. When done save <ctrl>+<o> and exit <ctrl>+<x>.

then
```
sudo apt update && sudo apt upgrade
sudo apt install steam
```

---

### Post by iain399 on 2018-06-05
When I used the code 
```
 sudo nano  /etc/apt/sources.list 
``` it said ```
 sudo: nano is not a command 
```

---

### Post by Perfect Storm on 2018-06-05
It may be it aren't installed by default on Xubuntu.

```
sudo apt install nano
```

---

### Post by oldrocker99 on 2018-06-06
Nano has been my go-to editor for a decade. Try it! You might love it as much as I do.

---

### Post by deadflowr on 2018-06-06
Quick back question,
I guess I buried my question, (in post # 14)

but is this a crouton install?

Being that it is a chromebook and you have the ports repository,
I would  guess it is.

But an educational guess isn't always correct.

If it is a crouton install, that will help others.

(or if it is a crouton-like install, that can also go long ways to help)

---

### Post by iain399 on 2018-06-06
yes it is a crouton install on an ARM chromebook.

---

### Post by iain399 on 2018-06-06
@Artificial Intelligence, it said ```
 E: Unable to locate package nano 
```

---

### Post by Perfect Storm on 2018-06-07
I don't think steam supports Arm/chromebook.

---

### Post by iain399 on 2018-06-07
WHY tho! I just want steam...

---

### Post by Perfect Storm on 2018-06-08
Sorry I have no experience with ARM. I can't help you there.

---

