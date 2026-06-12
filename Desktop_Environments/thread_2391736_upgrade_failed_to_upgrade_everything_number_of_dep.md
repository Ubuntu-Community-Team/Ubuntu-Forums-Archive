---
title: "upgrade failed to upgrade everything number of dependencies issues now"
date: 2018-05-12
forum: Desktop Environments
---

### Post by derekcentrico on 2018-05-12
Well that was no fun.  My 7-month old go to the keyboard and exited out of the screen for 18.04 upgrade before I had a chance to copy down the errors at the tail end of the upgrade.  It said it completed but had errors on 8 or so things to include python3, unity, gnome, and some other components.

I have not rebooted, but apt gives the following issues:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 gnupg : Depends: gnupg-l10n (= 2.2.4-1ubuntu1) but it is not installed
         Depends: gnupg-utils (= 2.2.4-1ubuntu1)
         Depends: gpg (= 2.2.4-1ubuntu1)
         Depends: gpg-wks-client (= 2.2.4-1ubuntu1)
         Depends: gpg-wks-server (= 2.2.4-1ubuntu1)
         Depends: gpgsm (= 2.2.4-1ubuntu1)
         Depends: gpgv (= 2.2.4-1ubuntu1)
         Breaks: python3-apt (<= 1.1.0~beta4) but 1.1.0~beta1ubuntu0.16.04.1 is installed
         Breaks: software-properties-common (<= 0.96.24.3) but 0.96.20.7 is installed
 libc6-dbg : Depends: libc6 (= 2.23-0ubuntu10) but 2.27-3ubuntu1 is installed
 libc6-i386 : Depends: libc6 (= 2.23-0ubuntu10) but 2.27-3ubuntu1 is installed
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.48.2-0ubuntu1) but 2.56.1-2ubuntu1 is installed
 libglib2.0-dev : Depends: libglib2.0-0 (= 2.48.2-0ubuntu1) but 2.56.1-2ubuntu1 is installed
 libgtk-3-dev : Depends: libglib2.0-dev (>= 2.49.4) but 2.48.2-0ubuntu1 is installed
 python-apt : Depends: libapt-inst2.0 (>= 1.4~beta3) but 1.2.26 is installed
              Depends: libapt-pkg5.0 (>= 1.4~beta3) but 1.2.26 is installed
 python3 : PreDepends: python3-minimal (= 3.5.1-3) but 3.6.5-3 is installed
           Depends: libpython3-stdlib (= 3.5.1-3) but 3.6.5-3 is installed
 python3-minimal : Depends: python3.6-minimal (>= 3.6.5-2~) but it is not installed
 python3.6 : Depends: python3.6-minimal (= 3.6.5-3) but it is not installed
 unity-control-center : Depends: libgnome-desktop-3-17 (>= 3.27.90) but it is not installed
                        Recommends: system-config-printer but it is not installed
                        Recommends: gnome-control-center-faces but it is not installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

I tried -f to repair, but no luck.

Ubuntu forum had a token error and lost tons more on my post.  

Lastlog is just @^ crap.

DMESG.log is quite large and says nothing amazing.  Can try to reproduce again if warranted.

I cannot find any other valuable logs including nothing existing for this upgrade in unattended-upgrades.

Any help so as to complete the upgrade properly before I reboot and end up in a major quandary would be most appreciated.

---

### Post by derekcentrico on 2018-05-12
Here's the stuff from synaptic view snapshot.


[ATTACH=CONFIG]279678[/ATTACH]

---

### Post by derekcentrico on 2018-05-12
Okay, so running dpkg --configure -a gets me what I saw during the upgrade failure screen.

Now I'm stuck at where to go from here...


dpkg: dependency problems prevent configuration of unity-control-center:
 unity-control-center depends on libgnome-desktop-3-17 (>= 3.27.90); however:
  Package libgnome-desktop-3-17 is not installed.


dpkg: error processing package unity-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3.6:
 python3.6 depends on python3.6-minimal (= 3.6.5-3); however:
  Package python3.6-minimal is not installed.


dpkg: error processing package python3.6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apt:
 gnupg (2.2.4-1ubuntu1) breaks python3-apt (<= 1.1.0~beta4) and is unpacked but not configured.
  Version of python3-apt to be configured is 1.1.0~beta1ubuntu0.16.04.1.


dpkg: error processing package python3-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk-3-dev:amd64:
 libgtk-3-dev:amd64 depends on libglib2.0-dev (>= 2.49.4); however:
  Version of libglib2.0-dev on system is 2.48.2-0ubuntu1.


dpkg: error processing package libgtk-3-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnupg2:
 gnupg2 depends on gnupg (>= 2.2.4-1ubuntu1); however:
  Package gnupg is not configured yet.


