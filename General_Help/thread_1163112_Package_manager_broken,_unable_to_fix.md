---
title: "Package manager broken, unable to fix"
date: 2009-05-18
forum: General Help
---

### Post by wookie27 on 2009-05-18
Hello, I am using Linux mint 6 btw and have not received any responses there and I was hoping that someone here would be able to help me.

My problem and what I tried:


So I tried to use the package manager to install some bio-linux tools and the package manager just hangs for hours with this screen:

[INDENT]Setting up bio-linux-genquery (2.2.2-1) ...
Pulling in some needed Perl modules not in Debian


CPAN is the world-wide archive of perl resources. It consists of about
300 sites that all replicate the same contents around the globe. Many
countries have at least one CPAN site already. The resources found on
CPAN are easily accessible with the CPAN.pm module. If you want to use
CPAN.pm, lots of things have to be configured. Fortunately, most of
them can be determined automatically. If you prefer the automatic
configuration, answer 'yes' below.

If you prefer to enter a dialog instead, you can answer 'no' to this
question and I'll let you configure in small steps one thing after the
other. (Note: you can revisit this dialog anytime later by typing 'o
conf init' at the cpan prompt.)
Would you like me to configure as much as possible automatically? [yes][/INDENT]

Since it hanged like this for about 3 hours, I closed the window and attempted to restart package manager.

When I restart linux and try to access package manager I get the error: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I did that, but the same thing happens, it just hangs in terminal with the same screen.

[INDENT]luke@luke-desktop ~ $ sudo dpkg --configure -a
Setting up bio-linux-genquery (2.2.2-1) ...
Pulling in some needed Perl modules not in Debian


CPAN is the world-wide archive of perl resources. It consists of about
300 sites that all replicate the same contents around the globe. Many
countries have at least one CPAN site already. The resources found on
CPAN are easily accessible with the CPAN.pm module. If you want to use
CPAN.pm, lots of things have to be configured. Fortunately, most of
them can be determined automatically. If you prefer the automatic
configuration, answer 'yes' below.

If you prefer to enter a dialog instead, you can answer 'no' to this
question and I'll let you configure in small steps one thing after the
other. (Note: you can revisit this dialog anytime later by typing 'o
conf init' at the cpan prompt.)
Would you like me to configure as much as possible automatically? [yes][/INDENT]

Searching under package manager help I did this:

I then manually deleted the .bin files through root /var/cache/apt and still could not fix the problem.

I can no longer install any packages because I get the error: 
[INDENT]Only one software management tool is allowed to run at the same time
[/INDENT]
even though I just rebooted the computer and didn't try to run anything.

It says please close the other application, but I do not have any other application open.

So then I did the following:
[INDENT]sudo apt-get clean -f
[sudo] password for luke: 
luke@luke-desktop ~ $ sudo apt-get update
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg [189B] 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US 
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg 
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US 
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia Release.gpg 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US 
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release [51.2kB] 
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US 
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg [189B] 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US 
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/main Translation-en_US 
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/upstream Translation-en_US 
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/import Translation-en_US 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages 
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages 
Get:4 [http://envgen.nox.ac.uk](http://envgen.nox.ac.uk) unstable Release.gpg [189B] 
Ign [http://envgen.nox.ac.uk](http://envgen.nox.ac.uk) unstable/bio-linux Translation-en_US 
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release [51.2kB] 
Get:6 [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia Release [7869B] 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages 
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages 
Get:7 [http://envgen.nox.ac.uk](http://envgen.nox.ac.uk) unstable Release [1197B] 
Ign [http://envgen.nox.ac.uk](http://envgen.nox.ac.uk) unstable Release 
Ign [http://envgen.nox.ac.uk](http://envgen.nox.ac.uk) unstable/bio-linux Packages 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages [113kB] 
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/main Packages 
Hit [http://envgen.nox.ac.uk](http://envgen.nox.ac.uk) unstable/bio-linux Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages 
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/upstream Packages 
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages [332kB] 
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/import Packages 
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/main Packages 
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages [3517B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages [50.5kB] 
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages [6729B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages [8436B] 
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages [106kB]
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/upstream Packages 
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages [10.9kB] 
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) felicia/import Packages 
Fetched 742kB in 2s (353kB/s) 
W: GPG error: [http://envgen.nox.ac.uk](http://envgen.nox.ac.uk) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3EC653D3EADA2460
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/INDENT]

But as you can see, it just brings me to the same problem.  

This is really frustrating atm and I do not understand what is going on.  FYI the place that I have my linux machine connected to uses a fixed IP address, not DHCP, so that is not the problem with connecting to some sort of libraries (I am a newb so I don't even know if that makes any sense).

Can someone please help me?

---

### Post by bumanie on 2009-05-18
Not sure if this will help, but try these codes in terminal > sudo apt-get install -f> sudo apt-get update && sudo apt-get upgradeThe first should force the download of any broken packages and the second should install any new/updated packages. Hope it helps.

---

### Post by Yellow Pasque on 2009-05-18
It sounds like you have a stale lock file ( /var/lib/dpkg/lock ) left behind by a package manager program that got interrupted (e.g. apt, synaptic, dpkg).
Remove that lock file and go from there.

---

### Post by wookie27 on 2009-05-18
bumanie

I tried those and i still got the same result:
 sudo apt-get install -f
[sudo] password for luke: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Temujin,  I deleted the file and I still get the error E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

But I do notice that the terminal says that the program I was trying to install is an unstable version.

So I am back at square one.  This is frustrating, but at the same time it is also a good learning experience for me.

---

### Post by wookie27 on 2009-05-18
I tried both of your suggestions again, and now it is updating and doing something, I will keep you posted if this works.  But I am enjoying seeing some progress.  Thank you both!

Even though I get some errors in terminal, I can now open package manager again, thanks!

---

### Post by Yellow Pasque on 2009-05-18
Can you purge that package and then configure?
```
sudo dpkg -P bio-linux-genquery
sudo dpkg --configure -a
```

EDIT: Just saw your post above, only us these commands if you're still having issues.

---

### Post by wookie27 on 2009-05-18
Thanks

I can install things, but at the end I always get an error even though the program does install.  HEre is my latest terminal:

bash: /usr/local/bioinf/config_files/aliasrc: No such file or directory
bash: /usr/local/bioinf/config_files/bioenvrc: No such file or directory
luke@luke-desktop ~ $ sudo dpkg -P bio-linux-genquery
(Reading database ... 147353 files and directories currently installed.)
Removing bio-linux-genquery ...
Purging configuration files for bio-linux-genquery ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing bio-linux-genquery (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 bio-linux-genquery
luke@luke-desktop ~ $ sudo dpkg --configure -a
Setting up linux-headers-2.6.27-7-generic (2.6.27-7.16) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.27-7-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.27-7-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up postgresql-common (90) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing postgresql-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql-8.3:
 postgresql-8.3 depends on postgresql-common (>= 79); however:
  Package postgresql-common is not configured yet.
dpkg: error processing postgresql-8.3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql:
 postgresql depends on postgresql-8.3; however:
  Package postgresql-8.3 is not configured yet.
dpkg: error processing postgresql (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.27-7-generic
 postgresql-common
 postgresql-8.3
 postgresql
luke@luke-desktop ~ $

---

### Post by Yellow Pasque on 2009-05-18
Again, make sure you don't have any other package managers running. If not, post output of:
```
fuser -v /var/cache/debconf/config.dat
```

---

### Post by wookie27 on 2009-05-18
I typed this in but nothing happened

luke@luke-desktop ~ $ fuser -v /var/cache/debconf/config.dat

I can manually open the config.dat file if you would like and paste it here, but there is a lot of text, should I do that?

---

### Post by Yellow Pasque on 2009-05-18
Sorry, you should run the fuser command with sudo.

> I can manually open the config.dat file if you would like and paste it here, but there is a lot of text, should I do that?
I personally wouldn't know what to look for in that file. BTW, if you want to share large amounts of text, use [http://ubuntu.pastebin.com/](http://ubuntu.pastebin.com/)

---

