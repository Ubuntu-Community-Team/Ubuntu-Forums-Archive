---
title: "Synaptic not working"
date: 2010-05-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TerryDecker on 2010-05-10
Get this error when running synaptic package manager. Its getting to be quite the headache. I've tried everything I know to get things up and running again and I don't want to reinstall the operating system. Suggestions?

E: Could not perform immediate configuration on 'libselinux1'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

---

### Post by IzByFl on 2010-07-07
I have the same problem.
I tried
```
izb@izb-laptop:~$ sudo apt-get install libselinux1
```
and i got
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apt apt-utils ca-certificates coreutils debconf debconf-i18n dpkg findutils
  gcc-4.4-base gnupg gnupg-curl gpgv libacl1 libattr1 libbz2-1.0 libc-bin
  libc6 libcomerr2 libcurl3-gnutls libdb4.8 libgcc1 libgcrypt11 libgnutls26
  libgpg-error0 libgpm2 libgssapi-krb5-2 libidn11 libk5crypto3 libkeyutils1
  libkrb5-3 libkrb5support0 libldap-2.4-2 liblocale-gettext-perl libncurses5
  libreadline6 libsasl2-2 libsasl2-modules libssl0.9.8 libstdc++6 libtasn1-3
  libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libusb-0.1-4
  lzma openssl perl-base readline-common tzdata ubuntu-keyring zlib1g
Suggested packages:
  aptitude synaptic wajig dpkg-dev apt-doc bzip2 python-apt debconf-doc
  debconf-utils whiptail dialog gnome-utils libterm-readline-gnu-perl
  libgnome2-perl libnet-ldap-perl mlocate locate slocate gnupg-doc xloadimage
  imagemagick eog libpcsclite1 glibc-doc locales rng-tools gnutls-bin gpm
  krb5-doc krb5-user libsasl2-modules-otp libsasl2-modules-ldap
  libsasl2-modules-sql libsasl2-modules-gssapi-mit
  libsasl2-modules-gssapi-heimdal openssl-doc
The following NEW packages will be installed:
  apt apt-utils ca-certificates coreutils debconf debconf-i18n dpkg findutils
  gcc-4.4-base gnupg gnupg-curl gpgv libacl1 libattr1 libbz2-1.0 libc-bin
  libc6 libcomerr2 libcurl3-gnutls libdb4.8 libgcc1 libgcrypt11 libgnutls26
  libgpg-error0 libgpm2 libgssapi-krb5-2 libidn11 libk5crypto3 libkeyutils1
  libkrb5-3 libkrb5support0 libldap-2.4-2 liblocale-gettext-perl libncurses5
  libreadline6 libsasl2-2 libsasl2-modules libselinux1 libssl0.9.8 libstdc++6
  libtasn1-3 libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl
  libusb-0.1-4 lzma openssl perl-base readline-common tzdata ubuntu-keyring
  zlib1g
0 upgraded, 52 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/22.2MB of archives.
After this operation, 76.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Could not perform immediate configuration on 'libselinux1'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

```
please help!

---

### Post by IzByFl on 2010-07-07
I think I fixed it!! 

What I did was: 

1. Load the live version with the cd. 

2. Open the partition where I have ubuntu installed. 

3. Type in the terminal ```
sudo nautilus
``` 

4. Search in my ubuntu partition for "dpkg". 

5. And finally replace every folder with that name for the one that is in the live version file system located in the same place. 

That worked for my. Do it at your own risk.

Then I got another error that I fixed deleting everything in "/var/lib/dpkg/info" (I got it from [[COLOR="Navy"][COLOR="Blue"]here[/COLOR][/COLOR]]("http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/")).

Again. Do it at your own risk.

Good luck!

---

