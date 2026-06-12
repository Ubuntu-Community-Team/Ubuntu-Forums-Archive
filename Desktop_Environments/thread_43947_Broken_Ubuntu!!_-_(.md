---
title: "Broken Ubuntu!! :- ("
date: 2005-06-23
forum: Desktop Environments
---

### Post by super on 2005-06-23
ok so the system is not totally broken, but...

i installed my system way back in the spring or winter and i used a preview release CD to install since Hoary had not yet been released.

Anyways a few days ago i decided to do an apt-get upgrade.

This did not work out too well. Most stuff were ok but ubuntu-base fails to install properly along with postfix, mutt, and postfix-utils.

Now everytime i install something via apt-get it returns errors. It will install the program but the errors are a bit annoying.

Here is the output from apt-get installs.

[FONT=Courier New][COLOR=Red]E: postfix:  subprocess post-installation script returned error exit status 1
E: mutt:  dependency problems - leaving unconfigured
E: postfix-tls:  dependency problems - leaving unconfigured
E: ubuntu-base:  dependency problems - leaving unconfigured[/COLOR][/FONT]

this actually did cause some serious problems for me, after the apt-get upgrade, i was unable to login using GDM because this had screwed up my .Xauthority file. As well i cannot use my wallpaper selector except as root or through sudo.

I don't use postfix or mutt so i was thinking of removing them, but i'm not so sure about ubuntu-base. Is this just a dummy package? can i remove it?

Please advise, any help would be appreciated!
Thanks!!

---

### Post by DJ_Max on 2005-06-23
Well, you need to backtack and tell what you've done, or been doing that might have cause this.  Do you use and unofficial repositories?? Used any .debs manually??

---

### Post by tonym on 2005-06-24
Have you tried apt-get dist-upgrade ?

---

### Post by super on 2005-06-24
I only have one non-ubuntu repository in my sources.conf and it is smoon's E17 repo. and i have not installed any .debs manually. i tried the dist-upgrade and again it upgraded most things but still messed up on thjose files, here is the output:

[FONT=Courier New][COLOR=Blue]Preparing to replace ubuntu-desktop 0.39 (using .../ubuntu-desktop_0.43_i386.deb) ...
Unpacking replacement ubuntu-desktop ...
Setting up postfix (2.1.5-9ubuntu3) ...

Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Starting Postfix Mail Transport Agent...
 *stfix/postfix-script: fatal: the Postfix mail system is already running[fail]
invoke-rc.d: initscript postfix, action "start" failed.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mutt:
 mutt depends on exim4 | mail-transport-agent; however:
  Package exim4 is not installed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mutt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postfix-tls:
 postfix-tls depends on postfix; however:
  Package postfix is not configured yet.
 postfix-tls depends on postfix (= 2.1.5-9ubuntu3); however:
  Package postfix is not configured yet.
dpkg: error processing postfix-tls (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-base:
 ubuntu-base depends on mutt; however:
  Package mutt is not configured yet.
 ubuntu-base depends on postfix; however:
  Package postfix is not configured yet.
 ubuntu-base depends on postfix-tls; however:
  Package postfix-tls is not configured yet.
dpkg: error processing ubuntu-base (--configure):
 dependency problems - leaving unconfigured
Setting up libshout3 (2.0-9) ...

Setting up gstreamer0.8-misc (0.8.8-1ubuntu4) ...

Setting up gstreamer0.8-vorbis (0.8.8-1ubuntu4) ...

Setting up hwdb-client (0.6-0ubuntu2) ...

Setting up libglib-perl (1.061-1) ...
Setting up libgtk2-perl (1.061-1ubuntu1) ...
Setting up libgnome2-canvas-perl (1.002-1) ...
Setting up libgnome2-vfs-perl (1.003-1) ...
Setting up libgnome2-perl (1.020-1) ...
Setting up ubuntu-desktop (0.43) ...
Errors were encountered while processing:
 postfix
 mutt
 postfix-tls
 ubuntu-base
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
[/FONT]

I am stumped since i have ubuntu running on 2 other computers including my home computer which *does* have a ton of unofficial repos and cvs software and yet it works fine.

anyways i fix the GDM and wallpaper switcher problems but this is still a pain.
 ](*,)

---

### Post by alastair on 2005-06-24
I think you are probably safe to just remove all of : postfix mutt postfix-tls and ubuntu-base.

I didn't actually /have/ ubuntu-base installed (I run Hoary on a latop i.e. Gnome, desktop etc.).

I installed it to "see" - then uninstalled it. It uninstalled "mdadm", which it installed a moment ago, and I don't need anyway (on the laptop).

---

### Post by super on 2005-06-25
thanks man thats what i wanted to know
i just did an apt-get remove postfix and that also removed ubuntu-base, ubuntu-desktop and anacron. the first two are know problem but i'll have to find a replacement for anacron or install it from source. but my system seems ok now.
Thanks again!
 :)

---

