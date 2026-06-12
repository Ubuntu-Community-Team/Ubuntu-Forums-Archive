---
title: "New Install: why no Firefox above 1.0.2?"
date: 2005-08-25
forum: Desktop Environments
---

### Post by mganguzi on 2005-08-25
I've installed Ubuntu today. Synaptic Package Manager reports:
   It is not possible to upgrade all packages.
     mozilla-firefox
     mozilla-firefox-gnome-support
     smbclient

I have activated all the repositories and double-checked the Unofficial Guide. All other upgrades were fine.

Is there no support for higher versions of these?

---

### Post by essexman on 2005-08-25
[QUOTE=mganguzi]I've installed Ubuntu today. Synaptic Package Manager reports:
   It is not possible to upgrade all packages.
     mozilla-firefox
     mozilla-firefox-gnome-support
     smbclient

I have activated all the repositories and double-checked the Unofficial Guide. All other upgrades were fine.

Is there no support for higher versions of these?[/QUOTE]
I found a few general problems with the 1.02 firefox that comes with 5.04.

Try cut and paste this ```
sudo apt-get upgrade mozilla-firefox --fix-missing
``` and/or ```
sudo apt-get install mozilla-firefox --fix-missing
``` from the command line.  I havn't found how to get synaptic to do this.  Maybe someone else knows?

---

### Post by mganguzi on 2005-08-25
Thank you for the suggestion, but it does not work.
After doing the "upgrade" version of the command, I get these errors:

  Reading package lists... Done
  Building dependency tree... Done
  The following packages have been kept back:
    mozilla-firefox mozilla-firefox-gnome-support smbclient
  0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

---

### Post by cjazz on 2005-08-25
[QUOTE=mganguzi]Thank you for the suggestion, but it does not work.
After doing the "upgrade" version of the command, I get these errors:[/QUOTE]


What happens if you do an "apt-get dist-upgrade"?

---

### Post by ISBB on 2005-08-25
weird cuz when i installed hoary on my laptop after getting it on the internet it popped up and said hey you need to update these packages i believe synaptic automatically did that... and mine updated it for me.. :D

---

### Post by PhilippWollermann on 2005-08-25
Look here: [http://www.ubuntuforums.org/showthread.php?t=59732](http://www.ubuntuforums.org/showthread.php?t=59732)
We have similar problems with the Backports project.. it seems, as if something is broken with the package trees on the mirrors. We haven't found a solution yet. :(

Philipp

---

### Post by essexman on 2005-08-25
[QUOTE=mganguzi]Thank you for the suggestion, but it does not work.
After doing the "upgrade" version of the command, I get these errors:

  Reading package lists... Done
  Building dependency tree... Done
  The following packages have been kept back:
    mozilla-firefox mozilla-firefox-gnome-support smbclient
  0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.[/QUOTE]
Try adding the repositories I have it my sources.list: ```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hoary main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted multiverse universe

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

##Spare Backports
# http://public.planetmirror.com/pub/ubuntu-backports/ hoary-backports main universe multiverse restricted
# http://public.planetmirror.com/pub/ubuntu-backports/ hoary-extras main universe multiverse restricted
```

This works for me. I have removed the 'us' from the URLs and added multiverse and universe to the Updates repository.

This can be done as a cut and past for /etc/apt/sources.list or add them in to synaptic via Settings>Repositories.

I'm using Firefox 1.06 right now.

Cheers

essexman

---

### Post by bionnaki on 2005-08-26
you could always download from mozilla.org
installing is pretty easy.

from [http://www.mozilla.org/products/firefox/releases/](http://www.mozilla.org/products/firefox/releases/)

> 
Linux/GTK2

Extract the tarball and run the installer like so:

tar -xzvf firefox-1.0.installer.tar.gz
cd firefox-installer
./firefox-installer

If you have Nautilus set up to run Executable Text Files you can just double click firefox-installer to run.


---

### Post by bob k on 2005-08-26
Try this script. This will setup the system to the to the current stable. I don't know what you have done to the OS, and the user interface, and since you are on a new install, just reinstall the OS and run this script.
 
[http://www.ubuntuforums.org/showthread.php?t=22646](http://www.ubuntuforums.org/showthread.php?t=22646)

When you go to update the system after the install, you may get an error about firefox and smb, I think it's 5 held back. Not to worry. I think the source and synaptic are out of sync. All of the apps held back are the current run levels

---

### Post by magnusbb on 2005-08-26
I had similar problems with Firefox... until today. The problem was truly that the files from the Backports project conflicted with those from the main source.

**The solution is simply to comment out the Backports section, and then upgrade:** 

```
sudo gedit /etc/apt/sources.list
``` 
Here, comment out the Backports section, and save the file.

Do a:
```
sudo apt-get update
sudo apt-get upgrade
``` 

And then, Firefox will install.

To get to the Backports mirror again, just reverse this process. It will still complain about "packages kept back", but at least, your Firefox should now be 1.0.6, rather than 1.0.2.

---

### Post by nickpaton on 2005-08-26
Can confirm that the fix for me was by and large as per Essexman:

New install - in Knynaptic no Firefox and a few other bits & bobs as per other posts elsewhere.

Updated the repositories but leave out the final two backport lines.

From the command line carry out as per Essex's instructions to first apt-get upgrade then install.

This installed Firefox 1.0.6 fine for me in the right place.

Many thanks Essex - must be an English thing!! :wink:

---

### Post by mganguzi on 2005-08-30
Thank you all for your advice and assistance! I will be trying this quite soon. Pardon my delay in responding. It is often difficult to get a good net connection where I am.

Wish me good luck! Blessings to you all.

---

