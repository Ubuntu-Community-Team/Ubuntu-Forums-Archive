---
title: "[SOLVED] can't install screenlets"
date: 2008-02-23
forum: Desktop Effects &amp; Customization
---

### Post by @tticus on 2008-02-23
hi guys ,
   I've got another problem. I am trying to install screenlets on my ubuntu gutsy 7.10 and after running ```
 sudo apt-get install screenlets
``` it gives me the following error message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
after running the command I get this long error message :


etting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up tex-common (1.9) ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
/usr/bin/ucf: line 351: getopt: command not found
dpkg: error processing tex-common (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of texlive-common:
 texlive-common depends on tex-common (>= 1.4); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-doc-base:
 texlive-doc-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-doc-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
 texlive-fonts-recommended depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base-bin:
 texlive-base-bin depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdvi:
 kdvi depends on texlive-fonts-recommended; however:
  Package texlive-fonts-recommended is not configured yet.
dpkg: error processing kdvi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdegraphics:
 kdegraphics depends on kdvi (>= 4:3.5.8-0ubuntu1); however:
  Package kdvi is not configured yet.
dpkg: error processing kdegraphics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde:
 kde depends on kdegraphics (>= 4:3.4.3); however:
  Package kdegraphics is not configured yet.
dpkg: error processing kde (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1


Could somebody please help me ?
Thanks,
   @tticus

---

### Post by fracturedmorals on 2008-02-23
First off......

TRY running dpkg --configure -a

There's always a way out of these little dpkg issues, and I'm sure that after tweking around a bit you can fix things up. 

Second off....go to [www.getdeb.net](www.getdeb.net) and get the latest screenlets package. It's actually a lot nicer.

:)

---

### Post by @tticus on 2008-02-23
I tried running dpkg --configure -a 
and it gave me that long list of errors, that's why i'm asking :)

---

### Post by fracturedmorals on 2008-02-23
> **@tticus said:**
> I tried running dpkg --configure -a 
and it gave me that long list of errors, that's why i'm asking :)

Whoops.

Either way....it looks like you have a broken package. Were you doing this from Synaptic or from the terminal?

I know that Synaptic has a nice way of handling broken packages if you go over to the "Status" section.

---

### Post by Chipter on 2008-02-23
the screenlets application should be installed by default, check your menues.

If not, try installing it through Synaptic instead of from command line with the apt-get command.

---

### Post by @tticus on 2008-02-24
Thanks for the replies.....I've found some really strange things here.....
I tried to run the Synaptic and it gave me this error message :

```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

than it failed to open. It seems to me that is something serious. I could use the Synapic a few days ago. 
 
By the way I have found screenlets in my K Menu -> Lost & Found
but I can not access the /lost+found folder to see whether there exists a .screenlets folder to copy my screenlets in
I've tried 

```

sudo cd /lost+found

```
but it says 
```

sudo: cd: command not found

```

Any suggestion would be helpful ....

---

### Post by toa on 2008-02-24
> **@tticus said:**
> I tried running dpkg --configure -a 
and it gave me that long list of errors, that's why i'm asking :)

Ubuntu repository is available with the latest version. To use it please add the folowing to your sources.list file for Gutsy: 

deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets

do an update
sudo apt-get update

then install again...

---

### Post by @tticus on 2008-02-24
I added the line to my sources.list and did the update which was interrupted with the same error message :

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by jryprt on 2008-02-24
Try [This](http://ubuntuforums.org/showthread.php?t=687752)

---

### Post by @tticus on 2008-02-25
I solved the problem by installing the ubuntu again. Now the Synaptics work and I could install screenlets easily.

Thanks for the help anyway !

---

