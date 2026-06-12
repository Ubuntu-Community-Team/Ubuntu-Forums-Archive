---
title: "Absolutelz Positivelz Stumped With Compiz"
date: 2007-06-22
forum: Desktop Effects &amp; Customization
---

### Post by rivera151 on 2007-06-22
I tried to upgrade Compiz unsuccessfully.  After trying to go back to mz previous )default= compiz install (from ubuntu repos) I have been most unsuccessfull.  Please help.  I reallyz want to get my desktop effects back.  Compiz forums were no help.  Can you help me get my Compiz back?

---

### Post by rivera151 on 2007-06-23
C'mon guys, I'm just trying to get back at my original settings.  No compiz upgrades or beryl, or even compiz fusion.  Just plain old Feisty default compiz.  I think my problem started when I decided to upgrade Compiz, and decided that before try to install new Compiz versions, I would remove (through Synaptic) anything that had to do with compiz.  After not being able to install, I decided to reinstall default compiz, but I haven't been able to do so.  Thank you.

---

### Post by zero244 on 2007-06-23
So is your computer booting into plain ole Gnome?
Have you gone into Synaptic and search for compiz to make sure nothing is still installed.
If nothing shows as installed can you use Synaptic to install the compiz core.
You may have to take out the deb lines from your sources list that are pointing to compiz-fusion.

gksu gedit /etc/apt/sources.list

Take a look and see whats showing.

---

### Post by rivera151 on 2007-06-23
Thank you for responding, I was beginning to get anxious :D.

I did try uninstalling everything, and simply leaving all Ubuntu repos, and then reinstalling.  No luck.  Here's my sources list:

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://pr.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://pr.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ feisty-security universe
deb http://archive.ubuntu.com/ubuntu/ feisty-security multiverse
# deb http://www.janvitus.netsons.org/repository/ Gwenhole
# deb http://ubuntu.beryl-project.org/ feisty main #Beryl Project Main Repository
# deb http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator
# deb-src http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator
# deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
# deb http://gandalfn.club.fr/ubuntu feisty motu
# deb http://download.tuxfamily.org/3v1deb feisty eyecandy
# deb http://download.tuxfamily.org/3v1deb feisty main
# deb http://ubuntu.moshen.de/ feisty release

