---
title: "Huge and constant package error"
date: 2006-06-22
forum: Desktop Environments
---

### Post by truenemesis on 2006-06-22
Each time, I install Ubuntu 6.06 and I update it. My packages eventually break along with Synaptic Pckg manager. And I get this error.

E: gdm: subprocess post-installation script returned error exit status 2
E: gnome-applets: subprocess post-installation script returned error exit status 2
E: libpango1.0-common: subprocess post-installation script returned error exit status 2
E: linux-image-2.6.15-25-386: subprocess post-installation script returned error exit status 2
E: linux-image-386: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.15-25-386: dependency problems - leaving unconfigured
E: linux-restricted-modules-386: dependency problems - leaving unconfigured
E: linux-386: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured
E: pcmcia-cs: subprocess post-installation script returned error exit status 2

Someone please suggest something.

---

### Post by rowanparker on 2006-06-22
Can you run ```
sudo apt-get install ubuntu-desktop
``` to make sure it is all installed correctly?

---

### Post by truenemesis on 2006-06-22
after doing that command, I get:

```

debconf: Perl may be unconfigured (Can't locate IO/File.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl/5.8/FileHandle.pm line 9.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
Setting up html2text (1.3.2a-3) ...
Can't locate File/Glob.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error processing html2text (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of debhelper:
 debhelper depends on html2text; however:
  Package html2text is not configured yet.
dpkg: error processing debhelper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alien:
 alien depends on debhelper (>= 3); however:
  Package debhelper is not configured yet.
dpkg: error processing alien (--configure):
 dependency problems - leaving unconfigured
Setting up gdm (2.14.9-0ubuntu1) ...
Can't locate POSIX.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 2
Setting up gnome-applets (2.14.2-0ubuntu1) ...
Can't locate POSIX.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing gnome-applets (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libpango1.0-common (1.12.3-0ubuntu1) ...
Can't locate POSIX.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing libpango1.0-common (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-image-2.6.15-25-386 (2.6.15-25.43) ...
Can't locate Cwd.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /var/lib/dpkg/info/linux-image-2.6.15-25-386.postinst line 20.
BEGIN failed--compilation aborted at /var/lib/dpkg/info/linux-image-2.6.15-25-386.postinst line 20.
dpkg: error processing linux-image-2.6.15-25-386 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-386:
 linux-image-386 depends on linux-image-2.6.15-25-386; however:
  Package linux-image-2.6.15-25-386 is not configured yet.
dpkg: error processing linux-image-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.15-25-386:
 linux-restricted-modules-2.6.15-25-386 depends on linux-image-2.6.15-25-386; however:
  Package linux-image-2.6.15-25-386 is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.15-25-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-386: linux-restricted-modules-386 depends on linux-restricted-modules-2.6.15-25-386; however:
  Package linux-restricted-modules-2.6.15-25-386 is not configured yet.
dpkg: error processing linux-restricted-modules-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-386:
 linux-386 depends on linux-image-386; however:
  Package linux-image-386 is not configured yet.
 linux-386 depends on linux-restricted-modules-386; however:
  Package linux-restricted-modules-386 is not configured yet.
dpkg: error processing linux-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gdm; however:
  Package gdm is not configured yet.
 ubuntu-desktop depends on gnome-applets; however:
  Package gnome-applets is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up pcmcia-cs (3.2.8-5.2ubuntu7) ...
Can't locate POSIX.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing pcmcia-cs (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 html2text
 debhelper
 alien
 gdm
 gnome-applets
 libpango1.0-common
 linux-image-2.6.15-25-386
 linux-image-386
 linux-restricted-modules-2.6.15-25-386
 linux-restricted-modules-386
 linux-386
 ubuntu-desktop
 pcmcia-cs
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

anyway, I just wanna be able to fix this problem without an reinstall.

---

### Post by rowanparker on 2006-06-22
Sorry, i'm lost.
Anyone else any ideas?

---

### Post by truenemesis on 2006-06-22
yeah, someone help me here. weird bug. it might be good to find out the problem as more and more people are moving to linux.

---

### Post by truenemesis on 2006-06-23
wow, thanks for the help everyone. Im leaving Ubuntu now. Its too buggy for me. Gonna go back to Windows.

---

### Post by ifokkema on 2006-06-23
[QUOTE=truenemesis]wow, thanks for the help everyone. Im leaving Ubuntu now. Its too buggy for me. Gonna go back to Windows.[/QUOTE]

Wow... giving up fast :)
It starts with complaining about a file perl should have.

Try:
```
sudo dpkg-reconfigure perl-base
sudo apt-get install --reinstall perl-base
sudo dpkg --configure -a
```

---

### Post by truenemesis on 2006-06-23
now i get this

```

BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/sbin/dpkg-reconfigure line 9.
BEGIN failed--compilation aborted at /usr/sbin/dpkg-reconfigure line 9.

```

---

### Post by ifokkema on 2006-06-23
Ok... you've got some broken packages, it seems. These are from debconf.

Try this, then:
```
sudo dpkg --configure perl-base debconf
sudo apt-get install --reinstall perl-base debconf
sudo dpkg --configure -a
```

---

### Post by truenemesis on 2006-06-23
when I run that, I get this:

dpkg: error processing perl-base (--configure):
 package perl-base is already installed and configured
dpkg: error processing debconf (--configure):
 package debconf is already installed and configured
Errors were encountered while processing:
 perl-base
 debconf

---

### Post by ifokkema on 2006-06-23
That's OK, just wanted to be sure they were configured properly. did you try the other two commands? The second command will re-install these two packages, the third will try and configure any unconfigured packages.

---

### Post by truenemesis on 2006-06-23
okay, when i do those apt-get commands, I get errors.
Check out this post
[http://ubuntuforums.org/showthread.php?t=202441](http://ubuntuforums.org/showthread.php?t=202441)

---

### Post by ifokkema on 2006-06-23
[QUOTE=truenemesis]okay, when i do those apt-get commands, I get errors.
Check out this post
[http://ubuntuforums.org/showthread.php?t=202441](http://ubuntuforums.org/showthread.php?t=202441)[/QUOTE]
LOL :D
Was too busy reading and posting that I didn't even notice you and I were discussing two issues at the same time.

OK... so this explains why you've got these problems with all these packages. Please check your drive, as I've described in the other thread. It seems damaged, which is causing all kinds of read errors and such.

---

