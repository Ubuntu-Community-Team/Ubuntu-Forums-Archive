---
title: "installing gftp"
date: 2005-02-22
forum: Desktop Environments
---

### Post by #Greg on 2005-02-22
I've installed gftp easily on multiple installs, but now it isn't working:

me@ubuntu:~ $ sudo apt-get install gftp
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gftp: Depends: gftp-gtk (= 2.0.17-6) but 2.0.17-6ubuntu0.2 is to be installed
        Depends: gftp-text (= 2.0.17-6) but it is not going to be installed
E: Broken packages

Even when I attempt to install those dependencies it doesn't work, it's saying it needs a specific version, and can't find it or that they aren't going to be installed, even when those exact packages/versions are requested for install?

---

### Post by kassetra on 2005-02-22
[QUOTE=#Greg]Even when I attempt to install those dependencies it doesn't work, it's saying it needs a specific version, and can't find it or that they aren't going to be installed, even when those exact packages/versions are requested for install?[/QUOTE]

Ok, tell me what's in your sources.list file, also, have you tried running synaptic?  I installed gftp through synaptic without a hitch... if you want to use the apt-get command line, that's cool too.  :)

---

### Post by #Greg on 2005-02-22
I use apt-get for the simpler stuff and Synaptic for the stuff that requires configuring, both have their merits :)

Synaptic produces the same errors by the way, this is my sources list:

# deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

This is a newly-installed desktop so I don't have multiverse etc in there yet, but I shouldn't need any other repositories for gftp, surely?

---

### Post by kassetra on 2005-02-22
Aha!  I had to look at my own install to figure out what was up!
Do a search for gftp in synaptic- 
you want to install gftp-common and gftp-gtk, and you should be set, no need for the other "gftp" package.  (You may need to install ftp!)

---

### Post by kassetra on 2005-02-22
Also, I don't know if you know this, but your nautilus file manager has ftp built in: when you type [ftp://yadayada](ftp://yadayada) in the location bar, it will take you there for drag & drop ftp-ing... also firefox has an ftp extension to allow you to do ftp inside the browser.  :)

---

### Post by neighborlee on 2005-02-23
[QUOTE=kassetra]Aha!  I had to look at my own install to figure out what was up!
Do a search for gftp in synaptic- 
you want to install gftp-common and gftp-gtk, and you should be set, no need for the other "gftp" package.  (You may need to install ftp!)[/QUOTE]
-----------
that is correct BUT..synaptic refuses to 'cooporate' because it says:

gftp:
  Depends: gftp-gtk but 2.0.17-6ubuntu0.2 is to be installed
 Depends: gftp-text but it is not going to be installed

something has been replaced on the repository or something cause this has always worked in the past and  I refuse to use the convulted ftp ability of nautilus <G>

thx
nl

---

### Post by bioS on 2005-02-23
I have exactly the same problem today. 
Any solution ?
Thx,
nIcO

---

### Post by Seandq on 2005-02-23
Same problem here. I'm now led to assume this is a repo problem as 3 people have all had the problem on the same day.

---

### Post by ixus_123 on 2005-02-23
Yep, same problem here as of yesterday.

I have installed Ubuntu about 3 times now without problems all in the same way so I'm sure it's not a problem at the user end

---

### Post by Seandq on 2005-02-23
[QUOTE=Seandq]Same problem here. I'm now led to assume this is a repo problem as 3 people have all had the problem on the same day.[/QUOTE]
 Fixed. My workaround:

[http://archive.ubuntu.com/ubuntu/pool/main/g/gftp/gftp-gtk_2.0.17-6ubuntu0.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gftp/gftp-gtk_2.0.17-6ubuntu0.2_i386.deb)

Download that file, then save in /home/yourusername directory. Open a terminal.

Navigate to your home directory, then type **sudo dpkg -i ggftp-gtk_2.0.17-6ubuntu0.2_i386.deb**. It SHOULD work and gFTP will be installed.

---

### Post by Yukonjack on 2005-02-23
You might want to check this tread, it works.

[http://www.ubuntuforums.org/showthread.php?t=15929](http://www.ubuntuforums.org/showthread.php?t=15929)

---

### Post by #Greg on 2005-02-24
[QUOTE=kassetra]
Do a search for gftp in synaptic- 
you want to install gftp-common and gftp-gtk, and you should be set, no need for the other "gftp" package.  (You may need to install ftp!)[/QUOTE]

This worked for me, I just installed gftp-common and -gtk and it's fine. Repository has definately been borked somehow, though.

---

