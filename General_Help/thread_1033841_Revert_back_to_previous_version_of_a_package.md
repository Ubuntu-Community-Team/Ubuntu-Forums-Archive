---
title: "Revert back to previous version of a package"
date: 2009-01-07
forum: General Help
---

### Post by dslehman on 2009-01-07
How does one revert back to a previous version of an installed package? For example, on my Ubuntu Dapper box I have recently applied a security patch via apt-get that upgraded the package "libgnutls12" from version "1.2.9-2ubuntu1.2" to version "1.2.9-2ubuntu1.4." Let's say that this update caused services to break that depended on the package "libgnutls12." How does one now revert back to the previous version "1.2.9-2ubuntu1.2"?

I had always assumed that Ubuntu kept all of their older packages in their repositories. However, it appears that they remove older releases and only keep the latest release.

I ran this command to see what package versions were available:

<snip>
root@vm36:/var/log# apt-cache showpkg libgnutls12
Package: libgnutls12
Versions: 
1.2.9-2ubuntu1.4(/var/lib/apt/lists/mirror.anl.gov_ubuntu_dists_dapper-updates_main_binary-amd64_Packages)(/var/lib/apt/lists/mirror.anl.gov_ubuntu_dists_dapper-security_main_binary-amd64_Packages)
1.2.9-2ubuntu1(/var/lib/apt/lists/mirror.anl.gov_ubuntu_dists_dapper_main_binary-amd64_Packages)(/var/lib/dpkg/status)
</snip>

Note that version "1.2.9-2ubuntu1.2" is not listed.

I then browsed the repo via my web browser ([http://security.ubuntu.com/ubuntu/pool/main/g/gnutls12/](http://security.ubuntu.com/ubuntu/pool/main/g/gnutls12/)). I verified that only the latest package "libgnutls12_1.2.9-2ubuntu1.4_amd64.deb" was present.


So if I wanted to back out of an update, where do I go to get the previous version of packages?

Thanks!!

---

### Post by dslehman on 2009-03-12
Anyone?
If one were to do a standard ubuntu package update, then they were to discover that the new package release broke something critical, how does one obtain the previous package release? That way they can reinstall the older, working version.

Thanks!!!

---

### Post by BadgerKid on 2009-04-23
I am also interested in how to do this since an upgrade broke my sound system.

---

### Post by mc4man on 2009-04-23
kinda hard today to show how because launchpad seems really slow but that's were you can usually find older versions.

For instance the op was looking for this
[https://launchpad.net/ubuntu/+source/gnutls12/1.2.9-2ubuntu1.2/+build/612568](https://launchpad.net/ubuntu/+source/gnutls12/1.2.9-2ubuntu1.2/+build/612568)

---

### Post by nholtz on 2010-01-20
A bit late to help the original poster, but perhaps for new googlers ...

I thought this morning that installing a new version of the intel video driver broke the ability for me to use the external VGA with a video projector.  I was possibly wrong about that, but this is what I did to restore the previous driver:

> apt-cache show xserver-xorg-video-intel | fgrep Version:

From that I determined that the previous version was  2:2.9.0-1ubuntu2~xup~3

Reverted back to that one by doing:

> sudo apt-get install xserver-xorg-video-intel=2:2.9.0-1ubuntu2~xup~3

Hope that helps
cheers

---

