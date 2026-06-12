---
title: "Updating a package from source code"
date: 2009-01-27
forum: General Help
---

### Post by TTFN on 2009-01-27
Using source code downloaded from Lame's site, I am trying to figure out how to update a package I installed from source (v 3.97) with a newer version that is also built from source (v 3.98.2).

I chose Lame for two reasons.  First, 3.98.x isn't available in Hardy and I would like to use the newer version.  Second, I want to learn about installing from source code and thought that Lame would be relatively easy compared to other packages.

Using the online documentation I've been able to get through most of the compiling and installing with minimal trouble.  I now have 3.97 installed from source.  (I'm using checkinstall so that it is also added to the package manager.)

Next I do the same process for version 3.98.2 - it configures, makes, then it create the .deb package, but won't install because a package with the same name is already installed.  Which there is.

I haven't been able to find any documentation that tells how to update a manually installed package easily, with (hopefully) a single "update" type command.  This leads me to believe that I have to remove the first package manually, then manually install the newer package.  Is this the only way?

If someone could point me to the right documentation, or help explain the right procedure I would greatly appreciate it.

Thanks.

---

### Post by oldos2er on 2009-01-27
AFAIK you should uninstall the older version before installing the newer one. I say this with no authority other than having read that advice on this forum, and personal experience.

---

### Post by TTFN on 2009-01-27
I appreciate the response.  While I was hoping for an all-in-one command, removing the old first then installing the new would be the cleaner way.

Thank you.  :)

---

### Post by jocko on 2009-01-27
You don't need to use checkinstall to generate a (fake) debian package, as the lame source code contains a real debian build directory.

Just install some dependencies:
```
sudo apt-get build-dep lame
sudo apt-get install build-essential fakeroot dpkg-dev
```Then unpack the lame source .tar.gz file and:
```
cd [COLOR=Blue]/path/to/lame/source[/COLOR]
chmod a+x debian/rules
fakeroot debian/rules binary
```That will make the packages lame, libmp3lame0 and libmp3lame0-dev for you, and they will be *real* debian packages with proper dependency handling and will be properly handled by apt/dpkg (i.e they will not overwrite files installed by other packages without warning like checkinstall (or any other non-debian install method) may do).

---

### Post by TTFN on 2009-01-27
Thanks, jocko.  I'll give it a try.

---

