---
title: "Installing dvd+rw-tools-6.1 and latest K3b from source"
date: 2006-04-19
forum: Desktop Environments
---

### Post by casfindad on 2006-04-19
I am having trouble burning video DVDs with K3b. The program appears to exit cleanly, but the resulting disk will only play in my computer DVD drives, not in my standalone player. Moreover, the video (ripped and transcoded with K9copy) will only play about 70-80% through on the new disk and then stops. If I check the vob files created by K9copy, the entire video seems to have been transcoded successfully, however. Other strange video DVD burning symptoms include the inability to set my write speed to a lower value in K3B (it defaults to 4x, even when I choose "ignore"), and I am unable to write to a DVD-RW that has been re-formatted with K3b; writing to such a disk gives me a fatal input/output error.

Based on posts in other threads, it seems that updating my copy of dvd+rw-tools to version 6.1 (see for example [this]("http://www.ubuntuforums.org/showpost.php?p=711531&postcount=28")), and perhaps my copy of K3b could solve these problems. I'm having trouble installing both of these packages from source, however.

After downloading and extracting dvd+rw-tools-6.1 from [here]("http://fy.chalmers.se/~appro/linux/DVD+RW/tools/?M=D"), I get the following when I start the compile by typing "./configure":

```
bash: ./configure: No such file or directory
```

I then found instructions for installing dvd+rw-tools-6.1 from source [here]("http://www.linuxfromscratch.org/blfs/view/cvs/multimedia/dvd-rw-tools.html"). However, when I try typing
```
sudo make all rpl8 btcflash
```
I get the following error:
```
/bin/sh: m4: command not found
make[1]: Entering directory `/home/casey/LinuxOnly/ExtraApps/dvd+rw-tools-6.1'
make[1]: *** No rule to make target `dvd+rw-tools'.  Stop.
make[1]: Leaving directory `/home/casey/LinuxOnly/ExtraApps/dvd+rw-tools-6.1'
make: *** [all] Error 2

```

As a relative noob, I'm stuck at this point.

I'm also having trouble installing K3b 0.12.15. I tried to install using the instructions in this [post]("http://www.ubuntuforums.org/showpost.php?p=795642&postcount=2"). Unfortunately, auto-apt gives me lots of errors when I try to install various dependencies. Now when I type "sudo ./configure" I get the following:
```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
```

I then tried to solved this headers problem by following the instructions in this [thread.]("http://www.ubuntuforums.org/showpost.php?p=917955&postcount=2")

I was unable to find kapplication.h, and unfortunately installation of kdebase-dev failed as well. See this output:

```
casey@SagamoreHill:~$ sudo find / -name kapplication.h
Password:
find: /proc/18966/task: No such file or directory
find: /proc/18966/fd: No such file or directory
casey@SagamoreHill:~$ sudo apt-get install kdebase-dev
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
  kdebase-dev: Depends: kdelibs4-dev (>= 4:3.5-rc1) but it is not going to be installed
E: Broken packages
```

Now the #*!@ seems to have really hit the fan, as I am unable to install other packages using apt or adept. See, for example, what I get when I try to install kmymoney2:

```
casey@SagamoreHill:~$ sudo apt-get install kmymoney2
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libofx2 libosp4
The following NEW packages will be installed:
  kmymoney2 libofx2 libosp4
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7696kB of archives.
After unpacking 18.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
Authenticating /var/cache/apt/archives/libosp4_1.5.1.0-2ubuntu2_i386.deb ...
debsig: Origin Signature check failed. This deb might not be signed.

dpkg: error processing /var/cache/apt/archives/libosp4_1.5.1.0-2ubuntu2_i386.deb (--unpack):
 Verification on package /var/cache/apt/archives/libosp4_1.5.1.0-2ubuntu2_i386.deb failed!
Authenticating /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb ...
debsig: Origin Signature check failed. This deb might not be signed.

dpkg: error processing /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb (--unpack):
 Verification on package /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb failed!
Authenticating /var/cache/apt/archives/kmymoney2_0.8-6ubuntu2_i386.deb ...
debsig: Origin Signature check failed. This deb might not be signed.

dpkg: error processing /var/cache/apt/archives/kmymoney2_0.8-6ubuntu2_i386.deb (--unpack):
 Verification on package /var/cache/apt/archives/kmymoney2_0.8-6ubuntu2_i386.deb failed!
Errors were encountered while processing:
 /var/cache/apt/archives/libosp4_1.5.1.0-2ubuntu2_i386.deb
 /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb
 /var/cache/apt/archives/kmymoney2_0.8-6ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Is it me, or does this seem like a lot of grief to burn a video DVD? ](*,) 

