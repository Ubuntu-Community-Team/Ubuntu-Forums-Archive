---
title: "Synaptic and apt-get Error Notices"
date: 2005-11-08
forum: Desktop Environments
---

### Post by Ingla on 2005-11-08
Hello.

When I reload the Synaptic list, I get this:
------------------------------------------------------------------------
[COLOR="Red"]W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>[/COLOR]
-------------------------------------------------------------------------

Apt-get told me to run a command (I'm not sure I remember, but I think it was just a[t-get upgrade) to solve the problem. It didn't.

Also, whenever I try to install something, I get a notice that I have to upgrade k3blibs. However, trying that gives me a list of dependencies which are not installable. So, I just keep getting the message (I uninstalled k3b some time ago)

Does anyone know what either or both of these error notices means and what
can be done?

Thanks.

---

### Post by Remmelas on 2005-11-10
you can use gpg to import the missing key to clear your error if you implicitly trust that key.

sudo gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 437D05B5
sudo gpg --armor --export 437D05B5 | apt-key add -
sudo apt-get update

usually uninstallable dependancies are a result of mixing packages from different distributions, so i'd check your /etc/apt/sources.list and make sure that there aren't any non-debian repositories enables when you are checking for updates.  Usually if i need a package for a different repository, i enable it, apt-get udpate, apt-get install, then disable it again(by commenting out the corresponding line in /etc/apt/sources.list

---

### Post by Ingla on 2005-11-10
Hi.

Thanks for the reply (where do you learn things like that?).

I tried running the commands. Here are the results:

------------------------------------------------------------------------
 [COLOR="Red"]_sudo gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 437D05B5_
Password:
gpg: directory `/home/avi/.gnupg' created
gpg: new configuration file `/home/avi/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/avi/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/avi/.gnupg/secring.gpg' created
gpg: keyring `/home/avi/.gnupg/pubring.gpg' created
gpg: requesting key 437D05B5 from hkp server wwwkeys.eu.pgp.net
gpg: /home/avi/.gnupg/trustdb.gpg: trustdb created
gpg: key 437D05B5: public key "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
avi@Abraham:~$_ sudo gpg --armor --export 437D05B5 | apt-key add -_
gpg: error writing keyring `/etc/apt/trusted.gpg': file write error
gpg: can't open `/etc/apt/secring.gpg'
gpg: error reading `-': file write error
gpg: import from `-' failed: file write error[/COLOR]
--------------------------------------------------------------------
Running apt-get update yielded the same error as previously.

Can you explain what this means?

I don't know whether I should comment out the repository or try further to find a fix because (if i'm reading this right) the repository is  [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release. Don't I need that?

Any idea what's wrong or what to do?

Thanks very much.

---

### Post by rjwood on 2005-11-10
```
sudo gedit /etc/apt/sources.list
``` from a terminal
when the list appears  remove the "us." portion of the line in question only "us." not the entire line. 
save the file and close out of it.
then
```
sudo apt-get update
``` That should do it.

edit: just noticed you are using kubuntu so instead of "gedit", use whatever text editor you have, (maybe kate)
sorry

---

### Post by Ingla on 2005-11-10
That seems to have done it. Thank you very much.

It took a few minutes because there were a couple of repositories answering to that name and apt-get the readout didn't specify. In the end, I took the "us." out of both and everything seems to be working fine.

Do you know what could have caused this? I mean, everything is fine and then, suddenly, the key for a repository disappears or gets corrupted?

I also want to repeat my question: "Where do you learn these commands for getting keys and such?"

By the way, I'm running Ubuntu 5.10 (gedit). I think Kubuntu uses kwrite or kedit or something (never tried it).

Thanks again.

---

### Post by rjwood on 2005-11-10
[quote=Ingla]That seems to have done it. Thank you very much.

It took a few minutes because there were a couple of repositories answering to that name and apt-get the readout didn't specify. In the end, I took the "us." out of both and everything seems to be working fine.

Do you know what could have caused this? I mean, everything is fine and then, suddenly, the key for a repository disappears or gets corrupted?

I also want to repeat my question: "Where do you learn these commands for getting keys and such?"

By the way, I'm running Ubuntu 5.10 (gedit). I think Kubuntu uses kwrite or kedit or something (never tried it).

Thanks again.[/quote]

It seems the country designations (us.) doesn't matter any more. although They re-appeared on me once out of nowhere--so keep an eye out.

Just hanging around these forums and learning a couple of things has taught me alot. I really don't know much but it's alot more than I knew a month ago.
enjoy and good luck:KS

---

### Post by seatea on 2005-11-10
I have been getting  the  same  error  message for  a couple  of days. I  was told in another  posting  that  this  was a problem  with the  repository and  to just ignore  it until it gets fixed. Now, I'm not sure what to do. It  seems  I am  always  wondering if  I have  somehow messed up(or is  it "broken"?) my sources.list file. I had  read a suggestion in the *Debian Gnu/Linux 3.1 Bible* reference book  that the  repository could be reconfigured by removing /etc/apt/sources.list and then running apt-setup. Would this be ok to do in Ubuntu to assure that you have a good sources.list file?

---

### Post by rjwood on 2005-11-10
here is mine just copy and paste into your sources.list file

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted



## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted  
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

then
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by seatea on 2005-11-10
I am using the ppc version of Ubuntu Breezy Badger 5.10. I have wondered how my repository differs, if at all, from the i386 version. I have enabled all the  backports, mirrors, etc. through the settings in Synaptic. Here is what I ended up with.

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## Security Updates
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

## Hoary Extras (October 16 2005: Breezy Extras are not curently available)
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

## Skype (October 16 2005: Broken)
## deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
 
I have no plans to use Skype, but since it is commented out, I presume it doesn't matter if it is there? I did the upgrade to Breezy from Hoary over the internet. Maybe that wasn't a good choice, but since my system was fresh it seemed like the best time to do that. Should I copy your sources.list from below the first line or do I really need to do anything? For the record, this is only the third week I have used a Linux system of any type.

---

