---
title: "Installing Firefox 1.0 (using the installer from mozilla.org)"
date: 2005-01-04
forum: General Help
---

### Post by Ruediger on 2005-01-04
I can't seem to install Firefox 1.0 correctly. 

I've done a little research and found out that programs should be placed either under the /usr/local/<application> directory or under the /usr/bin/<application>. The problem is the only way to install in any of these folders is to run the installer as su, since the user has no write permission on it. 

If I install Firefox as root the only way to run it is as root (or it will says that the profile is already in use).

Can anyone give me the right directions?

---

### Post by fng on 2005-01-04
the easiest way for installing firefox 1.0 is getting it from the backports-repository.

Stable Backports Branch (well-tested working software):
URI: [http://ubuntu-bp.sourceforge.net/ubuntu](http://ubuntu-bp.sourceforge.net/ubuntu)
Distribution: warty-backports
Section(s): main universe

sudo apt-get update
sudo apt-get install mozilla-firefox

---

### Post by Ruediger on 2005-01-04
[QUOTE=fng]the easiest way for installing firefox 1.0 is getting it from the backports-repository.

Stable Backports Branch (well-tested working software):
URI: [http://ubuntu-bp.sourceforge.net/ubuntu](http://ubuntu-bp.sourceforge.net/ubuntu)
Distribution: warty-backports
Section(s): main universe

sudo apt-get update
sudo apt-get install mozilla-firefox[/QUOTE]

I didn't know about this repository, thanks for the tip. 

Unfortunatley I need a localized version, which is not available in the repository, hence why I am using the installer.

---

### Post by ow50 on 2005-01-04
I installed firefox as root to /opt/firefox and created a link to the firefox executable in /usr/local/bin. After that i run firefox (not as root) and it works fine.

If firefox says that the profile is already at use, you might already have firefox running. Type "ps -A | grep firefox" at the command line, kill the processes listed and try starting firefox again.

Easiest way is indeed to install from ubuntu-backports, but at least for me some small things such as updating extensions don't work in the backported version. Installing with the official installer will get a better functioning install.

---

### Post by Ruediger on 2005-01-04
[QUOTE=ow50]I installed firefox as root to /opt/firefox and created a link to the firefox executable in /usr/local/bin. After that i run firefox (not as root) and it works fine.

If firefox says that the profile is already at use, you might already have firefox running. Type "ps -A | grep firefox" at the command line, kill the processes listed and try starting firefox again.

Easiest way is indeed to install from ubuntu-backports, but at least for me some small things such as updating extensions don't work in the backported version. Installing with the official installer will get a better functioning install.[/QUOTE]

I've followed your steps, no instance of Firefox was running and still got the same problem... Guess I'll have to stick with the backport release :\

EDIT: I found the problem. After installing the backport release I got the same problem, so I decided to delete the profile folder and now it works, I'll try to install the version from mozilla.org.

---

### Post by wallijonn on 2005-01-04
It was probably an extension. It's easier to just delete the extension folder, clear the cache, etc. than to blow everything away.

---

### Post by pmshoop on 2005-01-05
[QUOTE=Ruediger]I can't seem to install Firefox 1.0 correctly. 

I've done a little research and found out that programs should be placed either under the /usr/local/<application> directory or under the /usr/bin/<application>. The problem is the only way to install in any of these folders is to run the installer as su, since the user has no write permission on it. 

If I install Firefox as root the only way to run it is as root (or it will says that the profile is already in use).

Can anyone give me the right directions?[/QUOTE]

Hey, bring up a root terminal.  Easier than doing 'su' all the time.  Download the file and follow the instructions on their website.  I installed mine in my /home directory.  It works but it wasn't 'integrated' into my desktop like it would have been had I installed it through synaptec.  Actually, I installed firefox, thunderbird, real gold 10 and a few other programs this way.  Its harder but... it can be done.

Paul.

---