dpkg: error processing package gnupg2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-minimal:
 python3-minimal depends on python3.6-minimal (>= 3.6.5-2~); however:
  Package python3.6-minimal is not installed.


dpkg: error processing package python3-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apt:
 python-apt depends on libapt-inst2.0 (>= 1.4~beta3); however:
  Version of libapt-inst2.0:amd64 on system is 1.2.26.
 python-apt depends on libapt-pkg5.0 (>= 1.4~beta3); however:
  Version of libapt-pkg5.0:amd64 on system is 1.2.26.
 python-apt depends on gnupg; however:
  Package gnupg is not configured yet.


dpkg: error processing package python-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-common:
 gnupg (2.2.4-1ubuntu1) breaks software-properties-common (<= 0.96.24.3) and is unpacked but not configured.
  Version of software-properties-common to be configured is 0.96.20.7.


dpkg: error processing package software-properties-common (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 unity-control-center
 python3.6
 python3-apt
 libgtk-3-dev:amd64
 gnupg2
 python3-minimal
 python-apt
 software-properties-common
root@homeserver:/var/log#

---

### Post by derekcentrico on 2018-05-12
Now it gets even crappier.  I can't purge it out to reinstall later...  It won't work.

 dpkg --purge unity-control-center
dpkg: dependency problems prevent removal of unity-control-center:
 ubuntu-desktop depends on unity-control-center.
 unity-control-center-signon depends on unity-control-center.


dpkg: error processing package unity-control-center (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 unity-control-center

---

### Post by derekcentrico on 2018-05-12
Bleh I'm stuck now with python errors.  Installed a lot to resolve other issues, but I can't finish due to Python 3.6 which is a dependency itself..

 python3-markupsafe : Depends: python3 (< 3.6) but 3.6.5-3 is installed
 python3-pil : Depends: python3 (< 3.6) but 3.6.5-3 is installed
 python3-pycurl : Depends: python3 (< 3.6) but 3.6.5-3 is installed
 python3-renderpm : Depends: python3 (< 3.6) but 3.6.5-3 is installed
 python3-reportlab-accel : Depends: python3 (< 3.6) but 3.6.5-3 is installed
 python3-systemd : Depends: python3 (< 3.6) but 3.6.5-3 is installed
~

---

### Post by mc4man on 2018-05-12
If this was a 16.04 to 18.04 upgrade it's a coin flip as to whether it'll succeed. (upgrade from 16.04 to 18.04 won't be supported till july or so and still may fail.
Is there any reason not to do a fresh install?

---

### Post by derekcentrico on 2018-05-12
I'd prefer not as I don't remember all my customizations lol. I know that's bad.

Question I made a tarball of /. Easy way to revert from that? Very newb to that.

---

### Post by monkeybrain20122 on 2018-05-12
> **derekcentrico said:**
> I'd prefer not as I don't remember all my customizations lol. I know that's bad.

Question I made a tarball of /. Easy way to revert from that? Very newb to that.

If you have a lot of non trivial customizations then "upgrade" would most likely fail. "upgrade" works best with a pristine system with little modification, Therefore, people are advised to downgrade all their packages installed from ppas (disabling ppa is not enough) Uninstalling third party software including graphic driver etc to return the system back to the configuration it would be if there has been no non trivial customization and tweaks before they upgrade. But why would I go through all those troubles and then wait for a long time for upgrade to proceed while a clean install is much faster and I am going to lose most of my customization and tweaks anyway???


"Upgrade" is kind of pointless. It would be much faster to do a clean install if the system has not been modified much, and the only reason why "upgrade" would be desirable ("because I don't remember all my customizations") is precisely when it has a great chance to fail.

P.S. If you have spent a lot of time customizing 16.04 then I think the best approach is to wait for 18.04.1 comes up before doing anything, unless you want to contribute by filing bug reports, but a more painless way to do it would be to install 18.04 in an external hd or a test partition, or a computer you don't really use.

---

### Post by derekcentrico on 2018-05-12
I don't disagree with your points.  But, it is more trivial than most I'm confident.  My biggest thing is remembering all the changes as this puppy has gone from 12.04 onward with LTS upgrades.

---

### Post by derekcentrico on 2018-05-12
And it came back from reboot showing 18.04, but running 4.13 kernel and apt is still crapped out.  Dang.

---

### Post by derekcentrico on 2018-05-14
Went ahead and re-did the whole home server.  Missing a few components still, and will have to post with respect to an issue in re networking.  Otherwise, we are up again on a fresh install.

This thing went from 12.04 to 14.04 to 16.04.  It was about time for a refresher.

---

