---
title: "apt-get thru proxy"
date: 2005-11-29
forum: Desktop Environments
---

### Post by seismicmike on 2005-11-29
I know there are about 50 million ppl who have asked this before, but I still couldn't figure it out...

I cannot get apt-get to work through the proxy...

i did 

```
sudo export http_proxy=http://myproxy:myport
```

but i can't figure out how to authenticate

I tried:

```
sudo export http_proxy=http://myuname:mypass@myproxy:myport
```

no dice...

Can anyone help?

Should I put a line in the /etc/apt/apt.conf.d/proxy file about authentication???

---

### Post by Ampersand on 2005-11-29
My ubuntu computer is currently having hardware problems so I can't check, but are there any proxy settings in Synpatic (in the System - Administration menu)? If you set it there, it should also work for apt.

---

### Post by cwaldbieser on 2005-11-29
[QUOTE=seismicmike]I know there are about 50 million ppl who have asked this before, but I still couldn't figure it out...

I cannot get apt-get to work through the proxy...

i did 

```
sudo export http_proxy=http://myproxy:myport
```

but i can't figure out how to authenticate

I tried:

```
sudo export http_proxy=http://myuname:mypass@myproxy:myport
```

no dice...

Can anyone help?

Should I put a line in the /etc/apt/apt.conf.d/proxy file about authentication???[/QUOTE]

Are you sure you are supposed to use the "sudo" there?  I tried that from the command line and got an error.

---

### Post by seismicmike on 2005-11-30
[QUOTE=cwaldbieser]Are you sure you are supposed to use the "sudo" there?  I tried that from the command line and got an error.[/QUOTE]

actually, I did

```
sudo -s
```

and then typed everything above (omitting the sudo at the beginning).

---

### Post by seismicmike on 2005-11-30
[QUOTE=Ampersand]My ubuntu computer is currently having hardware problems so I can't check, but are there any proxy settings in Synpatic (in the System - Administration menu)? If you set it there, it should also work for apt.[/QUOTE]

Yeah, I put it in there and everything and synaptic contacts the proxy server to go through to get the stuff, but I can't get through b/c I have to authenticate.

It never prompts for a password.

In Synaptic I put my proxy info in as
```
Server: proxy.domain.com
Port: 80
```

and it doesn't do anything at all (can't find the proxy server or whatever)

So I tried:
```
Server: username@proxy.domain.com
Port: 80
```

Then it contacts the proxy server and puts my user name in, but it doesn't authenticate, so it doesn't go through

so I tried:

```
Server username:password@proxy.domain.com
Port: 80
```

and it says that It couldn't find an entry for "password@proxy.domain.com"

