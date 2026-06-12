---
title: "How do I install flash player?"
date: 2005-10-20
forum: Desktop Environments
---

### Post by 0sfensterheim on 2005-10-20
How do I install flash player

Thanks Sam:oops: ](*,) ](*,)

---

### Post by leaber on 2005-10-20
you have to... 

*sudo apt-get install flashplayer-mozilla*

you must first enable universe and multiverse repos...

more info. 
[http://ubuntuguide.org/#flash-mozilla]("http://ubuntuguide.org/#flash-mozilla")

---

### Post by WimVriend on 2005-10-20
[QUOTE=0sfensterheim]How do I install flash player

Thanks Sam:oops: ](*,) ](*,)[/QUOTE]

In a terminal you do
sudo gedit /etc/apt/sources.list

remove the # at the beginning of the lines, from the repositories and save the sources.list

Go to synaptic, upgrade the list and search for flash and install it.

Good luck

---

### Post by Efwis on 2005-10-20
[QUOTE=leaber]you have to... 

*sudo apt-get install flashplayer-mozilla*

you must first enable universe and multiverse repos...

more info. 
[http://ubuntuguide.org/#flash-mozilla]("http://ubuntuguide.org/#flash-mozilla")[/QUOTE]
thats for 5.04 Hoary Hedgehog, those backports and repos are won't work for Breezy...

---

### Post by dave9191 on 2005-10-20
When I visited a page that needed flash, firefox displayed that nice bar accross the top of the page and told me I need a plugin. I clicked on it and told it to install flash player and it did it for me. 

Dave

---

### Post by repawn on 2005-10-21
Ok - I may seem to be plugging a site - but I found this tool useful.

EasyUbuntu
[http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23]("http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23")
It is a small download that installs most video-music codecs, major firefox plug-ins (flash, java,etc) additionally it installs a tool to turn the numlock on at boot.  I am a total noob in linux (net admin in the windows world) and I found this very nice.

I extracted it to the /tmp directory and then you just have to click easyubuntu and run it in terminal (should prompt for password).  Hope this helps.

Chris

---

### Post by lo_mein_dreams on 2005-10-22
[QUOTE=Efwis]thats for 5.04 Hoary Hedgehog, those backports and repos are won't work for Breezy...[/QUOTE]

I'm new... where would I find this for Breezy?

---

### Post by Efwis on 2005-10-22
there are no backports available for Breezy yet. However for the most important factors of updating Breezy do the following.

click on applications>>accesories>>terminal then 
type or copy & paste the following code
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

before continuing it will ask for your password. after you enter your password type the following in the terminal.

```

sudo gedit /etc/apt/sources.list
```

this will open text editor with the permissions to re-write the sources.list file. then replace whats in there with the following information.

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


# deb-src http://dk.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://dk.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://dk.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
# deb-src http://dk.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://dk.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://dk.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe main restricted multiverse
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```
after doing that go back to terminal and type the following
```

sudo apt-get update
```

it will probably be a while before you can find the starter guide for Breezy, until it comes out just look for similar questions to the ones you have here in the forums.

---

### Post by cjazz on 2005-10-23
[QUOTE=Efwis]thats for 5.04 Hoary Hedgehog, those backports and repos are won't work for Breezy...[/QUOTE]


Flashplayer-mozilla is in Breezy multiverse ... I just checked.

---

### Post by Efwis on 2005-10-23
I didn't say that it wasn't in the repos, I was pointing out that the link that was given  is for Hoary, not Breezy. and that version of sources.list shown in that link wouldn't work for Breezy.

---

### Post by cjazz on 2005-10-23
[QUOTE=Efwis]I didn't say that it wasn't in the repos, I was pointing out that the link that was given  is for Hoary, not Breezy. and that version of sources.list shown in that link wouldn't work for Breezy.[/QUOTE]

And of course you're correct. I didn't mean to imply otherwise. I just wanted people to know it was avilable. No offense.

---

### Post by Efwis on 2005-10-24
none taken

---

