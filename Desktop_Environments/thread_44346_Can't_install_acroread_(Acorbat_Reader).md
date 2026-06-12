---
title: "Can't install acroread (Acorbat Reader)"
date: 2005-06-25
forum: Desktop Environments
---

### Post by John Jason Jordan on 2005-06-25
Bless their little corporate heart, Adobe released Acrobat Reader 7.0 for Linux some time ago. But no matter what I try, it gives errors on install. Synaptic lists just acroread-debian-files, but this fails because it needs other files that are not present. And apt-get acroread fails with similar error messages.

I know there's an open source PDF reader that is installed by default, but I do a lot of work sending files to print shops. The slightest error could be very costly, so I really need the genuine thing. 

What's the secret to installing it?

---

### Post by Xian on 2005-06-25
Sounds like your sources.list is not pulling the repos necessary.
Listed below is my /etc/apt/sources.list. Does yours look similar?

If not, then modify accordingly and hit "Reload" in Synaptic.

```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

##Backports
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
```

---

### Post by John Jason Jordan on 2005-06-25
[QUOTE=Xian]Sounds like your sources.list is not pulling the repos necessary.
Listed below is my /etc/apt/sources.list. Does yours look similar?

Here is mine:

------
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe main restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://ndiswrapper.sourceforge.net/debian](http://ndiswrapper.sourceforge.net/debian) ./
-----

I should remove the last one, since I have ndiswrapper installed properly now, and it doesn't link to version 1.2 anyway.

