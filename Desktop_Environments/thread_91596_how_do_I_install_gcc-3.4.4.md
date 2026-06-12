---
title: "how do I install gcc-3.4.4"
date: 2005-11-17
forum: Desktop Environments
---

### Post by hollowhead on 2005-11-17
I need to install gcc-3.4.4 primarily to get my modem up and running the modules were compiled on gcc-3.4.5 it won't compile using 4.02.  It would be fair to say I was surprised to find my breezy 5.1 came with gcc-4.02 even though it was not built with that version of gcc (apparently).  Version 4 according to my modest researches "has issues" as they say which may be part of the reason why I cannot get anything to install (that and lots of missing libs).  I tried running apt-get install gcc-3.4 only to get a what an earth are you on about can't find it message.  I downloaded gcc-3.4.4.tar.bz2 and unpacked it.  Tried running apt-get install gcc-3.4 install again in its dir.  No joy of course.  Is there a simple way of installing it?  I have started to read the configure/make/make install instructions but they are complicated and I haven't much faith gcc3.4 will compile with 4.02.  Can anyone help please-I'm getting desperate.  Hollowhead

---

### Post by 23meg on 2005-11-17
```
sudo apt-get install gcc-3.4 gcc-3.4-base
``` should help. What error messages are you getting when you do this?

---

### Post by tseliot on 2005-11-17
Perhaps it doesn't find (and doesn't install) gcc-3.4 because the internet connection is not available.

Do this:
```
Insert your Ubuntu CD in your cd reader
Open Synaptic
Then select the menus Edit/Add Cdrom
and add your Ubuntu CD
```

```
Then click on Reload
click on Search
Type "gcc"
select and install gcc-3.4 (not only the base package).

Close synaptic.
```

If you need to force the installer of your drivers to use gcc-3.4, follow these steps:

```
sudo passwd root
```
(and set the root password which you will need later)

then

```
su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
```

Now you can launch the command which failed before.

---

### Post by az on 2005-11-17
gcc3-4 is not *on* the cd.

"That will never happen again!" - Matt zimmerman.

I can make you a cd image that you can download, burn and add it to synaptic, if you want.

---

### Post by tseliot on 2005-11-17
[QUOTE=azz]gcc3-4 is not *on* the cd.

"That will never happen again!" - Matt zimmerman.

I can make you a cd image that you can download, burn and add it to synaptic, if you want.[/QUOTE]

Or s/he can download the packages (according to his/her architecture: i386, a,d64,etc) from [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/")

and install them manually:

cd /home/your_username/folder_in_which_you_downloaded_the_debfiles
sudo dpkg -i nameofthefile.deb

---

### Post by hollowhead on 2005-11-18
Cheers for the replies.  According to synaptic gcc-3.3 base is installed.  I will try both the cd option and downloding from the respository.  I have a fast internet connection here.  I'll let you know what happens.  Ta.  Hollowhead

---

### Post by tseliot on 2005-11-18
BTW there's a guide about [HOWTO: Install gcc-3.4 via apt-get without an Internet connection]("http://www.ubuntuforums.org/showthread.php?t=79896")

---

### Post by hollowhead on 2005-11-18
Cheers howto looks reasonably straightfwd I give it a try.  Hollowhead

---

### Post by hollowhead on 2005-11-19
I've tried the install gcc-3.4.4 howto.  I cannot get beyond creating the packages.  Created dir in home/neil so 
/home/neil/gcc-3.4

sudo apt-get install build-essential
dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz

I get a cannot find dkpg-scanpackages error and although Packages is created in the ~/gcc-3.4 dir but it then exits with this error.  Both build-essential and bin-utils are installed. dkpg-scanpackages exists and is in my path bin/usr I think.  Tried running the above as root as well since permissions on dkpg-scanpackages were not full same errors.  How do I get round this?  ta.

---

### Post by tseliot on 2005-11-19
[QUOTE=hollowhead]I've tried the install gcc-3.4.4 howto.  I cannot get beyond creating the packages.  Created dir in home/neil so 
/home/neil/gcc-3.4

sudo apt-get install build-essential
dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz

I get a cannot find dkpg-scanpackages error and although Packages is created in the ~/gcc-3.4 dir but it then exits with this error.  Both build-essential and bin-utils are installed. dkpg-scanpackages exists and is in my path bin/usr I think.  Tried running the above as root as well since permissions on dkpg-scanpackages were not full same errors.  How do I get round this?  ta.[/QUOTE]

I think you should ask the author of the guide (on his thread) because I don't know how to help you.

---

### Post by hollowhead on 2005-11-22
Cheers dpkg -i worked and my modem drivers working although any time I install software using Synaptic it goes through the modem configuration routine again.  So I downloaded DIA and installed using Synaptic I had set country etc for the modem.  Any way round this?  Hollowhead.

---

