---
title: "Add/Remove applications does not work. Major Failure?"
date: 2008-12-24
forum: General Help
---

### Post by fbjoey on 2008-12-24
"Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

This us the message i get after I start up the Add/Remove applications application. I tryed to reload the software and stuff and just got this message in the terminal
```
fbjoey@Fr3d:~$ sudo apt-get update
Hit http://security.ubuntu.com intrepid-security Release.gpg
Ign http://security.ubuntu.com intrepid-security/main Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid Release.gpg
Hit http://gb.archive.ubuntu.com intrepid/main Translation-en_GB
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_GB
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_GB
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com intrepid-security Release
Hit http://gb.archive.ubuntu.com intrepid/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid-updates Release.gpg
Hit http://gb.archive.ubuntu.com intrepid-updates/main Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Translation-en_GB
Hit http://security.ubuntu.com intrepid-security/main Packages
Hit http://gb.archive.ubuntu.com intrepid Release
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/main Sources
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://gb.archive.ubuntu.com intrepid-updates Release
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://gb.archive.ubuntu.com intrepid/main Packages
Hit http://gb.archive.ubuntu.com intrepid/restricted Packages
Hit http://gb.archive.ubuntu.com intrepid/main Sources
Hit http://gb.archive.ubuntu.com intrepid/restricted Sources
Hit http://gb.archive.ubuntu.com intrepid/universe Packages
Hit http://gb.archive.ubuntu.com intrepid/universe Sources
Hit http://gb.archive.ubuntu.com intrepid/multiverse Packages
Hit http://gb.archive.ubuntu.com intrepid/multiverse Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/main Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/main Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Sources
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
fbjoey@Fr3d:~$ 

```

Can anybody help?

Cheers
Joe

---

### Post by SuperSonic4 on 2008-12-24
```
sudo dpkg --configure -a
``` like it says at the bottom of the code ;)

---

### Post by fbjoey on 2008-12-24
well that makes me look simple but now ```
dpkg: requested operation requires superuser privilege

```

I am the only user. I'm so confused

---

### Post by redsoxreed on 2008-12-24
you have to put "sudo" before the dkpg.  It will ask you for your password and run it with root privileges.

---

### Post by fbjoey on 2008-12-24
Okay now it come up with 

```
Operating System Distributor License for Java v1.1 (DLJ)                  &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618; 
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618; 
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618; 
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618; 
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618; 
 &#9474; TERMS OF THE AGREEMEN
```

but i cant see how to accept the terms, sorry. i'm sure you can tell i only just installed linux

---

### Post by redsoxreed on 2008-12-24
I think you have to hold down enter to make it scroll through the agreement.  At the bottom, I think there is a [Y/n] box, asking if you accept the agreement, where you would enter the button "Y" and press enter.

---

### Post by GuitarRocker2562 on 2008-12-24
Yea, you just have to accept the agreement for Java. No biggie. Enjoy Ubuntu! Oh, and if the enter doesn't scroll, try space bar or tab.

---

### Post by fbjoey on 2008-12-24
yer i can scroll to the bottom.

The end looks like this
```
 For inquiries please contact: Sun Microsystems, Inc., 4150 Network        &#9618; 
 &#9474; Circle, Santa Clara, California 95054, U.S.A.                             &#9618; 
 &#9474;                                                                           &#9646; 
 &#9474; DLJ v1.1                                                  27APR2006ANS    &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>  
```

I cant type anything from what I can see and I cant install anything from the terminal either. 

and thanks I will enjoy Ubuntu as much as I can, I think it will be much easer to use once I figure the controls.

---

### Post by redsoxreed on 2008-12-24
Can you select/highlight the "<Ok>" with the arrow keys?  Or just try pressing enter once you're at the bottom.

---

### Post by fbjoey on 2008-12-24
I can highlight it but not select it and when I hit ender nothing happens.

---

### Post by xslimmiejimmiex on 2008-12-24
Press tab, then it will highlight OK and then you should be able to press enter

---

### Post by redsoxreed on 2008-12-24
Did you use the arrow keys or the mouse?
Edit: Try pressing Tab like xslimmiejimmiex suggests

---

### Post by fbjoey on 2008-12-24
Wooooo!Tab worked :D 
and the app now works, but i have forgot what I was going to do with it.

Cheers to everyone
Joe

Merry Christmas!!!!!!!!!!!

---

### Post by MaxIBoy on 2008-12-24
Cool that you got it working. Marking the thread as "solved" is good form.



Something you'll have to understand is that in UNIX-like operating systems, there's always a special "root" user. This "root" user is like the administrator, only with far more power and the ability to seriously mess things up. "Sudo" runs a single command as the root user, so you can use "sudo" with one command that you understand, and you don't have to risk messing things up with commands you don't understand. Unless you use "sudo" (or "gksudo" to launch graphical programs,) you actually won't have permission to do any harm.

---

### Post by fbjoey on 2008-12-24
Then it will be marked at solved.
I will remember :D wise words

---