```

Please don't give up!  I'm a patient debugger.

[EDIT]
BTW, haven't tried installing Fusion, and probably won't for a while, since Beryl was a little unfriendly in my ATI card.

---

### Post by rivera151 on 2007-06-24
Bump.

There has to be a way of reinstalling my original config without having to reinstall Ubuntu!

---

### Post by pardesi on 2007-06-24
try to force version to old one in the synaptics

---

### Post by rivera151 on 2007-06-24
Sorry to dissapoint, but I already tried that too!

One thing to notice though, is that the version I see through Synaptic (and have reinstalled several times) is "1:0.3.6-ubuntu13", but the command "compiz --version" shows "0.4.0".  Can someone confirm or deny this is the right Ubuntu-Feisty default version?

---

### Post by andrewsomething on 2007-06-24
> **rivera151 said:**
> Sorry to dissapoint, but I already tried that too!

One thing to notice though, is that the version I see through Synaptic (and have reinstalled several times) is "1:0.3.6-ubuntu13", but the command "compiz --version" shows "0.4.0".  Can someone confirm or deny this is the right Ubuntu-Feisty default version?

Try: sudo apt-get ubuntu-desktop

---

### Post by rivera151 on 2007-06-24
I'm going to try that again.

[EDIT] Didn't work, again.  I don't think I can get it back without a reinstall.  I'm going to have to start reading up on creating a home partition, the way this is going.

[EDIT] Could it be dbus?  I think I have something wrong with dbus.  How can I debug dbus issues?

---

### Post by zero244 on 2007-06-24
I havent had to reinstall but 3 times including the install I am using now. What mucked my machine up was similar to your situation. The envy drivers wouldn't install correctly and there was no way I could unring the bell.
I do have a complete backup now so I shouldn't have to reinstall again for a while.
Plus my machine is running just fine with Beryl and XGL.
Which is the only way I could get Beryl to work with my video card and drivers.
I think you might have to do a fresh install.
What I did this last time was create a 10 gig partition for root and a 44 gig for home.
I think thats what most of the long term Linux users do.

I use Ubuntu for most of my computing.
The only thing I use XP for really is gaming, which I dont have any good alternative choice.
XP is a good gaming platform.
I also have XP running in a VM which allows me to use my Audio streaming software without having to reboot into my native XP partition.
The only thing I cant do with XP in a virtual machine is run anything that requires 3D acceleration. Most software seems to work fine, even MS Office.

---

### Post by ivesjd on 2007-06-24
Im running compiz fusion which is compiz version 0.5.1. Just trying to give you some info.

---

### Post by rivera151 on 2007-06-24
I'm not interested in compiz fusion just yet.  Too new, and with my ATI card it probably won't work.  I HAD compiz working, beautifully, I'd like to add.  I really can't understand why I can't get it to where it was.  I tried beryl, but it was too unstable on my machine, so I went back to compiz.  I guess I'll have to try Beryl again, to see if its gotten any better.

---

### Post by ivesjd on 2007-06-24
You know that beryl and compiz have merged right? And it is now compiz fusion. And the number I gave you was just for reference. So you would have an idea of what to look for.

---

### Post by kpolice on 2007-06-24
> **rivera151 said:**
> I'm not interested in compiz fusion just yet.  Too new, and with my ATI card it probably won't work.  I HAD compiz working, beautifully, I'd like to add.  I really can't understand why I can't get it to where it was.  I tried beryl, but it was too unstable on my machine, so I went back to compiz.  I guess I'll have to try Beryl again, to see if its gotten any better.

Looks like you don't understand what Compiz Fusion is,

Fusion is just some Beryl plugins + new extras and this runs over Compiz, the same that comes with Ubuntu but newer.

Don't install the *fusion packages if you only want Compiz and the core plugins.

---

### Post by rivera151 on 2007-06-24
All right, all right.  I'll try the new stuff, but I suspect something more fundamental is broken, because I've tried to get the configuration that did work with the version that did work, and it doesn't.  But I'll try it.

[EDIT]
Here's the same error I've been getting, and I think is where the problem has been the whole time.

```

ricardo@chupalaptop:~$ sudo apt-get install compiz  # compiz-gnome 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator but it is not installable
E: Broken packages
ricardo@chupalaptop:~$

