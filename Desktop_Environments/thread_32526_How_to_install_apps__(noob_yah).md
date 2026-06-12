---
title: "How to install apps?  (noob yah)"
date: 2005-05-08
forum: Desktop Environments
---

### Post by anon.irisX on 2005-05-08
I love my Kubuntu, but i have no idea how to install stuff.  I was quite disappointed with the fact it didn't seem to come with much installed.

Two things it didn't install that I very much want/need are the GIMP and XMMS.

I can easily download the latest versions of both, (except for the GIMP) and already have XMMS.  

So what now?  A lot of people mention the apt-get prefixtural command, but isn't that just for when downloading programs?  

Because I have one old computer with the internet and my new one which has Kubuntu.  I don't really plan on getting internet on this one; I just put the things on disc.

Can someone please help me out with this?  Thanks a million.

---

### Post by XDevHald on 2005-05-08
[QUOTE=anon.irisX]I love my Kubuntu, but i have no idea how to install stuff.  I was quite disappointed with the fact it didn't seem to come with much installed.

Two things it didn't install that I very much want/need are the GIMP and XMMS.

I can easily download the latest versions of both, (except for the GIMP) and already have XMMS.  

So what now?  A lot of people mention the apt-get prefixtural command, but isn't that just for when downloading programs?  

Because I have one old computer with the internet and my new one which has Kubuntu.  I don't really plan on getting internet on this one; I just put the things on disc.

Can someone please help me out with this?  Thanks a million.[/QUOTE]
 You can use your Kynaptic Package Manager, if I am correct, it's in your **Systems** tab in your (K)Menu button on the taskbar.

Also if you can't find it, *just incase* type in a terminal window **sudo kynaptic** and that will bring it right up :)

Post any other quetions, and we'll be more than happy to help you:)

---

### Post by anon.irisX on 2005-05-08
[QUOTE=BB]You can use your Kynaptic Package Manager, if I am correct, it's in your **Systems** tab in your (K)Menu button on the taskbar.

Also if you can't find it, *just incase* type in a terminal window **sudo kynaptic** and that will bring it right up :)

Post any other quetions, and we'll be more than happy to help you:)[/QUOTE]
 Yeah I've been to Kynaptic, but it doesn't seem to have anywhere I can just install stuff from.

---

### Post by MaX on 2005-05-08
[QUOTE=anon.irisX]Yeah I've been to Kynaptic, but it doesn't seem to have anywhere I can just install stuff from.[/QUOTE]
 What do you mean?

You search for gimp, select it as to be installed, press apply and gimp downloads and installs.
You can't install files you've downloaded yourself without possibly breaking dependencies.
try dpkg -i gimpsdebianfile.deb in a shell.

---

### Post by jaclayton on 2005-05-08
OK.  I, too am having problems installing software.

I've added Universe and Multiverse to my sources, added the backports.  I've apt-get update'd and then tried to install scribus, firefox and inkscape.  

For Inkscape I get:

Package inkscape is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package inkscape has no installation candidate

For Scribus:

E: Couldn't find package scribus

And for Firefox:

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla-firefox: Depends: libatk1.0-0 (>= 1.9.0) but it is not installable
                   Depends: libbonobo2-0 (>= 2.8.0) but it is not installable
                   Depends: libbonoboui2-0 (>= 2.5.4) but it is not installable
                   Depends: libgconf2-4 (>= 2.9) but it is not installable
                   Depends: libgnome2-0 (>= 2.8.0) but it is not installable
                   Depends: libgnomecanvas2-0 (>= 2.6.0) but it is not installable
                   Depends: libgnomeui-0 (>= 2.8.0) but it is not installable
                   Depends: libgnomevfs2-0 (>= 2.9.90) but it is not installable
                   Depends: libgtk2.0-0 (>= 2.6.0) but it is not installable
                   Depends: libpango1.0-0 (>= 1.8.1) but it is not installable
E: Broken packages


This is a works machine, so I don't have the time or the patience to install Gentoo (which I run at home) - but I've just spent 2 hours trying to fix the above problems and am running out of patience.

Any suggestions?

---

### Post by cwaldbieser on 2005-05-08
In response to anon.IrisX's original question, it sounds like you want to either install additional packages from your CD-ROM, or from some other kind of media because you don't plan on hooking your (K)Ubuntu PC up to a network with Internet access.

You should be able to use apt-get/synaptic/knaptic to install packages from the CD-ROM.  There is usually a repository that starts with a CDROM:// URL (or something similar).

If you have the actual .deb files in a directory somewhere and you want to install them, you can use dpkg, though I am somewhat rusty on the exact syntax since I haven't used it in a while.  Something like:

```
$ sudo dpkg --install debfile.deb
```

apt-get is really a front end for dpkg, so the two will work together.  I think there might be some way to set up a directory on your hard disc as a repository URL for apt-get, too, but I have never tried it.

---

### Post by jaclayton on 2005-05-09
OK.  Have now found a source of repositories that is allowing me to install what I was looking for!

For those interested (I know it's already been posted on these forums, but...) it was: [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

Now things seem to be installing in a nice and peachy way.  Now all I've got to do is persuade this box to talk to the Novell server and I'm golden.  Bye bye XP at work!

---

