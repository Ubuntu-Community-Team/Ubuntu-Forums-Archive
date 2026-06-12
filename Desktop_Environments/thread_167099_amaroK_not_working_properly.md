---
title: "amaroK not working properly"
date: 2006-04-27
forum: Desktop Environments
---

### Post by Rhapsody on 2006-04-27
So, I'm on Kubuntu Linux, and I want to play some good music. But amaroK won't play MP3s without me helping it.

So I followed the [instructions](http://amarok.kde.org/amarokwiki/index.php/MP3_on_Ubuntu_5.10) the amaroK FAQ pointed to, but that didn't work. So I posted a [topic](http://amarok.kde.org/forum/index.php/topic,11918.0.html) on their forums, where they weren't particularly helpful. So they ended up pointing me back to here ('distro-specific' aparrently, although it can also happen on SuSE, and Redhat/Fedora).

Which leaves me here. Most of my music is MP3, and I can't play those on amaroK right now. I do like amaroK, but being stuck on a loop of my few Ogg Vorbis files is beginning to grate. So can anyone help me get amaroK playing my MP3 files?

---

### Post by gingermark on 2006-04-27
[https://wiki.kubuntu.org/RestrictedFormats](https://wiki.kubuntu.org/RestrictedFormats) should sort you out.
EDIT: If you come across instructions that include the command "sudo gedit" substitute "kdesu kate" instead.

---

### Post by Rhapsody on 2006-04-27
I'd already enabled two lines necessary to add software from the 'universe' repository, the amaroK FAQ seemed convinced this was all that was needed. I've now enabled two more lines necessary to add software from the 'backports' repository. Now when I type in the command that's supposed to get amaroK to play my MP3s, I get a brand new error!

```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.8-mad: Depends: libid3tag0 (>= 0.15.1b) but it is not installable
                    Depends: libmad0 (>= 0.15.1b) but it is not installable
E: Broken packages
```

I take it from this that amaroK still won't play MP3s?

Edit: I should also probably note that I have some AAC files as well, and it'd be handy if I could play those too.

---

### Post by gingermark on 2006-04-28
If you enable all the repositories that are currently disabled it should work. If not, post the contents of your sources.list file located in /etc/apt and we'll take it from there.

---

### Post by Rhapsody on 2006-04-28
Alright.

```
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 


## Uncomment the following two lines to fetch updated software from the network
deb http://gb.archive.ubuntu.com/ubuntu breezy main restricted 
deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted 

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted 
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu breezy universe 
deb-src http://gb.archive.ubuntu.com/ubuntu breezy universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu breezy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted 

deb http://security.ubuntu.com/ubuntu breezy-security universe 
deb-src http://security.ubuntu.com/ubuntu breezy-security universe 
```

All non-comment lines are now enabled, yet I'm still getting the same error.

---

### Post by gingermark on 2006-04-28
That sources.list looks fine for me (although you might want to comment out the CD).

Once you uncommented them, did you do a
```
sudo apt-get update
```
or "Fetch updates" in Adept?

You need to do one of the two so your system knows the packages that are now available to you.

---

### Post by Rhapsody on 2006-04-28
[QUOTE=gingermark]That sources.list looks fine for me (although you might want to comment out the CD).[/QUOTE]
That one was actually uncommented before I started. What does it do?

[QUOTE=gingermark]Once you uncommented them, did you do a
```
sudo apt-get update
```
or "Fetch updates" in Adept?

You need to do one of the two so your system knows the packages that are now available to you.[/QUOTE]
...

I can't believe I forgot to do that. It's working now.

---

