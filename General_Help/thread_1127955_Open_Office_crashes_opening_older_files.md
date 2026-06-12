---
title: "Open Office crashes opening older files"
date: 2009-04-17
forum: General Help
---

### Post by Zhiro on 2009-04-17
Hi.  I just recently upgraded to 8.10 from 8.04 and all of my OOo documents do not open.  I can create new documents with OO, but whenever I try to open an older one, OO immediately closes and pops up with the recovery window (i.e. "Due to an unexpected error, OO crashed.  Your files will be recovered...", etc.).  Then, when I re-open OO, I get the normal recovery window and click to recover files.  It always says they are successfully recovered but do not show up.  If I opened it from the file icon on my desktop (as opposed to opening it from within OO), it immediately goes back to the "Due to an unexpected error..." window.

Any help would be much much appreciated! :D

P.S. I'm kind of a noob at Ubuntu, so full explanations would be handy.

System information that may be pertinent:
Ubuntu 8.10
OpenOffice 2.4 (?)

---

### Post by ajmorris on 2009-04-18
> **Zhiro said:**
> Hi.  I just recently upgraded to 8.10 from 8.04 and all of my OOo documents do not open.  I can create new documents with OO, but whenever I try to open an older one, OO immediately closes and pops up with the recovery window (i.e. "Due to an unexpected error, OO crashed.  Your files will be recovered...", etc.).  Then, when I re-open OO, I get the normal recovery window and click to recover files.  It always says they are successfully recovered but do not show up.  If I opened it from the file icon on my desktop (as opposed to opening it from within OO), it immediately goes back to the "Due to an unexpected error..." window.

Any help would be much much appreciated! :D

P.S. I'm kind of a noob at Ubuntu, so full explanations would be handy.

System information that may be pertinent:
Ubuntu 8.10
OpenOffice 2.4 (?)

Hi there,
since it seems you are getting an error in your GUI dialog pop-up box, that is not very informative, could you please open up your open office via a terminal, and go ahead and try to open your documents, then paste here the output in your terminal.
To open openoffice in yout terminal, run the terminal from your menus - (in accessories in gnome iirc) and type in the openoffice component, and press enter. If you are using the writer component of openoffice, the executable is called 'oowriter' so just enter in oowriter, and press enter, if you are trying to use a different component, just enter in 'oo' and press tab twice, this will give you a list of all executables in your PATH, starting with oo. Choose the relevant executable for your component, i.e oocalc for the calc component etc.

AJ

---

