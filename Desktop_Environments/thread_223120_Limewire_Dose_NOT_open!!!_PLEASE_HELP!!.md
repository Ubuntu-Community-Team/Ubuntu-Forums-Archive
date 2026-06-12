---
title: "Limewire Dose NOT open!!! PLEASE HELP!!"
date: 2006-07-25
forum: Desktop Environments
---

### Post by morbid_bean on 2006-07-25
Why dosnt my limewire open, the icon is there on the applications menu and when I click on it, it dose nothing. And when i say nothing it dose NOTHING, it acts as if i click on an open space on my desktop.

Any help!?!?!

P.S. Yes it is installed. And i have Reinstalled, still dose it.

---

### Post by slipk487 on 2006-07-25
do u have java installed

---

### Post by JerMe on 2006-07-25
> **morbid_bean said:**
> Why dosnt my limewire open, the icon is there on the applications menu and when I click on it, it dose nothing. And when i say nothing it dose NOTHING, it acts as if i click on an open space on my desktop.

Any help!?!?!

P.S. Yes it is installed. And i have Reinstalled, still dose it.

Run it from the terminal and post back what the output is.  My guess is that you're having a java issue, and you need to set the default JRE to Sun.

---

### Post by morbid_bean on 2006-07-25
You know what i think it is java, but how do i install it?


By the way i did try to open it from terminal, and it is java.

---

### Post by JerMe on 2006-07-26
You didn't post the output!  It's ok - pay a visit to the Ubuntu java wiki.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Install Sun Java, then set it as default JRE 

```
sudo update-alternatives --config java
```

Then run [FONT="Courier New"]limewire[/FONT] from the terminal again.  If it doesn't work, **post the output so we can help**. ;)

---

### Post by morbid_bean on 2006-07-26
oh yea forgot, this is wut it says...

myname@ubuntu:~$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
myname@ubuntu:~$



I also forgot to mention that i still use ubuntu 5.10 because 6.06 dosnt work on my computer....not enough ram.

---

### Post by JerMe on 2006-07-26
So following the Java link I gave you earlier...

> Direct installation of Sun packages

