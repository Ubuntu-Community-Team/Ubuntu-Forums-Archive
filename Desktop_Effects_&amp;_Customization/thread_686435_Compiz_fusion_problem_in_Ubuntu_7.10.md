---
title: "Compiz fusion problem in Ubuntu 7.10"
date: 2008-02-03
forum: Desktop Effects &amp; Customization
---

### Post by amartya on 2008-02-03
I installed Ubuntu 7.10 desktop from the image disk available in Ubuntu official website. I have heard that this version comes with already installed compiz fusion package.But Ubuntu is not showing the system>preferences>advanced desktop effects settings as it should. I want to enable the desktop cube effect but I could not do so.

My laptop has a Nvidia Geforce 8400M GS 128 mb graphics card and I have installed necessary drivers for it. It is working and I can enable the extra visual effects from system>preferances>appearence. But no 3d cube :(

Now my qn is:
1. what I have to do to enable 3d cu be effect?
2. If I need to reinstall compiz fusion I am getting an error message >>

     Could not download all repository indexes
        The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:) 403 Forbidden
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz:) 403 Forbidden
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz:) 403 Forbidden
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/binary-i386/Packages.gz:) 403 Forbidden


What to do?
If the currently installed compiz will do then what steps to take to enable 3D cube?
i am new to the Linux world so plz give detailed steps to solve the problem.

thanks

---

### Post by merlinDwizzard on 2008-02-03
You need to install compiz settings manager then advanced desktop effects will appear in you preferences tab. I don't have the steps handy, but at least you now know what to search for. Hope this helps.

---

### Post by amartya on 2008-02-03
@merlinDwizzard

I am downloading the compiz settings manager with synaptic but it is giving the msg>>>>

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:) 403 Forbidden
[http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/binary-i386/Packages.gz:](http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/binary-i386/Packages.gz:) 403 Forbidden
[http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/source/Sources.gz:](http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/source/Sources.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/binary-i386/Packages.gz:) 403 Forbidden
[http://download.tuxfamily.org/3v1deb/dists/edgy/beryl-svn/source/Sources.gz:](http://download.tuxfamily.org/3v1deb/dists/edgy/beryl-svn/source/Sources.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/binary-i386/Packages.gz:) 403 Forbidden
[http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz:](http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz:) 403 Forbidden
[http://ubuntu.beryl-project.org/dists/edgy/main/binary-i386/Packages.gz:](http://ubuntu.beryl-project.org/dists/edgy/main/binary-i386/Packages.gz:) 404 Not Found


no luck so far.:confused:

---

### Post by merlinDwizzard on 2008-02-03
let me check on something and i'll get back to you in a few minutes okay

---

### Post by merlinDwizzard on 2008-02-03
check this out amartya [http://kevin.vanzonneveld.net/techblog/article/upgrade_to_ubuntu_gutsy_with_compizfusion/]("http://kevin.vanzonneveld.net/techblog/article/upgrade_to_ubuntu_gutsy_with_compizfusion/")
it installs from gutsy's own compiz repos. Ignore the stuff about feisty. What your'e looking for is step #3 on the gutsy section

---