```

If somebody has any clue on how to fix this bug, don't hold out!

---

### Post by ivesjd on 2007-06-24
[http://ubuntuforums.org/showthread.php?t=481615&highlight=compiz+fusion](http://ubuntuforums.org/showthread.php?t=481615&highlight=compiz+fusion) 
Try that guide. It worked for me. You will just want to not do the step down towards the bottom where it says to install the compiz fusion plugins. Or maybe not, you might like them.

---

### Post by rivera151 on 2007-06-24
Same exact steps I tried.  No luck.  This is definitely a bug, I'm gonna have to file.

Thank god the compiz site is back up.

---

### Post by kpolice on 2007-06-24
If you are going to report it then report it to Ubuntu's launchpad not to Compiz because it is not a problem with it but with your packages and they don't do any packaging.

BTW, are you using 32 or 64 bit Ubuntu?

---

### Post by rivera151 on 2007-06-24
64 bit.  I have tried upgrading to compiled binaries from other repos, but I still get that dependency glitch.  So there is something up with the dependencies.

[EDIT] Also, I don't have a /usr/bin/compiz shell script.  I read from the compiz site that thsi should be on there somewhere, but I don't have it.

---

### Post by kpolice on 2007-06-25
Treviño's repository didn't have 64bit packages the last time I checked so maybe that's the problem.

---

### Post by ivesjd on 2007-06-25
Compiz Fusion doesn't run on 64bit from what I've read.

---

### Post by rivera151 on 2007-06-25
Just to clarify once more:  I'm not trying to run Fusion, just Compiz.  Compiz runs on 64 bit; I was running it fine before I tried to "upgrade" it.  I'm trying to compile from source now using git+make; I can't remember if I was successful last night; I'm gonna try again today when I get home, but as far as I can remember, I wasn't able to.  There is definitely something wrong with the compiz-decorator package.

Does somebody know what could make a package "not installable"?

---

### Post by andrewsomething on 2007-06-25
Something could have happened so that the package was only partially installed and is now broken, blocking you from reinstalling it.

Try running:

sudo apt-get -f install

That will will attempt to correct a system with broken dependencies.

---

### Post by ivesjd on 2007-06-25
Well I guess, if you really want to get back to the default compiz, you could reinstall ubuntu. That would work.

---

### Post by rivera151 on 2007-06-25
I think that's what all this is really adding up to.  I'd like to thank all of you who showed interest and patience in helping me try to debug this problem.  Let's keep up the good work in this Ubuntu community.  If I happen to have a breakthrough before reinstalling Ubuntu, I'll post.  Cheers!

---

### Post by rivera151 on 2007-06-25
Ha!  I think I'm getting somewhere.

I will not try to repeat what I have read, its a little complicated, but to make a long story short, I think my problem has to do with /usr/lib/libGL.so* files and links.  I'm gonna try some stuff.

Here's some links, if you're interested.

[http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#GLX_EXT_texture_from_pixmap_is_missing](http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#GLX_EXT_texture_from_pixmap_is_missing)
[http://ubuntuforums.org/showthread.php?t=131267&page=20#post745383](http://ubuntuforums.org/showthread.php?t=131267&page=20#post745383)
[http://ubuntuforums.org/showthread.php?t=315869&page=4](http://ubuntuforums.org/showthread.php?t=315869&page=4)

I'll update on my experiments when I have some data, for those of you that are having a similar problem.

---

### Post by sertmann on 2007-07-01
I got it working on 64bit...

1) apt-get remove --purge,  all packages related to compiz and beryl, or do a search in synaptic and select 'completely remove' to all packages you find.
2) Go to your home folder, type ctrl+h and remove any dirs related to beryl and compiz - .beryl* and .compiz*
3) Install Janvitus public key: 
> gpg --keyserver hkp://keyserver.ubuntu.com:11371/ --recv-keys 2C4C84CC && gpg --export --armor 2C4C84CC | sudo apt-key add -
4) Get Janvitus packaged in your respositories
> ## uPure64 Repository (Experimental)
deb [http://janvitus.interfree.it/ubuntu/](http://janvitus.interfree.it/ubuntu/) feisty-upure64 experimental-amd64
deb-src [http://janvitus.interfree.it/ubuntu/](http://janvitus.interfree.it/ubuntu/) feisty-upure64 experimental-amd64
5) Install compiz, compiz-fusion* and compiz-gnome - packages
6) run the command
> compiz --replace

1 and 2nd steps are quite crutial, as compiz segfaulted on me, until i did this...

---

### Post by jymboche on 2007-07-01
i was (am) also having the compiz-decorator dependency error... i just tried the upure64 repository you just listed but am still getting the error. I don't really understand how the package is still broken after ive purged/removed ever instance of compiz i can find

anyone know how to fix the broken dependency? or maybe possible to install compiz-decorator from source to fix the problem?

---

### Post by jymboche on 2007-07-02
Fixed.....
thanks for posting the repos for 64bit...
i had to do a fresh install :( but it did work... also installed compizconfig settings manager...
now just to get my desktop back to its beautiful osx looking style!

---

### Post by f1uxam on 2007-07-05
I had to do four complete, fresh installs.  But, it looks awesome with nVidia's June 8 driver in my core2 duo Vaio notebook.
But, getting the thing started is a PITA, with me having to load Beryl Manager to change and reload decorators and window managers so as to get back the disappearing toolbar and impose my favorite Emerald theme.
Is there a better and newer amd64 Beryl Manager in some repository? Trevino's description of a loading wrapper seems too complex for me.

---