Any help is very sincerely appreciated.

casfindad

---

### Post by Ramses de Norre on 2006-04-19
There is no configure script in the dvd+rw-tools directory, but I could just do make after untaring it.

---

### Post by casfindad on 2006-04-19
Thanks Ramses, I'll try make only in a moment. Presently I'm very concerned with my broken apt. I think I messed up when I followed your apt-run instructions for installing k3b. Any suggestions on how I can fix the failed verification errors with apt/apt-run?

---

### Post by casfindad on 2006-04-19
[QUOTE=Ramses de Norre]There is no configure script in the dvd+rw-tools directory, but I could just do make after untaring it.[/QUOTE]

Well, I tried typing make in the directory, and here is the error I received:

```
casey@SagamoreHill:~/LinuxOnly/ExtraApps/dvd+rw-tools-6.1$ sudo make
/bin/sh: m4: command not found
make[1]: Entering directory `/home/casey/LinuxOnly/ExtraApps/dvd+rw-tools-6.1'
make[1]: *** No rule to make target `dvd+rw-tools'.  Stop.
make[1]: Leaving directory `/home/casey/LinuxOnly/ExtraApps/dvd+rw-tools-6.1'
make: *** [all] Error 2

```

Any ideas?

---

### Post by casfindad on 2006-04-20
Bump. I still can't install dvd+rw-tools-6.1 or K3b, and it looks like apt is broken. Any help very much appreciated.

---

### Post by casfindad on 2006-04-20
[QUOTE=casfindad]Bump. I still can't install dvd+rw-tools-6.1 or K3b, and it looks like apt is broken. Any help very much appreciated.[/QUOTE]

I've solved the broken apt problem. See [this thread]("http://www.ubuntuforums.org/showthread.php?t=163172").

I still don't know how to install dvd+rw-tools-6.1, however. Any help appreciated. I think I've given up on installing the latest K3b.

casfindad

---

### Post by wpshooter on 2006-04-20
[QUOTE=casfindad]I've solved the broken apt problem. See [this thread]("http://www.ubuntuforums.org/showthread.php?t=163172").

I still don't know how to install dvd+rw-tools-6.1, however. Any help appreciated. I think I've given up on installing the latest K3b.

casfindad[/QUOTE]

Casfinddad:

     I don't think your problem is that you need a newer version of this K3b program but that you need an older version in order for it to work.

     I have been trying to get this program to properly copy and VERIFY copied files for several days now and if the research I did is correct, the newest version of this program will NOT work properly with the later versions on the Linux kernel (at least the one that is being used in Ubuntu 5.10).

     I am serious beginning to wonder if this Ubuntu/linux O/S is ready for prime time !!!  It seems to do fine in the areas of internet connection/surfing and e-mail sending/receiving but most every other application type I try seems to have some type of problem with it.

     Good luck.

---

### Post by casfindad on 2006-04-20
[QUOTE=wpshooter]Casfinddad:

     I don't think your problem is that you need a newer version of this K3b program but that you need an older version in order for it to work.

     I have been trying to get this program to properly copy and VERIFY copied files for several days now and if the research I did is correct, the newest version of this program will NOT work properly with the later versions on the Linux kernel (at least the one that is being used in Ubuntu 5.10).

     I am serious beginning to wonder if this Ubuntu/linux O/S is ready for prime time !!!  It seems to do fine in the areas of internet connection/surfing and e-mail sending/receiving but most every other application type I try seems to have some type of problem with it.

     Good luck.[/QUOTE]

Thanks, wpshooter. I share your frustration at times. I definitely feel that Ubuntu is not ready for "prime time", mainly because too much time is spent configuring things as opposed to getting actual work done. That said, I think it will improve with community support (i.e. people using it and giving feedback to developers). Free software, my desire to learn more about computer administration, the spirit of FOSS and the Ubuntu community keep me using it at home, but the reliabilty, tremendous ease-of-use and apps I need for work keep me using Mac OSX for my job. If some prognosticators are right and OSX is released for generic x86 hardware, however, I'll set up my home machine to dual-boot in a heartbeat.

Re: K3b and kernel versions, please provide a link if possible so I can follow up. What you say may certainly be true, but as I note in my first post, some Ubuntu users apparently have solved the video burning problem by updating dvd+rw-tools. I also see that the dapper repositories have K3b 0.12.14, which is awfully close to the latest 0.12.15.

---

