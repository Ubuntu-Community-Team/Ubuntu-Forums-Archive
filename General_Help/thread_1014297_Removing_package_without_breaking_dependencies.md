---
title: "Removing package without breaking dependencies"
date: 2008-12-17
forum: General Help
---

### Post by dax2112rush on 2008-12-17
Hello,

I'd like to know if it is possible to remove a package without removing stuff that depends on the package. What I'd like to do exactly is to remove jackd (audio server) without removing QJackCtl and other dependant stuff. I'd replace jackd with a newer version compiled from source. 
I tried updating the debian package, but did not succeed and I don't want to spend too much time on updating jackd.

Thanks
Eric

---

### Post by Titan8990 on 2008-12-17
If you remove a app, it will not remove the dependencies. In order to remove the dependencies you would have to do apt-get autoremove.

So, as long as you don't give the command apt-get autoremove, it will not remove the dependencies

---

### Post by dax2112rush on 2008-12-17
I think I worded this bad...
Packages on which jackd depends won't be removed, but packages that depend on jackd will be removed:

dax@RockStar:~/SourceBuilds/jack-audio-connection-kit-0.109.2/debian$ sudo  apt-get remove jackd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnuplot gnome-do libnet-daemon-perl libmime-types-perl sharutils libsgmls-perl libfile-remove-perl python-twisted-mail libdigest-sha1-perl x11proto-video-dev python-twisted-bin libreadline5-dev
  nspluginwrapper type-handling gfortran-4.3 libwnck2.20-cil libxv-dev libosp5 docbook-utils python-openssl docbook-dsssl libsp1c2 python-twisted-lore python-twisted-news libdbi-perl libostyle1c2
  libboost-date-time1.34.1 liblo0ldbl docbook-xsl python-twisted-conch python-twisted-words sp python-twisted-web jadetex libxxf86vm-dev transfig linux-source-2.6.27 libfile-desktopentry-perl
  python-twisted python-serial openjade python-pam doxygen sgmlspl libevolution3.0-cil gnuplot-x11 x11proto-xf86vidmode-dev libhdf5-serial-1.6.6-0 libgnomedesktop2.20-cil libboost-thread1.34.1
  libfile-basedir-perl gnuplot-nox gfortran libmail-box-perl libdbd-mysql-perl libnotify0.4-cil libcap-dev python-twisted-core netpbm ftplib3 libcsiro0 docbook-xsl-doc-html libplrpc-perl
  python-zopeinterface python-twisted-names libhdf5-serial-dev python-twisted-runner libnetpbm10 kernel-wedge liblrdf0 libplplot9 libobject-realize-later-perl python-pyopenssl libuser-identity-perl xmlto
  libfreebob0-dev python-crypto libdigest-hmac-perl dh-buildinfo libltdl3 libnetcdf4
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ardour jack-tools jackd qjackctl
0 upgraded, 0 newly installed, 4 to remove and 34 not upgraded.
After this operation, 32.3MB disk space will be freed.
Do you want to continue [Y/n]? 

I want to avoid that since I will be building jackd from SVN.
Thanks

---

### Post by mc4man on 2008-12-17
Whether or not you can will be made irrelevant if qjackctl from ubuntu won't work (or install if you remove it) with the version of libjack0 you'll need for your new build.

Both jackd and qjackctl depend on a specific version of libjack0 which conflicts with different versions of jackd

---

### Post by dax2112rush on 2008-12-17
libjack0 (well the libraries contained in the package) would be built also through the process of building jack from SVN or it's latest stable release. As for QJackCtl, I believe the API (libjack) should be stable enough at this point to be backward compatible with 0.109.2. I may be wrong though.

QJackCtl seems to require libjack0.100.0-dev (>= 0.103.0) and not a specific version according to it's debian/control file.

At the very least, I believe I should be able to keep ardour without having to compile it from source against new version of libjack. So even if it's not relevant (I acknowledge I may run into library version issues, so it's probably a good idea to enforce those rules), I'd like to know if it is possible, so I can try.

If someone could guide me through the process of updating the ubuntu package (standard recipe doesn't seem to work, but I'm not experienced with debian packaging), this could be another (cleaner) solution...

Thanks!

---

### Post by dax2112rush on 2008-12-21
Should I just build from source without removing the jackd package?

---

### Post by snova on 2008-12-21
This could end badly...

You can do it with dpkg. Run 'dpkg --force-help' and it will give you a list of things for you to force. One of them will be to force removal of a package that other packages depend on.

When installing the source, I suggest you use the checkinstall program so that it can be more easily removed later on (on the chance you should want to go back to the official package).

Out of curiousity, why would you want to do this in the first place?

---

### Post by wolfen69 on 2008-12-21
> **Titan8990 said:**
>  In order to remove the dependencies you would have to do apt-get autoremove.



autoremove only removes *unused* dependencies. not sure if that's what you meant.

---

### Post by dax2112rush on 2008-12-21
I need a newer version of jackd to get compatibility with 32-bit programs. This is available with newer versions of jackd, but I failed upgrading the debian package (using apt-get source and uupdate...). It should be possible, but I didn't want to spend lots of time getting familiar with debian packaging. I can get it to compile (out of the debian package context), but I'd prefer not compiling every jack-dependant app from source, that is why I seek to replace jackd and libjack0 with an up to date SVN build.

Thanks for your suggestion of using --force- , I'll try that!

---

### Post by dax2112rush on 2008-12-22
dpkg -r --force-all jackd did indeed do what I intended. However, when I first used synaptic to install something, it removed "broken" packages that depended on jackd and libjack0.

I may therefore give another try at creating a newer version of the jackd and libjack0 .deb...

Thanks

---

### Post by steve167 on 2008-12-22
If you really don't want to overthink this too much you can just roll with my deb.

[http://ubuntuforums.org/showthread.php?t=1018236&highlight=jackd](http://ubuntuforums.org/showthread.php?t=1018236&highlight=jackd)

---

### Post by dax2112rush on 2008-12-22
Thanks for your reply, I was about to do something similar, but I found out there was a Jaunty package for 0.116.1. So I installed it.. but I'm still missing something (my ultimate goal is to run windows VST's through Wine): libjack version 0.116.1 in ia32-libs, and I don't really have a clue on how to update those libs.

---

