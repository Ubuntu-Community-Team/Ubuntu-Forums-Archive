---
title: "Switch from GNOME to KDE?"
date: 2007-02-16
forum: Desktop Environments
---

### Post by rkrug on 2007-02-16
I'm just wondering, is it possible to switch from gnome to KDE without making a live CD and installing Kubuntu?

I'm running Ubuntu Edgy.

---

### Post by old_geekster on 2007-02-16
> **rkrug said:**
> I'm just wondering, is it possible to switch from gnome to KDE without making a live CD and installing Kubuntu?

I'm running Ubuntu Edgy.
Yes, it is truly easy:  "sudo apt-get install kde", without the quotes, from the "Terminal".

You can also go to "Synaptic" (System/Administration/Synaptic Package Manager) and search for kde and install it from there.

Once you have done this, you must Log-out,/Log-in/click "Sessions" and chose KDE.  It will allow you to change the desktop for that one time or change it permanently.

I did this and it worked perfectly.

---

### Post by rkrug on 2007-02-16
thanks! :biggrin:

---

### Post by kurgan78 on 2007-02-16
I think it's actually faster and easier to use "sudo apt-get install kubuntu-desktop".. it should load all of the programs that come loaded by default in Kubuntu.

---

### Post by rkrug on 2007-02-17
I've also been trying to install Xfce. I've tried installing through the terminal and package manager, but once I try to log in using Xfce all it shows is my background and nothing else.

I'm currently running KDE (having removed gnome) and I'd really like to get Xfce working as well.

---

### Post by WhiteStool on 2007-02-17
sudo apt-get install xubuntu-desktop

That will install xfce and apps that go well with it.

---

### Post by ubuntu27 on 2007-02-17
> **rkrug said:**
> I'm just wondering, is it possible to switch from gnome to KDE without making a live CD and installing Kubuntu?

I'm running Ubuntu Edgy.

Here is a link on How to install KDE

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Also, I will recommend you to read the following:

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by rkrug on 2007-02-17
> **WhiteStool said:**
> sudo apt-get install xubuntu-desktop

That will install xfce and apps that go well with it.

I've already tried that, and it didn't work. Neither did installing through the package manager, nor did this work:

```
 sudo aptitude update && sudo aptitude install xubuntu-desktop 
```

---

### Post by rkrug on 2007-02-18
bump :oops:

---

### Post by ubuntu27 on 2007-02-18
> **rkrug said:**
> I've already tried that, and it didn't work. Neither did installing through the package manager, nor did this work:

```
 sudo aptitude update && sudo aptitude install xubuntu-desktop 
```



First, it is better to create a new thread when there is a new problem. 
Since the original intention for this thread was to answer the question whatever or not it was possible to switch from GNOME to KDE. Now that it has been answered there is no need to continue this thread.

People who browse around the forums looking for threads to answer questions are more likely to take a look at those new threads in which it has fewer replies. 

So, I recommend you to create a new thread for this problem. 

Since the original intention for this thread was to answer the question whatever or not it was possible to switch from GNOME to KDE. Now that it has been answered there is no need to continue this thread. :)

***********************


I am not expert but I will help the best I can


Can you post your source.list content?

```
gedit /etc/apt/sources.list
```


The clue may lie in your source.list

---

### Post by rkrug on 2007-02-18
> Can you post your source.list content?

```

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main
```

---

### Post by ubuntu27 on 2007-02-18
There it is! It was your source.list.

You got Dapper and Edgy repo. in your source.list.
You should only use one, your current version of UBuntu.

By mixing the repo, there is a high chance that the system (the OS) could break. If that happens the only remedy will be to reinstall Ubuntu.


So, do this:

If you are running Ubuntu Edgy Eft, then replace all dappers with "edgy"
If you are running Dapper Drake, then replaces all "edgy" with "dapper"

```
sudo gedit /etc/apt/sources.list
```

make the change, save it.

and then update:
```

sudo aptitude update
```

---

### Post by rkrug on 2007-02-18
hmm, when I try to save the file I get this error:

The document could not be saved, as it was not possible to write to file:///etc/apt/sources.list.
Check that you have write access to this file or that enough disk space is available.

---

### Post by rkrug on 2007-02-18
Oh, stupid me, I just had to sudo it :oops:

thanks

---

### Post by ubuntu27 on 2007-02-18
> **rkrug said:**
> thanks

You're welcome :)

So how is it? Did it solve the problem?


If you need a fresh unchanged source.list
Here is mine :



```
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
# deb http://security.ubuntu.com/ubuntu edgy-security universe
deb http://archive.ubuntu.com/ubuntu/ edgy-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports restricted main multiverse universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```


Comment: 

I don't use third party repos, I only enabled multiverse and Universe.
I am running Ubuntu Edgy Eft (6.10) for the 32bit (i386)
and I reside in USA. :)

---

### Post by rkrug on 2007-02-18
hmm, nope, still just my background when i try to log in with a xfce session. I'll try again with your source.list.

---

### Post by ubuntu27 on 2007-02-19
> **rkrug said:**
> hmm, nope, still just my background when i try to log in with a xfce session. I'll try again with your source.list.

Do you get any error, any message?

Can you give more details about what you see on the screen?
A Screen Shot could be useful.

---

### Post by shrimphead on 2007-02-20
try deleting your xfce config directories (they are hidden folders in your home dir) and then logging in again. chances are whats happened id that xfce is trying to load a bogus configuration each time. If you delete the current config and start it again it will create the default options of a standard xubuntu install

hope this helps

---

### Post by rkrug on 2007-02-20
I actually reinstalled Ubuntu last night and I actually still had problems with Xfce (albeit different ones), so I'm going to stick with GNOME and KDE for now.

Thanks for all th help, though.

---

### Post by mjm1231 on 2007-02-20
> **old_geekster said:**
> Yes, it is truly easy:  "sudo apt-get install kde", without the quotes, from the "Terminal".

You can also go to "Synaptic" (System/Administration/Synaptic Package Manager) and search for kde and install it from there.

Once you have done this, you must Log-out,/Log-in/click "Sessions" and chose KDE.  It will allow you to change the desktop for that one time or change it permanently.

I did this and it worked perfectly. While I have no fear of using the terminal command to install KDE, I'd like to try it using synaptic. However, searching kde gives the full list of various kde packages (kdebluetooth, kfind, etc.) I can't find any one thing to select to get the same effect as 'apt-get install kde'. How exactly would this be done using synaptic? I plan on installing xfce also and trying out all three.

---

### Post by mjm1231 on 2007-02-20
Of course, immediately after hitting submit I found the selection for plain old "kde" in the list. doh.

---

### Post by infinitelink on 2007-02-22
I'm trying to install KDE into Ubuntu using 

sudo apt-get install kde

but then I get the following:

Reading package lists... Done
Building dependency tree... Done
Package kde is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kde has no installation candidate

Can anybody tell me what to do?

B

---

### Post by ubuntu27 on 2007-02-24
> **infinitelink said:**
> I'm trying to install KDE into Ubuntu using 

sudo apt-get install kde

but then I get the following:

Reading package lists... Done
Building dependency tree... Done
Package kde is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kde has no installation candidate

Can anybody tell me what to do?

B

Try:

```
sudo aptitude update
```

```
sudo aptitude install kubuntu-desktop
```

---

### Post by aysiu on 2007-02-24
What does your /etc/apt/sources.list look like?

---

