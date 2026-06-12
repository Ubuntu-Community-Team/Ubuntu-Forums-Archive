---
title: "GNOME Shell is quite nice"
date: 2009-09-18
forum: Desktop Environments
---

### Post by ardchoille42 on 2009-09-18
I don't know how many of you have used GNOME Shell, but recently installed it and was highly impressed with it. I installed it on my Ubuntu 9.04 system and it runs great.

I wrote a short review (with screenshots) of it [here]("http://ardchoille42.blogspot.com/2009/09/review-gnome-shell-in-ubuntu-904.html").

I don't know how long GNOME Shell has been around but I'm hoping to see it as the default environment i a future version of GNOME.

How many others have used GNOME Shell? What were your thoughts?

---

### Post by theZoid on 2009-09-18
This is the kind of thing that peaks my interest....thanks for the information as I hadn't heard of it (I don't think, memory is slipping ha ha)

BTW, have a link to the turrican theme?

---

### Post by ardchoille42 on 2009-09-18
Yeah, I was intrigued by it too. The theme that  you see on those screenshots is made up of the Turrican GTK2 theme and the New Wave metacity theme, I didn't like the metacity theme provided by Turrican. You can find the New Wave theme in current Jaunty and probably in Karmic too. Information (with download link) about the Turrican theme can be found [here]("https://wiki.ubuntu.com/Artwork/Incoming/Karmic/Turrican?highlight=(Turrican)").

---

### Post by breakbread on 2009-09-21
I'm actually trying to install this now, on my eeePC.

Problem is:

```
ryan@ryan-linux:~$ sudo bash gnome-shell-build-setup.sh
Checking out jhbuild into /home/ryan/Source/jhbuild ... done
Installing jhbuild...
Writing ~/.jhbuildrc ... done
PATH does not contain /home/ryan/bin, it is recommended that you add that.

Please run 'sudo apt-get install libwnck-dev ' before building gnome-shell.

Done.
```

Then, if I try to install libwnck-dev:

```
ryan@ryan-linux:~$ sudo apt-get install libwnck-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libwnck-dev: Depends: libstartup-notification0-dev (>= 0.7-1) but it is not going to be installed
E: Broken packages

```

---

### Post by theZoid on 2009-09-21
> **breakbread said:**
> I'm actually trying to install this now, on my eeePC.

Problem is:

```
ryan@ryan-linux:~$ sudo bash gnome-shell-build-setup.sh
Checking out jhbuild into /home/ryan/Source/jhbuild ... done
Installing jhbuild...
Writing ~/.jhbuildrc ... done
PATH does not contain /home/ryan/bin, it is recommended that you add that.

Please run 'sudo apt-get install libwnck-dev ' before building gnome-shell.

Done.
```

Then, if I try to install libwnck-dev:

```
ryan@ryan-linux:~$ sudo apt-get install libwnck-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libwnck-dev: Depends: libstartup-notification0-dev (>= 0.7-1) but it is not going to be installed
E: Broken packages

```

I just installed libwnck-dev through Synaptic no problem...it added those dependencies you mention plus a couple of others.  Now I'll try the shell.

---

### Post by breakbread on 2009-09-21
> **theZoid said:**
> I just installed libwnck-dev through Synaptic no problem...it added those dependencies you mention plus a couple of others.  Now I'll try the shell.

If I go through package manager I get the same error about libstartup-notification0-dev.  Says it has unresolved dependencies.  Is there a repository I need enabled?

---

### Post by theZoid on 2009-09-21
> **breakbread said:**
> If I go through package manager I get the same error about libstartup-notification0-dev.  Says it has unresolved dependencies.  Is there a repository I need enabled?

hmmmm...turn on all your src repos and try it....mine are all on....this shell is interesting, but for me it still needs a lot of refinement...

---

### Post by breakbread on 2009-09-22
> **theZoid said:**
> hmmmm...turn on all your src repos and try it....mine are all on....this shell is interesting, but for me it still needs a lot of refinement...


All of my repositories are enabled and I still get the error.  I am, however, on eeebuntu right now, so I'm not sure if it has all of the 9.04 repositories of the default Ubuntu installation.

```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse

```

---

### Post by Subban on 2009-09-22
> **ardchoille42 said:**
> How many others have used GNOME Shell? What were your thoughts?

I tried it a few months ago after seeing information about it posted somewhere and seeing a youtube video of it.  I went from very excited to "OMG NOOOO!" in less than 24hrs. I found it very unintuitive and frankly it seemed more like a tech demo looking for a purpose than a useful new Interface approach. I found I had to click more than the traditional menu's and spent longer waiting for animations.