hmmmm :(

---

### Post by MikeyXX on 2005-11-30
I haven't got synaptic to work. But I have got apt-get to work off the prompt:

Do your export http_proxy=http://myuname:mypass@myproxy:myport

Then sudo apt-get update

Give that a shot. Don't do the "sudo" part in your export. And remember this only works for that terminal session. Try quotes around the "http://name:password@proxy:port" part if the above doesn't work.

---

### Post by seismicmike on 2005-11-30
without the quotes:
```
Ign http://us.archive.ubuntu.com breezy Release.gpg
Ign http://security.ubuntu.com breezy-security Release.gpg
Ign http://us.archive.ubuntu.com breezy-updates Release.gpg
Ign http://security.ubuntu.com breezy-security Release
Ign http://us.archive.ubuntu.com breezy-backports Release.gpg
Ign http://security.ubuntu.com breezy-security/main Packages
Ign http://us.archive.ubuntu.com breezy Release
Ign http://security.ubuntu.com breezy-security/restricted Packages
Ign http://us.archive.ubuntu.com breezy-updates Release
Ign http://security.ubuntu.com breezy-security/main Sources
Ign http://security.ubuntu.com breezy-security/restricted Sources
Ign http://us.archive.ubuntu.com breezy-backports Release
Ign http://security.ubuntu.com breezy-security/universe Packages
Ign http://us.archive.ubuntu.com breezy/main Packages
Ign http://us.archive.ubuntu.com breezy/restricted Packages
Ign http://security.ubuntu.com breezy-security/universe Sources
Ign http://us.archive.ubuntu.com breezy/main Sources
Err http://security.ubuntu.com breezy-security/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://security.ubuntu.com breezy-security/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Ign http://us.archive.ubuntu.com breezy/restricted Sources
Ign http://us.archive.ubuntu.com breezy/universe Packages
Err http://security.ubuntu.com breezy-security/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Ign http://us.archive.ubuntu.com breezy/universe Sources
Ign http://us.archive.ubuntu.com breezy-updates/main Packages
Err http://security.ubuntu.com breezy-security/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://security.ubuntu.com breezy-security/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://security.ubuntu.com breezy-security/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Ign http://us.archive.ubuntu.com breezy-updates/restricted Packages
Ign http://us.archive.ubuntu.com breezy-updates/main Sources
Ign http://us.archive.ubuntu.com breezy-updates/restricted Sources
Ign http://us.archive.ubuntu.com breezy-backports/main Packages
Ign http://us.archive.ubuntu.com breezy-backports/restricted Packages
Ign http://us.archive.ubuntu.com breezy-backports/universe Packages
Ign http://us.archive.ubuntu.com breezy-backports/multiverse Packages
Ign http://us.archive.ubuntu.com breezy-backports/main Sources
Ign http://us.archive.ubuntu.com breezy-backports/restricted Sources
Ign http://us.archive.ubuntu.com breezy-backports/universe Sources
Ign http://us.archive.ubuntu.com breezy-backports/multiverse Sources
Err http://us.archive.ubuntu.com breezy/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-updates/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-updates/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-updates/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-updates/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Reading package lists... Done
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by seismicmike on 2005-11-30
with the quotes:
```
Ign http://security.ubuntu.com breezy-security Release.gpg
Ign http://security.ubuntu.com breezy-security Release
Ign http://security.ubuntu.com breezy-security/main Packages
Ign http://security.ubuntu.com breezy-security/restricted Packages
Ign http://security.ubuntu.com breezy-security/main Sources
Ign http://security.ubuntu.com breezy-security/restricted Sources
Ign http://security.ubuntu.com breezy-security/universe Packages
Ign http://security.ubuntu.com breezy-security/universe Sources
Err http://security.ubuntu.com breezy-security/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://security.ubuntu.com breezy-security/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://security.ubuntu.com breezy-security/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://security.ubuntu.com breezy-security/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://security.ubuntu.com breezy-security/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://security.ubuntu.com breezy-security/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Ign http://us.archive.ubuntu.com breezy Release.gpg
Ign http://us.archive.ubuntu.com breezy-updates Release.gpg
Ign http://us.archive.ubuntu.com breezy-backports Release.gpg
Ign http://us.archive.ubuntu.com breezy Release
Ign http://us.archive.ubuntu.com breezy-updates Release
Ign http://us.archive.ubuntu.com breezy-backports Release
Ign http://us.archive.ubuntu.com breezy/main Packages
Ign http://us.archive.ubuntu.com breezy/restricted Packages
Ign http://us.archive.ubuntu.com breezy/main Sources
Ign http://us.archive.ubuntu.com breezy/restricted Sources
Ign http://us.archive.ubuntu.com breezy/universe Packages
Ign http://us.archive.ubuntu.com breezy/universe Sources
Ign http://us.archive.ubuntu.com breezy-updates/main Packages
Ign http://us.archive.ubuntu.com breezy-updates/restricted Packages
Ign http://us.archive.ubuntu.com breezy-updates/main Sources
Ign http://us.archive.ubuntu.com breezy-updates/restricted Sources
Ign http://us.archive.ubuntu.com breezy-backports/main Packages
Ign http://us.archive.ubuntu.com breezy-backports/restricted Packages
Ign http://us.archive.ubuntu.com breezy-backports/universe Packages
Ign http://us.archive.ubuntu.com breezy-backports/multiverse Packages
Ign http://us.archive.ubuntu.com breezy-backports/main Sources
Ign http://us.archive.ubuntu.com breezy-backports/restricted Sources
Ign http://us.archive.ubuntu.com breezy-backports/universe Sources
Ign http://us.archive.ubuntu.com breezy-backports/multiverse Sources
Err http://us.archive.ubuntu.com breezy/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-updates/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-updates/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-updates/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-updates/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Reading package lists... Done
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by cwaldbieser on 2005-11-30
[QUOTE=seismicmike]with the quotes:
```
Ign http://security.ubuntu.com breezy-security Release.gpg
Ign http://security.ubuntu.com breezy-security Release
Ign http://security.ubuntu.com breezy-security/main Packages
Ign http://security.ubuntu.com breezy-security/restricted Packages
Ign http://security.ubuntu.com breezy-security/main Sources
Ign http://security.ubuntu.com breezy-security/restricted Sources
Ign http://security.ubuntu.com breezy-security/universe Packages
Ign http://security.ubuntu.com breezy-security/universe Sources
Err http://security.ubuntu.com breezy-security/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://security.ubuntu.com breezy-security/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://security.ubuntu.com breezy-security/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://security.ubuntu.com breezy-security/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://security.ubuntu.com breezy-security/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://security.ubuntu.com breezy-security/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Ign http://us.archive.ubuntu.com breezy Release.gpg
Ign http://us.archive.ubuntu.com breezy-updates Release.gpg
Ign http://us.archive.ubuntu.com breezy-backports Release.gpg
Ign http://us.archive.ubuntu.com breezy Release
Ign http://us.archive.ubuntu.com breezy-updates Release
Ign http://us.archive.ubuntu.com breezy-backports Release
Ign http://us.archive.ubuntu.com breezy/main Packages
Ign http://us.archive.ubuntu.com breezy/restricted Packages
Ign http://us.archive.ubuntu.com breezy/main Sources
Ign http://us.archive.ubuntu.com breezy/restricted Sources
Ign http://us.archive.ubuntu.com breezy/universe Packages
Ign http://us.archive.ubuntu.com breezy/universe Sources
Ign http://us.archive.ubuntu.com breezy-updates/main Packages
Ign http://us.archive.ubuntu.com breezy-updates/restricted Packages
Ign http://us.archive.ubuntu.com breezy-updates/main Sources
Ign http://us.archive.ubuntu.com breezy-updates/restricted Sources
Ign http://us.archive.ubuntu.com breezy-backports/main Packages
Ign http://us.archive.ubuntu.com breezy-backports/restricted Packages
Ign http://us.archive.ubuntu.com breezy-backports/universe Packages
Ign http://us.archive.ubuntu.com breezy-backports/multiverse Packages
Ign http://us.archive.ubuntu.com breezy-backports/main Sources
Ign http://us.archive.ubuntu.com breezy-backports/restricted Sources
Ign http://us.archive.ubuntu.com breezy-backports/universe Sources
Ign http://us.archive.ubuntu.com breezy-backports/multiverse Sources
Err http://us.archive.ubuntu.com breezy/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-updates/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-updates/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-updates/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-updates/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Err http://us.archive.ubuntu.com breezy-backports/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Reading package lists... Done
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```[/QUOTE]

OK, I got it.  You are trying to authenticate against a MS ISA proxy.  If it is using NTLM authentication, you are not going to get very far.

I had this problem at work.  In order to get around it, I used this neat little python script that acts as a proxy to the proxy, and it can do NTLM authentication on your behalf.

You can get the script here: [http://www.geocities.com/rozmanov/ntlm/]("http://www.geocities.com/rozmanov/ntlm/")

Configuring it is pretty simple, but if you have questions, feel free to ask.

---

### Post by seismicmike on 2005-12-01
Funny story... I actually figured it out by reading another post from someone who was having trouble with the same thing...

I was forgetting to put my domain in....

instead of

in the file /etc/apt/apt.conf, I added the line:

```
Acquire::http::Proxy "http://MYDOMAIN\MYNAME:MYPASS@MY.PROXY.COM:MYPORT"
```

whereas before I just had:

[code]Acquire::http::Proxy "http://MYNAME:MYPASS@MY.PROXY.COM:MYPORT"

---

### Post by Sarek on 2006-05-30
Just to let you know:

```
Acquire::http::Proxy "http://MYDOMAIN\MYNAME:MYPASS@MY.PROXY.COM:MYPORT"**;**
```

I had to put a semicolon at the end of the line. Otherwise I was informed of > additional chunk at the end of line.

Best wishes! :D

---

### Post by steve66 on 2006-05-30
[QUOTE=cwaldbieser]OK, I got it.  You are trying to authenticate against a MS ISA proxy.  If it is using NTLM authentication, you are not going to get very far.

I had this problem at work.  In order to get around it, I used this neat little python script that acts as a proxy to the proxy, and it can do NTLM authentication on your behalf.

You can get the script here: [http://www.geocities.com/rozmanov/ntlm/]("http://www.geocities.com/rozmanov/ntlm/")

Configuring it is pretty simple, but if you have questions, feel free to ask.[/QUOTE]
I try ntlmasp script (main.py), where I edited server.cfg:
PARENT_PROXY, PARENT_PORT,NT_DOMAIN, USER and PASSWORD leave blank
 then I run script my.py and enter PASWORD;
and finally I run apt-get update, but get same error  "407 Proxy Authentication Required "
What do you need yet to apt-get using this ntlmaps ?
Thanks fo r each advice

---

### Post by hamisan on 2006-07-13
Hi,
I had this problem "407 Proxy Authentication Required" right now, too. Therefore I've started to search any soultion on the web, so I've found this forum.
I've already tried all of the variation of the possible solutions written here except the last one being a little bit difficult :) even though nothing helped me. Then I've looked at the http_proxy environment variable:

# echo $http_proxy
[http://myproxy:myport/](http://myproxy:myport/)

Then I changed it in the following way:

# http_proxy=http://myuser:mypasswd@myproxy:myport/

And now everything works fine. Don't ask me why. But! After I log out and log in again, I have to set this variable again.

---

### Post by sms_james on 2006-07-25
Refer to the My articles->linux section in [www.tarunworld.com](www.tarunworld.com).. You will definately be able to do after that..

Regards

---

### Post by mdecler2 on 2006-07-27
There has to be a safer way to this...
The last thing I want to do is put my proxy password in plain text.
Shouldn't there be some encryption to make this work?

Honestly, I have been setting the http_proxy environment variable each time, that is probably safer since I can remove it when I need to. But that is just tedious.

Anybody have any ideas?

---

### Post by arnieboy on 2006-07-27
try this:
[http://ubuntuforums.org/showpost.php?p=541276&postcount=1006](http://ubuntuforums.org/showpost.php?p=541276&postcount=1006)

---

### Post by mdecler2 on 2006-08-04
> **arnieboy said:**
> try this:
[http://ubuntuforums.org/showpost.php?p=541276&postcount=1006](http://ubuntuforums.org/showpost.php?p=541276&postcount=1006)
This did not work for me:
```

ACQUIRE
{
   http::proxy "http://proxy:port/"
}

```

I have to authenticate against my proxy and this configuration only gave me errors, without asking for authentication.

---

### Post by mdecler2 on 2007-05-22
I'd like to bump this. Does anyone know a better way of apt-get'ing through a proxy that does not involve storing a password in plain text?

---

### Post by hamen on 2007-05-29
Hi,
I know it can be stupid for someone, but I have a problem with my proxy password.
I'm trying with:

export http_proxy=http://myuser:mypasswd@myproxy:myport/

but my password contains " : ".
I got:
407 Proxy Authentication Required

I guess it misunderstands "myuser:mypassword" part
Any idea?
Thanks,
hamen

---

### Post by inception on 2007-05-30
Hi there,

I'm also trying to connect to a MS ISA server that requires authentication.
My apt.conf looks like this;

```
Acquire::http::Proxy "http://unett\******:******@http://ped-01isa/array.dll?Get.Routing.Script:8080";
```
As you can see, I have to do the array.dll operation thing, and in terminal it gives me
```
[Connecting to ped-01isa (10.120.0.184)] 
```
I'm guessing it doesn't work because it won't accept the path after the server name?

---

### Post by mdecler2 on 2007-05-30
> **inception said:**
> Hi there,

I'm also trying to connect to a MS ISA server that requires authentication.
My apt.conf looks like this;

```
Acquire::http::Proxy "http://unett\******:******@http://ped-01isa/array.dll?Get.Routing.Script:8080";
```
As you can see, I have to do the array.dll operation thing, and in terminal it gives me
```
[Connecting to ped-01isa (10.120.0.184)] 
```
I'm guessing it doesn't work because it won't accept the path after the server name?

inception, is your user name actually unett\****** with the backslash? That might be the problem. I'm guessing that you are trying to hide your user name on the forum, or what are all those stars representing? Also, make sure you are on the right port for the proxy server, it  might be on something like 1080 instead of the main traffic 8080 port.

Try a different format:```

ACQUIRE
{
   http::proxy "http://userName:password@some.proxy.com:1080/";
}

```
For the heck of it, try a forward slash at the end before the double quote, that seems to work for me.
I have no idea what the problem could be otherwise, that seems like the right format as far as I know.

---

### Post by mdecler2 on 2007-05-30
> **hamen said:**
> Hi,
I know it can be stupid for someone, but I have a problem with my proxy password.
I'm trying with:

export http_proxy=http://myuser:mypasswd@myproxy:myport/

but my password contains " : ".
I got:
407 Proxy Authentication Required

I guess it misunderstands "myuser:mypassword" part
Any idea?
Thanks,
hamen

Hamen, I really don't know what to do in your case. I tried using single quotes around my password, but those were interpreted as part of the password string. The only thing I can think of is using a backslash like you would use for regular expressions. The problem seems like the system is interpretting your ':' as part of the format as opposed to part of the actual password itself. The backslash might cause the system to interpret the colon differently, But then again, there is no reason why a backslash couldn't be part of the password string as well...I might change my password if I was you.

---

### Post by ozmark on 2007-05-31
> **mdecler2 said:**
> I'd like to bump this. Does anyone know a better way of apt-get'ing through a proxy that does not involve storing a password in plain text?

I put the following in my .bashrc, then all I have to do is type 'proxy' to be prompted for password before I do any apt-get'ing;

```
proxy ()
{
    echo -n "proxy password: ";
    read -es password;
    echo;
    export http_proxy="http://username:$password@proxy:port/";
}
```

It's as safe as you'll get, the password only "lives" in your current shell session.

---

### Post by mdecler2 on 2007-06-01
> **ozmark said:**
> I put the following in my .bashrc, then all I have to do is type 'proxy' to be prompted for password before I do any apt-get'ing;



Interesting idea with the .bashrc. I took your script, turned it into a shell script and refined it a little bit to my liking. Let me know what you think:
```

#!/bin/sh
echo -n "Proxy password: ";
read -es password;
echo;
export http_proxy="http://user_name:$password@proxy:port/";

if !(sudo apt-get update)
   then echo "Failure: apt-get update";
fi

sleep 2

echo -n "Run 'apt-get upgrade'? (Y/N): ";
read -e response;

if [ "$response" = "Y" ] || [ "$response" = "y" ]
   then
      if !(sudo apt-get upgrade)
         then echo "Failure: apt-get upgrade";
      fi
elif [ "$response" != "N" ] || [ "$response" != "n" ]
   then echo "$response: Invalid input.";
fi

unset http_proxy;

exit 0;

```

---

### Post by jorno on 2007-09-10
I don't know if anyone still has this problem, but I found my solution in another post.

The steps mentioned here earlier are good and all, BUT if those of  you who's got this problem is in a Windows environment with a Microsoft ISA Proxy that need authentication, this is the solution that worked for me:

You need to install NTLMAPS.

[http://packages.ubuntu.com/feisty/web/ntlmaps](http://packages.ubuntu.com/feisty/web/ntlmaps)
* Go there, and download, either from within Firefox (if you manage to get Proxy working with Firefox - I did, but not apt-get or Synaptics or anything else).
* Download the package for ntlmaps (this is for Ubuntu Feisty)
* Start a terminal, find your downloaded package, and type:
*sudo dpkg -i ntlmaps_0.9.9.0.1-6_all.deb*
This should guide you trough the installation of the package...

BUT, my problems didn't stop there!
After, I had to edit /etc/ntlmaps/server.cfg manually.
( *sudo vim /etc /ntlmaps/server.cfg* )
Then I saw that the config-file was formatted with DOS (not UNIX), so I had to tell vim to convert it to UNIX-format. Do this in vim:
*:set fileformat=unix*
*:wq*
This should convert the file, and save it.
I also had to change some of the options:
Under the [CLIENT_HEADER] section, I had to comment out the first Accept and User-Agent part (Windows 98), and then uncomment the next part (Windows 2000 emulation).
Then I filled in "NT_HOSTNAME" (remembered what PC number this workstation had in Windows), and "NT_DOMAIN").

After those changes, restart ntlmaps:
*/etc/init.d/ntlmaps restart*

And point all your proxy-settings to: [http://127.0.0.1:5865](http://127.0.0.1:5865)

Make a file: */etc/apt/apt.conf*
Acquire::http::Proxy "http://127.0.0.1:5865";

And then try "*apt-get update*".

You could also insert this into:
System -> Preferences -> Network Proxy

And in Synaptics:
System -> Administration -> Synaptics -> Settings -> Preferences -> Network:
Manual proxy configuration:

127.0.0.1 port 5865 (no authentication)


This should do the trick! It did for me.. Please ask if there is something not clear yet, or if I should correct any of this. (Sorry, English is not my native tongue).

---

### Post by jbindel on 2007-09-21
> **mdecler2 said:**
> Interesting idea with the .bashrc. I took your script, turned it into a shell script and refined it a little bit to my liking. Let me know what you think:

Rather than setting the username and password in an environment variable that may be available to any setup scripts that get run from apt-get, I am passing the credentials on the apt-get command line with a modified version of your script.

```

#!/bin/sh
echo -n "Proxy password: ";
read -es password;
echo;
proxyOption='Acquire::http::Proxy="http://domain\username:'$password'@proxyip:port/"';

if !(sudo apt-get -o $proxyOption update)
   then echo "Failure: apt-get update";
fi

sleep 2

echo -n "Run 'apt-get upgrade'? (Y/N): ";
read -e response;

if [ "$response" = "Y" ] || [ "$response" = "y" ]
   then
      if !(sudo apt-get -o $proxyOption upgrade)
         then echo "Failure: apt-get upgrade";
      fi
elif [ "$response" != "N" ] || [ "$response" != "n" ]
   then echo "$response: Invalid input.";
fi

```

It seems maybe a little bit safer.

---

### Post by bve on 2007-10-09
Although this is an old thread, the following worked for me

[http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)

---

### Post by tech9 on 2007-10-25
> **jorno said:**
> I don't know if anyone still has this problem, but I found my solution in another post.

The steps mentioned here earlier are good and all, BUT if those of  you who's got this problem is in a Windows environment with a Microsoft ISA Proxy that need authentication, this is the solution that worked for me:

You need to install NTLMAPS.

[http://packages.ubuntu.com/feisty/web/ntlmaps](http://packages.ubuntu.com/feisty/web/ntlmaps)
* Go there, and download, either from within Firefox (if you manage to get Proxy working with Firefox - I did, but not apt-get or Synaptics or anything else).
* Download the package for ntlmaps (this is for Ubuntu Feisty)
* Start a terminal, find your downloaded package, and type:
*sudo dpkg -i ntlmaps_0.9.9.0.1-6_all.deb*
This should guide you trough the installation of the package...

BUT, my problems didn't stop there!
After, I had to edit /etc/ntlmaps/server.cfg manually.
( *sudo vim /etc /ntlmaps/server.cfg* )
Then I saw that the config-file was formatted with DOS (not UNIX), so I had to tell vim to convert it to UNIX-format. Do this in vim:
*:set fileformat=unix*
*:wq*
This should convert the file, and save it.
I also had to change some of the options:
Under the [CLIENT_HEADER] section, I had to comment out the first Accept and User-Agent part (Windows 98), and then uncomment the next part (Windows 2000 emulation).
Then I filled in "NT_HOSTNAME" (remembered what PC number this workstation had in Windows), and "NT_DOMAIN").

After those changes, restart ntlmaps:
*/etc/init.d/ntlmaps restart*

And point all your proxy-settings to: [http://127.0.0.1:5865](http://127.0.0.1:5865)

Make a file: */etc/apt/apt.conf*
Acquire::http::Proxy "http://127.0.0.1:5865";

And then try "*apt-get update*".

You could also insert this into:
System -> Preferences -> Network Proxy

And in Synaptics:
System -> Administration -> Synaptics -> Settings -> Preferences -> Network:
Manual proxy configuration:

127.0.0.1 port 5865 (no authentication)


This should do the trick! It did for me.. Please ask if there is something not clear yet, or if I should correct any of this. (Sorry, English is not my native tongue).

Big Thanks to jorno for this post! :)

---

### Post by tenderflesh on 2007-11-30
Jorno, your way totally worked!!!  thanks!! :)

---

