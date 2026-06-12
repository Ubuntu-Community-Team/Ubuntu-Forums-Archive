---
title: "OK, I have a .deb file, now what?"
date: 2006-09-20
forum: Desktop Environments
---

### Post by mrcpu on 2006-09-20
I want to run daemontools on my ubuntu dapper VPS.  I've managed
to find on the ubuntu site a daemontools-installer_0.76-9_all.deb file, and downloaded it.

Now what?  I looked through aptitude, daemontools isn't in there, I don't have X, so synaptics is out (and it isn't even installed).

So how the heck do I actually have this thing unpack itself so I can run the installer?

Can debian packages be used?  Ultimately, I want djbdns and daemontools, but for now, just getting my feet wet.

Of course, I can build the stuff from source, and that was OK, but I need a better understanding of how the package stuff works under LInux, I'm more used to the ports/packages system under FreeBSD.

Any tips appreciated.

THanks.

---

### Post by nikhilk on 2006-09-20
If you do not mind reading "man" pages you can do with 
```
man dpkg
```
```
man apt-get
```

Otherwise Google is always a good alternative.
HTH

---

### Post by yota on 2006-09-20
Just a hint (offtopic):

mounting .iso files is a native function on linux:

```

mount -o loop imagefile.iso /path/to/mount/point

```
other formats can be converted to iso and the mount action can be put in a script and associated with .iso files.

Hope this helps.

---

### Post by Johnathon on 2006-09-20
The command you want is

```
dpkg -i filename_of_installer.deb
```

That will install the .deb.

---

### Post by mrcpu on 2006-09-20
Yeah, this VPS has no man pages...  'man : command not found'...

dpkg -i *.deb gripes about needing build-essential and patch and debhelper...  OK, so apt-get install build-essential just find more unmet dependencies.

SO there's gotta be some kind of tool that does this recursively and downloads and installed the dependencies... 

Something like dpkg -ir *.deb...

If I run aptitude, and then find build-essential and try to install it, then I get "FATAL: Unable to fork"....

I am ssh'd in as root, but it doesn't give me any more details...

---

### Post by lamego on 2006-09-20
gdebi will install all the required depedencies (as long you have the proper repositories):

sudo gdebi filename_of_installer.deb

---

### Post by mrcpu on 2006-09-20
gdebi is "command not found".  I'm presuming that you guys are referring to some kind of graphical installer.

There is no X on this server, no kde, no nothing.  Not even make or gcc or any of that.  So walking the dependency chain I would presume that it would pull in all that development stuff.

But everything I select in aptitude just has more dependencies.

Of course, doing this under the GUI is no problem, but I need to do it "text-mode" style...

---

### Post by patrickfromspain on 2006-09-20
sudo nano /etc/apt/sources.list and uncoment all the repos (all lines starting with deb or deb-src). Then, control+o (o as in wOman) to save and control+X to exit nano.

sudo apt-get update and the you should be able to install anything.

---

### Post by mrcpu on 2006-09-20
Ah ha... I think I must be missing some repositories or something.

The only entry in /etc/apt is:

deb [http://archive.ubuntulinux.org/ubuntu](http://archive.ubuntulinux.org/ubuntu) dapper main

However, it sounds like there should be more.  There are no files
in /etc/apt/sources.list.d .

I wonder if these VPS guys stripped out a bunch of the choices to force people to upgrade...  Grrr.  (It's at vpslink.com).

---

### Post by patrickfromspain on 2006-09-21
Ok, I'll post my sources.list, case it helps:

> ####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

# Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse

# Ubuntu Commercial
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

###############################
### XGL Compiz Repositories ###
###############################
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://ubuntu.moshen.de/](http://ubuntu.moshen.de/) dapper eyecandy
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

##############################
### Automatix Repositories ###
##############################

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

##############################
###  Sources Repositories  ###
##############################

#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse

## created by automatixrepoamd64-4

---

### Post by mrcpu on 2006-09-22
Well, finally got closer.

Using my workstation version of Ubuntu, I was able to get synaptic to download the .deb files for all the dependencies.

I put 'em all in a dir, and ran dpkg -i *.deb, which kind of worked, but griped about certain things not being "configured".

So I ran apt-get update, which then revealed the -f option, which I ran, which then downloaded a couple missing dependencies, and did what I expected, which gave me working executrables when all was said and done.

SO I am a happy camper.  And I thank everybody for their help.

---