### Post by Zhiro on 2009-04-18
Thank you for the explanation about it.  I ran oowriter through terminal (Open Office seems to be working just fine with the spreadsheet, I haven't ever used the others yet.)  This is all I get from the terminal:

(soffice:8174): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

When I ran it the first time, I got the above, the second time I got:

(soffice:8244):

And then the rest same as above, I don't know if that means anything other than I tried to open a different file.  Thank you for the help!

---

### Post by ajmorris on 2009-04-19
> **Zhiro said:**
> Thank you for the explanation about it.  I ran oowriter through terminal (Open Office seems to be working just fine with the spreadsheet, I haven't ever used the others yet.)  This is all I get from the terminal:

(soffice:8174): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

When I ran it the first time, I got the above, the second time I got:

(soffice:8244):

And then the rest same as above, I don't know if that means anything other than I tried to open a different file.  Thank you for the help!

hmm, when openoffice crashed, you should have gotten some error messages in the terminal... strange. OK, run a backtrace and an strace on oowriter, (sending them to seperate files), then either upload the files here, or paste the contents of the files here using ```
 envelops.

Instructions on running a backtrace:
[CODE]sudo apt-get install gdb
gdb oowriter 2>&1 | tee gdb-oowriter.txt

```
then once inside the gdb prompt, run the following:
```
handle SIG33 pass nostop noprint
set pagination 0
run

```
after issuing run, oowriter will start, do your necessary steps to reproduce the crash.
Then once the application has crashed, run the following:
```
backtrace full
info registers
thread apply all backtrace
quit
```
And upload gdb-oowriter.txt to here.

Instructions on running the strace:
```
apt-get install strace
strace -Ff -tt oowriter 2>&1 | tee strace-oowrter.txt
```
and upload strace-oowriter.txt

Just to let you know, these are some standard steps in providing information for a bug report. I have been unable to load the ubuntu bug tracker as of yet, but there may already be a bug on this. Once i sift through your backtrace and strace, if it is something not easily fixable, i will check on the ubuntu bug tracker if a bug already exists, if not i'll ask you to file one :)
If this is the case, i might further need your assistance if you're up for it, in providing some more information, so i can create a patch for the bug. Although, this may not be a bug, and just something that can be fixed, just a heads up though :)

AJ

---

### Post by Zhiro on 2009-04-19
Alright, I wasn't able to do the GDB backtrace because when I try to load it, I get this error:

```
"/usr/bin/oowriter": not in executable format: File format not recognized
```

It still puts me into (gdb) and I can get through SIG33 and Set pagination, but when I tell it to run, it gives me this:

```
Starting program:
No executable file specified.
Use the "file" or "exec-file" command.
```

So GDB isn't working yet, but I got strace to work, so here's the file:

Just kidding, apparently 2.01MB exceeds the 19.5K limit of .txt files for this forum.  Further instructions would be helpful? :D  Thank you for being quite helpful thus far, and yes, I'm willing to continue providing information if it helps fix the bug.

---

### Post by ajmorris on 2009-04-19
ah, i did a bit of digging, it seems to debug openoffice components, you need to install the following packages:
> openoffice.org-writer-dbgsym openoffice.org-base-core-dbgsym openoffice.org-base-dbgsym openoffice.org-core-dbgsym
Please install those, then repeat the gdb steps i outlined :)

for the strace, open the text file in a text editor, copy the entire contents, and paste it here with [code] envelops around it. 

AJ

---

### Post by Zhiro on 2009-04-20
*sigh* I tried to install those with sudo apt-get and it tells me it couldn't find the package.

I also tried to upload the strace in the code tabs around it but it takes too long to upload it to the forum and it cuts me off (if it takes over 60 seconds UbuntuForums tells me it reached its limit and kills it).

So.  Where to from here?  Is there any way to condense the strace or do you have ideas of how to get those packages for OO?  Sorry my computer sucks at being cooperative, and I continually appreciate your help on the subject! =D

---

### Post by ajmorris on 2009-04-20
> **Zhiro said:**
> *sigh* I tried to install those with sudo apt-get and it tells me it couldn't find the package.

I also tried to upload the strace in the code tabs around it but it takes too long to upload it to the forum and it cuts me off (if it takes over 60 seconds UbuntuForums tells me it reached its limit and kills it).

So.  Where to from here?  Is there any way to condense the strace or do you have ideas of how to get those packages for OO?  Sorry my computer sucks at being cooperative, and I continually appreciate your help on the subject! =D

ah, sorry, it seems those packages aren't in the default intrepid repos, add the following repos to /etc/apt/sources.list:
```
deb http://ddebs.ubuntu.com intrepid main universe
deb http://ddebs.ubuntu.com intrepid-updates main universe
deb http://ddebs.ubuntu.com intrepid-proposed main universe
deb http://ddebs.ubuntu.com intrepid-security main universe
```

then ```
sudo apt-get update
``` and install the relevant packages for the backtrace.
For the strace, you could try uploading it to pastebin.ca or even the txt file to filebin.ca


AJ

---

### Post by Zhiro on 2009-04-21
I added those repos to the /etc/apt/sources.list, but I still get this issue with doing apt-get update (I was getting this before too).  After it reads through all the packages and Hits all the sites it's supposed to, it gives me this:

```
W: GPD error: http://ddebs.ubuntu.com intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ECDCAD72428D7C01
W: GPD error: http://ddebs.ubuntu.com intrepid-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ECDCAD72428D7C01
W: GPD error: http://ddebs.ubuntu.com intrepid-proposed Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ECDCAD72428D7C01
W: GPD error: http://ddebs.ubuntu.com intrepid-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ECDCAD72428D7C01
W: You may want to run apt-get update to correct these problems

```

So I run apt-get update again and get the same errors.

---

### Post by Zhiro on 2009-04-22
Alright, so I decided that since it seems a lot of my problems could potentially be stemming from missing repositories or such things, here's my /etc/apt/sources.list so you can compare it and let me know if there are any major problems?  Thanks!

```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
deb http://archive.ubuntu.com/ubuntu intrepid main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu intrepid main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu gutsy universe
# deb-src http://archive.ubuntu.com/ubuntu gutsy universe

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse

## deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# deb http://ppa.launchpad.net/dell-team/ubuntu gutsy main
# deb-src http://ppa.launchpad.net/dell-team/ubuntu gutsy main

# deb http://ppa.launchpad.net/dell-team/ubuntu hardy main
# deb-src http://ppa.launchpad.net/dell-team/ubuntu hardy main
# deb http://ppa.launchpad.net/compiz/ubuntu hardy main
deb http://archive.ubuntu.com/ubuntu intrepid-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu intrepid-updates restricted main multiverse universe
# PulseAudio Fixes - http://ubuntuforums.org/showthread.php?t=789578
deb http://ppa.launchpad.net/psyke83/ubuntu intrepid main
deb-src http://ppa.launchpad.net/psyke83/ubuntu intrepid main
```

---

### Post by ajmorris on 2009-04-22
yep, your repositories are out... AFAIK, you can not put your repositories on a single line like you have it:
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid main restricted universe multiverse

if you want all those repos, they must be put on seperate lines, i.e:
```
deb http://archive.ubuntu.com/ubuntu intrepid main 
deb http://archive.ubuntu.com/ubuntu intrepid restricted
deb http://archive.ubuntu.com/ubuntu intrepid universe 
deb http://archive.ubuntu.com/ubuntu intrepid multiverse
```

please make the corresponding adjustments, then run ```
sudo apt-get update && sudo apt-get upgrade
``` This will update your packages list to the remote on on the servers, then do an upgrade of all outdated packages.

As for your signiature verification errors, you can rectify them by doing the following:

```
gpg --keyserver keyserver.ubuntu.com --recv-key 428D7C01
gpg --check-sigs 428D7C01
gpg -o - --export 428D7C01 | sudo apt-key add -
```

AJ

---

### Post by Zhiro on 2009-04-23
Alright, I made the corresponding changes to my sources.list and updated a couple packages.  I'm still getting the error with the GPG ones though, so I tried your solution, and I get this:

```
gpg: WARNING: unsafe ownership on configuration file `/home/james.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
```

I'm also confused because here are my permissions for ~/.gnupg

```

$ls -ld ~/.gnupg
drwx------ 2 james james 4096 2009-04-23 00:00 /home/james/.gnupg
$ls -l ~/.gnupg
total 8
-rw------- 1 james james 28 2008-07-30 23:05 gpg.conf
-rw------- 1 james james  0 2008-07-30 23:05 pubring.gpg
-rw------- 1 james james  0 2008-07-30 23:05 secring.gpg
-rw------- 1 james james 40 2008-07-30 23:05 trustdb.gpg
```

---

### Post by Zhiro on 2009-04-27
Alright, I got fed up with trying to fix it, so I upgraded it to Open Office 3.0 and now everything works.  Thank you so much for your help though!

---

