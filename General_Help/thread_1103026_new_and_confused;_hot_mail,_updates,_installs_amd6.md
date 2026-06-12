---
title: "new and confused; hot mail, updates, installs amd64"
date: 2009-03-22
forum: General Help
---

### Post by george703 on 2009-03-22
Hello All;
   I am new and am having three major issues, that i need help with.
A)i cant open letters in hot mail
B)i cant update repositories
C)i cant install packages, error cant install on your machine type amd64

any help would be appreciated
                                thanks george703

---

### Post by linuxisevolution on 2009-03-22
> **george703 said:**
> Hello All;
   I am new and am having three major issues, that i need help with.
A)i cant open letters in hot mail
B)i cant update repositories
C)i cant install packages, error cant install on your machine type amd64

any help would be appreciated
                                thanks george703

You most likely downloaded the wrong version of Ubuntu. You downloaded the amd64 version which should only be used if you have more than 4gb of ram. You should re-download Ubuntu and this time select the i386 version.

Good Luck!

---

### Post by 3Miro on 2009-03-22
> **linuxisevolution said:**
> You most likely downloaded the wrong version of Ubuntu. You downloaded the amd64 version which should only be used if you have more than 4gb of ram. You should re-download Ubuntu and this time select the i386 version.

Good Luck!

You can use AMD64 with less than 4GB of ram and still get many benefits. If your CPU supports it, it should be fine.

Were you able to install Ubuntu? Do you have any trouble with your internet connection in general (i.e. can you go to google and make some random search?). Do you get any error messages?

If you go to Applications -> Terminal and type

sudo synaptic

do you get any messages? What about if you try to update the repositories from that.

---

### Post by linuxisevolution on 2009-03-22
> **3Miro said:**
> You can use AMD64 with less than 4GB of ram and still get many benefits. If your CPU supports it, it should be fine.

Were you able to install Ubuntu? Do you have any trouble with your internet connection in general (i.e. can you go to google and make some random search?). Do you get any error messages?

If you go to Applications -> Terminal and type

sudo synaptic

do you get any messages? What about if you try to update the repositories from that.

The user is new so I suspected he would not know. He says that he wants to install a non-amd64 package, so he needs the i386 version.

---

### Post by oldos2er on 2009-03-22
> **george703 said:**
> Hello All;
   I am new and am having three major issues, that i need help with.
A)i cant open letters in hot mail
B)i cant update repositories
C)i cant install packages, error cant install on your machine type amd64
  

 Do you have a working internet connection? Sounds like there may be a problem there.

---

### Post by dacorr on 2009-03-22
second that, 64bit Dual Core AMD, 2GB runs no problem

---

### Post by 3Miro on 2009-03-22
It is possible to install a 32-bit package on a 64-bit system with --force-architecture:

sudo dpkg -i --force-architecture package_name

The issue is that depending on what you are installing, the problem might nor work. I have tried that for skype on 64-bit system and it works flawlessly, I have tried installing a driver for my printer and naturally it did not work. (Yea I know 32-bit drivers do not work on 64-bit system but it was worth the try :) ).

---

### Post by george703 on 2009-03-22
Hello All;
   update, took advice and reinstalled 32 bit and that took care of the hotmail issue.
   as far as the repository it is 90% better.
   i have not checked the download applications status yet, i will keep you all informed.
   my faith has been restored, i feared i would have to rejoin the dead in the world of microsoft. thank you all for your help
                      very grateful; george703

---

### Post by george703 on 2009-03-23
Hello All;
   this is another update, seems i was wrong about the repository issue, i am not able to fetch from server, seems as though it is a easy fix, i just dont know how! the error message said i need to make sure the preferences in the network connection have the repos. address correct. i did not see the address in preferences at all.
  can anyone tell me where to look and how to populate with correct address?
  i tried to change servers but since forgot how!
  that did not fix the issue than anyway.
  B)repository issue (cant fetch)
  C)install (have not checked yet)

---

### Post by oldos2er on 2009-03-23
To change repository servers, open System, Administration, Software Sources, click Download from, Other, Select Best Server.

---

### Post by george703 on 2009-03-23
are there updates i am not going to be able to get?

and i cant get adobe flash player to install?

any help would be appreciated!

---

### Post by oldos2er on 2009-03-23
"and i cant get adobe flash player to install?"

 Can you be more specific? If you see any error messages, please copy and paste them here.

---

### Post by george703 on 2009-03-23
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.  

Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/intrepid/main/binary-i386/Packages.bz2](http://ubuntu.cs.uaf.edu/ubuntu/dists/intrepid/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/intrepid/main/source/Sources.bz2](http://ubuntu.cs.uaf.edu/ubuntu/dists/intrepid/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

the top appears in the window header the bottom is the actual error.
does this mean anything to any one? and if so can you help me resolve the issue?
                 george:confused:

---

### Post by oldos2er on 2009-03-23
Can you please post the output of "cat /etc/apt/sources.list"?

---

### Post by george703 on 2009-03-24
Hello All;
   First off thank you all for your help. i am one of those slowly recocering microsoft people i gather a lot of linux people dont really like. i dont know my way around cammand line use yet. so thanks for your patience.
   
   update;
A) i am back on 32 bit
B) hot mail is now working great
C)[B]Updates are not working;i belive from reading around it is a hash sum mismatch. i found a post on this forum i will try tonight.
   i have broad band over powerline BPL as i live in Manassas,VA i use a netgear router. one of the configurations in my net work settings is a (loop back) does anyone know what that is? anyway i really need to resovle the hash sum issue so if any body has a sure fire resolution i would love to here it.
                    thanks george!

---

### Post by oldos2er on 2009-03-24
The presence of a network loopback device is normal: [http://en.wikipedia.org/wiki/Loopback](http://en.wikipedia.org/wiki/Loopback)

---

### Post by george703 on 2009-03-24
oldos2er  	
Re: new and confused; hot mail, updates, installs amd64
Can you please post the output of "cat /etc/apt/sources.list"? 

tried machine said it does not exist!:(

---

### Post by oldos2er on 2009-03-24
> **george703 said:**
> oldos2er      
Re: new and confused; hot mail, updates, installs amd64
Can you please post the output of "cat /etc/apt/sources.list"? 

tried machine said it does not exist!:(

Ok, Can you copy and paste that command and its output here?

---

### Post by george703 on 2009-04-01
george@george-desktop:~$ cat/etc/apt/sources.list
bash: cat/etc/apt/sources.list: No such file or directory
george@george-desktop:~$

---

### Post by george703 on 2009-04-01
sorry it took so long to answer

---

### Post by 3rdalbum on 2009-04-01
There should be a space in between "cat" and "/etc". This is because "cat" is a program that you want to run, and "/etc/apt/sources.list" is some information you are giving to that program. Without the space, Linux thinks you are trying to run a program called "cat/etc/apt/sources.list" which of course doesn't exist :-)

---