And yes, I Reloaded when it did not appear properly. No change. :(

---

### Post by Xian on 2005-06-25
You may want to add the backports repo and try again.

```
##Backports
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
```

---

### Post by John Jason Jordan on 2005-06-25
[QUOTE=Xian]You may want to add the backports repo and try again.

```
##Backports
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
```[/QUOTE]
 OK, I added the two backsports sources. Then I reloaded Synaptic. And it still listed only acroread-debian-files. I tried to install it again, just in case the Backsports repositories might have helped, but I still get:

"Depends acroread, but it is not available."

And then the installation quits without installing anything.

Other suggestions? Anyone?

---

### Post by Xian on 2005-06-25
Make sure you don't have any apt preferences.

Use the command below and if there is any text in the file remove it and save it as a blank document.

```
$ sudo gedit /etc/apt/preferences
```
If the document is already blank then the only other recouse I can think of is to duplicate my config on your system, since I am not having any issues downloading and installing acroread.

Rename your current sources.list as this will be your back-up, and then copy and paste mine (see previous post) into your text editor and save it as /etc/apt/sources.list. Do a 'sudo apt-get update' session and then issue the command below:
```
sudo apt-get install acroread
```
Listed below is my output of that command.
Note that it is pulling the package from the backport repos.
```
$ sudo apt-get install acroread --reinstall
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 23.4MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  acroread
Install these packages without verification [y/N]? y
[color=red]Get:1 ftp://ftp2.caliu.info hoary-extras/restricted acroread 7.0-0.9~5.04ubp1 [23.4MB]
Fetched 23.4MB in 2m30s (155kB/s)[/color]

Preconfiguring packages ...
(Reading database ... 106991 files and directories currently installed.)
Preparing to replace acroread 7.0-0.9~5.04ubp1 (using .../acroread_7.0-0.9~5.04ubp1_i386.deb) ...
Unpacking replacement acroread ...
Setting up acroread (7.0-0.9~5.04ubp1) ...
$
```

---

### Post by John Jason Jordan on 2005-06-25
OK, here is what happened:

-----
jjj@Devil5:~$ sudo apt-get install acroread
Password:
Reading package lists... Done
Building dependency tree... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  acroread-debian-files
E: Package acroread has no installation candidate
jjj@Devil5:~$
-----

And there are no apt preferences. :(

---

### Post by Xian on 2005-06-25
My next post will at least get you that package installed on your system, but in the meantime please post the _entire_ output that is the result of issuing the command below. I want to see precisely what apt is doing when it pulls from your sources.list.

```
$ sudo apt-get update
```

---

### Post by Xian on 2005-06-25
Okay, let's just get that acroread package on your system.
That's the main thing right now.

Download it here directly from the backport repo: [acroread_7.0-0.9~5.04ubp1_i386.deb](http://ftp2.caliu.info/backports/dists/hoary-extras/restricted/binary-i386/acroread_7.0-0.9~5.04ubp1_i386.deb)

Place that file in your /home/username directory and then issue the command listed below. That will install acroread but we still need to resolve the larger problem.
```
$ sudo dpkg -i acroread_7.0-0.9~5.04ubp1_i386.deb
```

---

### Post by John Jason Jordan on 2005-06-25
OK, now I have the answer.

This is the error message I got:

dpkg: error processing acroread_7.0-0.9~5.04ubp1_i386.deb (--install):
package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
acroread_7.0-0.9~5.04ubp1_i386.deb

So now I can guess why it is not listed in Synaptic. Synaptic must know that this is an amd64 installation. And perhaps there is no 64-bit version of acroread. Therefore it does not appear.

That's a guess, but it makes sense, in the light of the above error message.

But I _really_ need Acrobat Reader. Don't tell me I'm going to have to get a Windows computer to print from. Is there any kludge for getting a 32-bit program to run on a 64-bit system? Doesn't the amd64 process 32-bit data anyway?

I don't absolutely have to have version 7.0. Is there perhaps an older version available in 64-bit mode? (Grasping at straws here.)

:( :( :( :(

---

### Post by Xian on 2005-06-25
You said you got errors when trying to use the official Acroread installer?

Here's what I used: [AdbeRdr70_linux_enu.tar.gz](http://ardownload.adobe.com/pub/adobe/reader/unix/7x/7.0/enu/AdbeRdr70_linux_enu.tar.gz)

_Directions:_
1. Download the Acrobat 7.0 Reader installer application.
2. After the download is complete, quit your Web browser. 
3. Double-click the newly downloaded file "AdbeRdr70_linux_enu.tar.gz" and follow the instructions on your screen. 
4. Uncompress or gunzip the file. 
5. Untar the file and read the text file for specific installation steps. 
6. The installation procedure will ask you to read and accept the Electronic End-User License Agreement.

---

### Post by John Jason Jordan on 2005-06-26
[QUOTE=Xian]You said you got errors when trying to use the official Acroread installer?

Here's what I used: [AdbeRdr70_linux_enu.tar.gz](http://ardownload.adobe.com/pub/adobe/reader/unix/7x/7.0/enu/AdbeRdr70_linux_enu.tar.gz)

_Directions:_
1. Download the Acrobat 7.0 Reader installer application.
2. After the download is complete, quit your Web browser. 
3. Double-click the newly downloaded file "AdbeRdr70_linux_enu.tar.gz" and follow the instructions on your screen. 
4. Uncompress or gunzip the file. 
5. Untar the file and read the text file for specific installation steps. 
6. The installation procedure will ask you to read and accept the Electronic End-User License Agreement.[/QUOTE]

Evidently you posted that just after I posted my sad resutls from your previous suggestion. It turns out that the problem is that I am on 64-bit Ubuntu 5.04 and Acrobat Reader is 32-bit only and will refuse to install on a 64-bit system. 

So now I am trying to figure out why, and if there is an alternative. After all, the AMD64 chip can run 32-bit code. Can't Ubuntu-64? I can understand occasional problems with drivers, but surely 32-bit applications can be run on 64-bit Ubuntu. This isn't making a lot of sense to me.

---

### Post by tonyw50 on 2005-06-26
Xian,

I'm also having problems installing AcroRead.  Following your instructions, I got an error message saying it needs libgcc1 version 1:4.0.0-7.  I'm relatively new to Linux and Ubuntu and can't figure out how to load it into Synaptic. I have 1:4.0pre6ubuntu7 installed.  I'm using a Thinkpad 600E.

---

### Post by John Jason Jordan on 2005-06-29
I'm a total n00n at Linux, but someone on a local Linux e-list just said he had 32-bit plugins installed in 64-bit Gentoo, and Acrobat 7.0 as well.

I asked him how he managed to install Acrobat 7.0 in a 64-bit kernel. He said it was easy (yeah, easy for someone with his experience!). He said you create chroot, which is a 32-bit kernel running inside your 64-bit kernel. 

I don't know any more about it than that. But evidently it can be done. I shall be waiting here for instructions!

---

### Post by andrewL on 2005-06-29
Hi there,
  I wasn't able to view files with acrobat until I read this.  Thanks a lot.

cheers,
Andrew

:-)

---

### Post by Zifnab on 2005-07-02
It won't let me install it either. Well actually, I *had* it installed, and then it said that to upgrade I had to remove the Mozilla plugin and some Debian plugin for it, so I relented and said okay, since I kept getting annoying messages about it whenever I let the auto-update program run. And then it gives me some crab about libc6 versions.

But regardless, I've been using a program called Xpdf the whole time anyhow and it works just fine. So if anyone else can't isntall acroread, I suggest Xpdf.

---

