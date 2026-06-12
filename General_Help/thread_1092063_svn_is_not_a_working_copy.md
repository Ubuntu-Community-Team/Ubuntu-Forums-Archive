---
title: "svn is not a working copy"
date: 2009-03-10
forum: General Help
---

### Post by alireza2 on 2009-03-10
Hi

I tried to install a software in Ubuntu,during the compile I faced this error message:
" svn: '.' is not a working copy "

Can you tell me how I can fix the error?

---

### Post by Yellow Pasque on 2009-03-10
Do you have svn installed?
```
sudo apt-get install svn
```

If so, please give more detail on what you're trying to do.

---

### Post by alireza2 on 2009-03-11
I tried the code to install svn,I had this message:

E: Couldn't find package svn

Where can I find the package to install?
I am going to install an audio software in my Desktop on the Ubunto server

---

### Post by oldos2er on 2009-03-11
Try 'sudo apt-get install subversion' instead.

---

### Post by lloyd_b on 2009-03-11
> **alireza2 said:**
> Hi

I tried to install a software in Ubuntu,during the compile I faced this error message:
" svn: '.' is not a working copy "

Can you tell me how I can fix the error?

That error is generated when you do an "svn up" command, and the current directory is not a working copy of an subversion repository.

You really need to take this one up with the maintainers of the software you're trying to install.  It sounds like they're trying to "svn up" as part of the "make" in order to get the most recent version, but that will only work correctly if you "checked out" the code ("svn co") from a subversion repository in the first place.

Lloyd B.

---

### Post by alireza2 on 2009-03-11
> **oldos2er said:**
> Try 'sudo apt-get install subversion' instead.
I did it,it didn't solve the problem!

---

### Post by alireza2 on 2009-03-11
> **lloyd_b said:**
> That error is generated when you do an "svn up" command, and the current directory is not a working copy of an subversion repository.

You really need to take this one up with the maintainers of the software you're trying to install.  It sounds like they're trying to "svn up" as part of the "make" in order to get the most recent version, but that will only work correctly if you "checked out" the code ("svn co") from a subversion repository in the first place.

Lloyd B.

I am a newbie in Ubuntu, can you tell me more what I should do to fix it ?

---

### Post by lloyd_b on 2009-03-11
> **alireza2 said:**
> I am a newbie in Ubuntu, can you tell me more what I should do to fix it ?
Could you tell us exactly what software it is you're trying to install?  As it is, we just don't have enough information to work with...

Lloyd B.

---

### Post by alireza2 on 2009-03-12
The software is "Wonder".But I think the problem is with my Ubuntu!

---

### Post by Yellow Pasque on 2009-03-12
Can you give a link to the software's webpage?

Also, post the output of:
```
svn --version
```

---

### Post by alireza2 on 2009-03-12
ver 1.5.1 (r32289)

I used "ls -a" command,I saw there is '.' and '..' in the directory,
Is there any relation between this '.' and the error?

The link of the software:
[http://sourceforge.net/project/showfiles.php?group_id=136020&package_id=299220](http://sourceforge.net/project/showfiles.php?group_id=136020&package_id=299220)

---

### Post by lloyd_b on 2009-03-13
First off, the "." and ".." are normal - "." refers to the current directory, and ".." is the parent directory.

I downloaded the tar.gz file, and here's what I had to do to get it compiled.  In a terminal window:```
sudo apt-get install liblo0-dev
sudo apt-get install libsndfile1-dev
sudo apt-get install fftw3-dev
sudo apt-get install libqt4-dev
sudo apt-get install scons
sudo apt-get install libjack-dev

```
Note that you may get an "already installed" message for one or more of these - I have no way of knowing exactly what you've already installed on your machine, so I listed everything *I* needed to install.

After that, "cd" into the directory where you unpacked the Wonder archive.  It's *probably* "wonder3.1.0", then:```
scons all=1
```
This should handle the compilation.  For the rest, I'd suggest reading the install file ("Install.txt", in the "documentation" subdirectory).

Lloyd B.

---

### Post by alireza2 on 2009-03-13
Thanks ,so usefull:D
Could you please tell me where I can find the svn copy? in the manual is written I should continue the rest of procedure from the root directory of received!! svn copy?

---

### Post by lloyd_b on 2009-03-13
> **alireza2 said:**
> Thanks ,so usefull:D
Could you please tell me where I can find the svn copy? in the manual is written I should continue the rest of procedure from the root directory of received!! svn copy?

"root directory of the svn copy" means, in this case, the directory you unpacked the archive to ("wonder3.1.0").  The author of that documentation apparently assumed that you'd be retrieving the code via svn, and never considered that people would be downloading a "tarball" (.tar.gz file containing all the sources).

(I don't know why they even mention svn, since they have support for svn turned off on the SourceForge site).

Lloyd B.

---

### Post by alireza2 on 2009-03-16
Thanks for your help.
I believe the manual of the software is old and is not up to date.

Cheers,;)

---

