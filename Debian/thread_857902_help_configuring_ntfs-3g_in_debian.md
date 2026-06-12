---
title: "help configuring ntfs-3g in debian"
date: 2008-07-13
forum: Debian
---

### Post by timzak on 2008-07-13
Hi,

I'm using Debian Lenny w/XFCE and would like some help configuring ntfs-3g to read my ntfs drive on dev/hda2.  I'd prefer to use ntfs-config (it worked very easily when I was playing with Xubuntu before installing Debian XFCE), but I cannot locate it in the Debian repositories.  

On a side note, is there a site that has all the Debian repositories listed so I can pick and choose which to add?  I'd like some non-free and multimedia options.

Thanks.

---

### Post by odiseo77 on 2008-07-13
Hi. As for the ntfs-config package, i don't find it in the repos either. I'd suggest you to open synaptic and search for the keyword "ntfs"; some packages should appear there. I haven't these installed, but maybe you could find "ntfsprogs" and "disk-manager" interesting for your purposes.

If this helps, this is the line I'm using in my /etc/fstab file for my ntfs partition:

```
[COLOR="Red"]/dev/sda6[/COLOR]       [COLOR="Red"]/mnt/datos[/COLOR]      ntfs-3g   defaults,auto,[COLOR="Red"]locale=es_VE.utf8[/COLOR],uid=[COLOR="Red"]username[/COLOR],gid=[COLOR="Red"]username[/COLOR]  0       0
```

The things in red are options that you have to change according to your needs: device, mount point, locale in case you need a special one like me, username should be your user, in case you have one and you want this one to have full access to this partition, etc. The options could differ a lot from mine according to your needs. If you need to specify a special locale to use, execute ***locale -a*** to know what locale(s) you're using.

As for the repositories, this is my sources.list:

```
##
# deb cdrom:[Debian GNU/Linux testing _Lenny_ - Official Snapshot i386 DVD Binary-1 20071106-23:39]/ lenny contrib main 

# deb cdrom:[Debian GNU/Linux testing _Lenny_ - Official Snapshot i386 DVD Binary-1 20071106-23:39]/ lenny contrib main 

# Line commented out by installer because it failed to verify:
deb http://security.debian.org/ lenny/updates main contrib 
# Line commented out by installer because it failed to verify:
deb-src http://security.debian.org/ lenny/updates main contrib 

deb http://ftp.us.debian.org/debian/ testing main contrib non-free 
deb-src http://ftp.us.debian.org/debian/ testing main contrib non-free 

#Debian Unofficial
#deb http://ftp.debian-unofficial.org/debian/ testing main contrib non-free restricted   

#Debian Unstable
#deb http://ftp.us.debian.org/debian/ sid main contrib non-free   

#Debian Experimental
#deb http://ftp.us.debian.org/debian/ experimental main contrib non-free  

#Debian-multimedia
deb http://mirror.home-dn.net/debian-multimedia/ lenny main 
deb-src http://mirror.home-dn.net/debian-multimedia/ lenny main
```

There might be other repositories but these ones have worked fine for me.

Greetings.

---

### Post by timzak on 2008-07-14
Thanks, that was very helpful.  One follow up question, with your sources.list, I now get a message about one or more of the repositories not having a valid key?  I forget the exact terminology and I'm not in front of a Linux computer at the moment.  Do you know what I'm talking about?

Thanks.

---

### Post by odiseo77 on 2008-07-14
As for the repositories keys, it's like a signature that certifies the package(s) you're downloading belong to a specific repository. Basically, apt-get (or aptitude, or synaptic) is warning you that it's not sure these packages are trusted. Some debian repositories have a package named debian-*-keyring that you can install to get rid of these warnings (only if you know the repository you're adding is trusted). I think that probably the key apt-get is warning you about is the debian-multimedia keyring. Take a look at [this]("http://www.debian-multimedia.org/"), specifically, this part:

> The first package to install is debian-multimedia-keyring.
Under root do the following :
wget [http://debian-multimedia.org/gpgkey.pub](http://debian-multimedia.org/gpgkey.pub) -O - | apt-key add - && apt-get install debian-multimedia-keyring

If this is the keyring you're missing, the above should get rid of the warning. Otherwise, you can google for the key number, or post the complete error here to see what are you missing :)

Greetings.

---