If this is the direction Gnome is going to make its default desktop, then it is going to lose corporate desktops and utterly and completely confuse the backside off people coming from Windows or other desktops. 

I hope I am wrong and that things are coming together with it now because it would be very nice to see Gnome updated, it really would, but I seriously think this is entirely the wrong direction to go,

---

### Post by theZoid on 2009-09-22
> **Subban said:**
> I tried it a few months ago after seeing information about it posted somewhere and seeing a youtube video of it.  I went from very excited to "OMG NOOOO!" in less than 24hrs. I found it very unintuitive and frankly it seemed more like a tech demo looking for a purpose than a useful new Interface approach. I found I had to click more than the traditional menu's and spent longer waiting for animations.

If this is the direction Gnome is going to make its default desktop, then it is going to lose corporate desktops and utterly and completely confuse the backside off people coming from Windows or other desktops. 

I hope I am wrong and that things are coming together with it now because it would be very nice to see Gnome updated, it really would, but I seriously think this is entirely the wrong direction to go,

Pretty much my opinion of it.....anyone know how to uninstall the shell?  :)

---

### Post by theZoid on 2009-10-06
How to uninstall gnome-shell?  thanks and a bump :)

---

### Post by varsamakos on 2009-10-21
> **theZoid said:**
> How to uninstall gnome-shell?  thanks and a bump :)

I also wanted to know.
I tried it and now I want to uninstall all these packages
that made it in my pc. 

Anyone who knows the way ?

---

### Post by keytthom on 2010-05-31
ideas anybody??

i would like to know to.

---

### Post by gakon77 on 2010-05-31
I have followed the link to understand how to install Gnome desktop, an the blog shown was empty.

Is there any comprehensive guide easy to learn how to do it?

Thank you.

---

### Post by gakon77 on 2010-05-31
The link to the mentioned review brings an empty address from a blog.
:confused:

I have followed the link to understand how to install Gnome desktop, an the blog shown was empty.

Is there any comprehensive guide easy to learn how to do it?

Thank you.

> **ardchoille42 said:**
> I don't know how many of you have used GNOME Shell, but recently installed it and was highly impressed with it. I installed it on my Ubuntu 9.04 system and it runs great.

I wrote a short review (with screenshots) of it [here]("http://ardchoille42.blogspot.com/2009/09/review-gnome-shell-in-ubuntu-904.html").

I don't know how long GNOME Shell has been around but I'm hoping to see it as the default environment i a future version of GNOME.

How many others have used GNOME Shell? What were your thoughts?

---

### Post by teachop on 2010-05-31
Tried Gnome Shell twice, and decided it wasn't for me.  My laptop runs so very s-l-o-w with it (3 years old and bottom end when it was new) - not usable.  The machine normally runs lucid fine, even runs compiz fine, but not good with gnome-shell.

Also problems with dual monitors made not possible to test gnome-shell that way on my equipment.

I would be very surprised if it ever becomes a standard.

---

### Post by davrosuk on 2010-06-10
GNOME Shell is so different to anything else so I'm unsurprised at the range of reactions to it. I'll be honest, I love it. I find myself being able to navigate more quickly in it than the existing GNOME 2. Its very early days too, this isn't due until September, so a lot may change/be refined. The machine I put it on is also my HTPC and its solved my screen tearing issues that I had with compiz in flash/BBC iplayer which have frustrated me for years.

---

### Post by ElSlunko on 2010-06-13
There are just a bunch of cool easter eggs when using it. It definitely needs some performance improvements though.

---

### Post by Chancier on 2010-10-08
hi! friends me too faced some problems with gnome-shell, so i decided to remove gnome-shell, To remove gnome shell completely from your desktop run the following command in terminal ... 

sudo aptitude remove gnome-shell

it worked for me ..:P


if u like Gnome shell & need To install Gnome-Shell run the following command in terminal
 
sudo aptitude remove gnome-shell

---

### Post by sendblink23 on 2010-10-08
erased - got confused with post i had read somewhere else

---

### Post by AoSteve on 2010-10-14
I like the shell; but I don't like the physics behind it.  It may be better the longer it goes on; but for now; it's just alright.  I'm much faster with my terminal on my left hand.  LOL

btw...

```
sudo apt-get remove gnome-shell
sudo apt-get remove gnome3-session
```

:)   It's going to be interesting where they go from here.  It's been pushed back until at least March...

---