**Note: This is only for Ubuntu 5.10 and earlier.** See above for 6.06

   1. Download (with your browser is OK) the sun-java5-bin_1.5.0-06-1_i386.deb (or sun-java5-bin_1.5.0-06-1_amd64.deb for Amd64) and  sun-java5-jre_1.5.0-06-1_all.deb from [WWW] [http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java5/](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java5/) They will probably wind up on your desktop, which is OK. You can remove them from there when Java is up and running.

   2. Install the unixodbc package. Preferably using Synaptic (System > administration > Synaptic package manager)

   3. Open a terminal (program > tillbehör > terminal) and type sudo dpkg -i sun-java5-jre_1.5.0-06-1_all.deb (or copy, Ctrl+C, and paste, with Shift+Ins or middle-click)

   4. Accept the license. It will fail, due to needing -bin, but you need to accept the license. You cannot install -bin first

   5. Install the -bin with sudo dpkg -i sun-java5-bin_1.5.0-06-1_i386.deb (or sun-java5-bin_1.5.0-06-1_amd64.deb for Amd64) (Even this step will have some messages that seem to mean it hasn't worked, but after the next step it should be OK)

   6. Run sudo dpkg --configure -a to configure the two java packages

---

### Post by morbid_bean on 2006-07-26
K thank you this should work, im downloading the 2 files right now (lol slow internet) and i hope this works......THANKS AGAIN!

---

### Post by disciple on 2006-07-26
..

---

### Post by morbid_bean on 2006-07-26
Ok, I did exactly what was said right there, and i did it and still wont open, i tried it again and this is my code for the second time i try it:

myname@ubuntu:~$ cd Desktop
myname@ubuntu:~/Desktop$ sudo dpkg -i sun-java5-jre_1.5.0-06-1_all.deb
(Reading database ... 78824 files and directories currently installed.)
Unpacking sun-java5-jre (from sun-java5-jre_1.5.0-06-1_all.deb) ...
sun-dlj-v1-1 license has already been accepted
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing sun-java5-jre_1.5.0-06-1_all.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/cmm/PYCC.pf')
Errors were encountered while processing:
 sun-java5-jre_1.5.0-06-1_all.deb
myname@ubuntu:~/Desktop$ sudo dpkg -i sun-java5-bin_1.5.0-06-1_i386.deb
(Reading database ... 78824 files and directories currently installed.)
Preparing to replace sun-java5-bin 1.5.0-06-1 (using sun-java5-bin_1.5.0-06-1_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java5-bin ...
dpkg: dependency problems prevent configuration of sun-java5-bin:
 sun-java5-bin depends on sun-java5-jre (= 1.5.0-06-1); however:
  Package sun-java5-jre is not installed.
dpkg: error processing sun-java5-bin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java5-bin
myname@ubuntu:~/Desktop$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of sun-java5-bin:
 sun-java5-bin depends on sun-java5-jre (= 1.5.0-06-1); however:
  Package sun-java5-jre is not installed.
dpkg: error processing sun-java5-bin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java5-bin
myname@ubuntu:~/Desktop$

---

### Post by JerMe on 2006-07-26
You installed unixodbc right?

try **sudo dpkg -i sun-java5-jre_1.5.0-06-1_all.deb** again and then **sudo dpkg --configure -a**

---

### Post by morbid_bean on 2006-07-26
Yep, doubled checked and unixodbc is installed, tried what you said  this is what i get:

myname@ubuntu:~$ cd Desktop
myname@ubuntu:~/Desktop$ sudo dpkg -i sun-java5-jre_1.5.0-06-1_all.deb
Password:
(Reading database ... 78824 files and directories currently installed.)
Unpacking sun-java5-jre (from sun-java5-jre_1.5.0-06-1_all.deb) ...
sun-dlj-v1-1 license has already been accepted
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing sun-java5-jre_1.5.0-06-1_all.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/cmm/PYCC.pf')
Errors were encountered while processing:
 sun-java5-jre_1.5.0-06-1_all.deb
myname@ubuntu:~/Desktop$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of sun-java5-bin:
 sun-java5-bin depends on sun-java5-jre (= 1.5.0-06-1); however:
  Package sun-java5-jre is not installed.
dpkg: error processing sun-java5-bin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java5-bin
myname@ubuntu:~/Desktop$

---

### Post by morbid_bean on 2006-07-26
I also have tried to restart my computer.:confused: :confused: :confused:

---

### Post by disciple on 2006-07-26
hey.. sounds like a problem i had with the frostwire ( limewire's open source twin) package  under breezy..  after clickin on the icon, it would jsut bounce a couple times, then disappear....

had something to do with one of the config files being stored in an ms-dos text file, instead of a linux friendly one, or so it seemed to me
..

anyhow, here's the thread that helped me 
[http://ubuntuforums.org/showthread.php?t=165371](http://ubuntuforums.org/showthread.php?t=165371)
 
hope it works for you

---

### Post by slipk487 on 2006-07-27
if anything just get automatix and then have it install java and frostwire frostwire is better then limewire unless u have limewire pro

[site]("http://getautomatix.com/")
[forum]("http://ubuntuforums.org/showthread.php?t=177646")

---

### Post by cjm5229 on 2006-07-28
Frostwire maxes out memory and cpu on every computer I have installed it on. Limewire doesn't use hardly any. If he has low memory he better stick with Limewire. However if you use Automatix to install Java it should work quite well.

---

### Post by disciple on 2006-08-01
> **cjm5229 said:**
> Frostwire maxes out memory and cpu on every computer I have installed it on. Limewire doesn't use hardly any. If he has low memory he better stick with Limewire. However if you use Automatix to install Java it should work quite well.


hmm.. never had that happen ..i used frostwire up until limewire came out, and i observed no great difference, if any

frostwire is a fork of the limewire project, so for the most part, it's the same code ( for now)

if anything, they both draw a lot of cpu time and memory through java ( they both use java)

---

### Post by AppleNick on 2006-08-01
Did you install Java in /usr/lib? That's where LimeWire checks for Java installations.

---

