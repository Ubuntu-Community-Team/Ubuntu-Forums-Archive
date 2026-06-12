---
title: "Trouble installing and running Wakfu"
date: 2012-03-12
forum: Gaming &amp; Leisure
---

### Post by sffvba[e0rt on 2012-03-12
Hi,

Currently running Ubuntu 12.04 Beta (64-bit) and I am having trouble installing / Running Wakfu.

I downloaded the linux client from the website, a file called "Wakfu_unix.sh" which is around 24.3MB in size. 

If I try and run the file from Nautilus nothing happens.  Running it from Terminal I get a message that the following:
```
nlsthzn@circle:~/Downloads$ ./Wakfu_unix.sh 
Unpacking JRE ...
Preparing JRE ...
Starting Installer ...
Could not display the GUI. This application needs access to an X Server.
*******************************************************************
You can also run this application in console mode without
access to an X server by passing the argument -c
*******************************************************************
nlsthzn@circle:~/Downloads$ 
nlsthzn@circle:~/Downloads$
``` 

If I run it with the -c option it runs through the installation and I end up with a directory with three files (uninstall, UpLauncher and Wakfu) plus one hidden folder with several files in it.

Trying to run Wakfu gives me this:
```
The archive /home/nlsthzn/ankama/Wakfu/core.jar does not exist.
nlsthzn@circle:~/ankama/Wakfu$
nlsthzn@circle:~/ankama/Wakfu$ 

```

Trying to run UpLauncer gives me:
```
./UpLauncher 
./UpLauncher: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
nlsthzn@circle:~/ankama/Wakfu$ 

```

Googling *libgtk-x11-2.0.so.0* got me a hit to make sure *libgtk2.0-0* is installed and it is.

I have found nothing on the net thus far to assist with this installation even though I have read on this forum there is issues using a 64-bit distro but that they can be overcome.

Any assistance greatly appreciated.


404

---

### Post by madjr on 2012-03-12
ok, i will try it on my precise computer when i get home.

for now it works well on my oneiric 32bit.

[http://ubuntuforums.org/showpost.php?p=11759248&postcount=8](http://ubuntuforums.org/showpost.php?p=11759248&postcount=8)

---

### Post by madjr on 2012-03-12
ok i tried it on 12.04 64bit. i get this:

```
Unpacking JRE ...
Preparing JRE ...
./Wakfu_unix.sh: 197: ./Wakfu_unix.sh: bin/unpack200: not found
Error unpacking jar files. The architecture or bitness (32/64)
of the bundled JVM might not match your machine.
```

guess i will be installing 32bit precise or staying with 32bit oneiric for a while till they add 64bit support.

oh and might be better to merge the threads and specify in the title is 64bit.

---

### Post by Perfect Storm on 2012-03-12
Works fine here on Ubuntu 11.10 64-bit. Which Java are you using? Are 32-libs installed?

```
orion@universe:~$ sh '/home/orion/Downloads/Wakfu_unix.sh' 
Unpacking JRE ...
Preparing JRE ...
Starting Installer ...

```

---

### Post by madjr on 2012-03-12
> **Artificial Intelligence said:**
> Works fine here on Ubuntu 11.10 64-bit. Which Java are you using? Are 32-libs installed?

```
orion@universe:~$ sh '/home/orion/Downloads/Wakfu_unix.sh' 
Unpacking JRE ...
Preparing JRE ...
Starting Installer ...

```

how i install 32libs on precise 64bit?

---

### Post by sffvba[e0rt on 2012-03-12
> **madjr said:**
> how i install 32libs on precise 64bit?

+1 - How would we go about doing this?


404

---

### Post by Perfect Storm on 2012-03-13
in Ubuntu 11.10 (and 12.04) if you check Synaptic Package Manager (if installed), you'll notice that every libs have a 32-bit counterpart which usually named **:i386**. 

Those libs are separated from the 64-bit libs when installed. The 32-bit version libs are installed under /lib32.

To get the most common 32-bit to run most 32-bit applications in a 64-bit environment just install the two meta-package:

ia32-libs
ia32-libs-multiarch:i386 



Note, that I used Oracle Java instead of OpenJava to run Wakfu.

---

### Post by sffvba[e0rt on 2012-03-13
> **Artificial Intelligence said:**
> in Ubuntu 11.10 (and 12.04) if you check Synaptic Package Manager (if installed), you'll notice that every libs have a 32-bit counterpart which usually named **:i386**. 

Those libs are separated from the 64-bit libs when installed. The 32-bit version libs are installed under /lib32.

To get the most common 32-bit to run most 32-bit applications in a 64-bit environment just install the two meta-package:

ia32-libs
ia32-libs-multiarch:i386 



Note, that I used Oracle Java instead of OpenJava to run Wakfu.

Was able to install ia32-libs (no ia32-libs-multiarch:i386 available).

No change.

Installed the game via the terminal again...

Now I get the following:
```
nlsthzn@circle:~/ankama/Wakfu$ sudo ./UpLauncher 
./UpLauncher: error while loading shared libraries: libjpeg.so.62: cannot open shared object file: No such file or directory
nlsthzn@circle:~/ankama/Wakfu$ 

```

I installed any package I could get in Synaptic that had the word libjpeg and a 6 and a 2 in it :p  ... Obviously didn't work :(

I can't find out much about libjpeg.so.62 except it definitly isn't on my machine at the moment:
```
nlsthzn@circle:/$ sudo locate -i libjpeg.so
/home/nlsthzn/.i4j_jres/1.6.0/lib/i386/libjpeg.so
/usr/lib/x86_64-linux-gnu/libjpeg.so.8
/usr/lib/x86_64-linux-gnu/libjpeg.so.8.0.2
/usr/local/i4j_jres/1.6.0/lib/i386/libjpeg.so
nlsthzn@circle:/$
```

??


404

---

### Post by Perfect Storm on 2012-03-13
Install; 

libjpeg62:i386

---

### Post by sffvba[e0rt on 2012-03-13
> **Artificial Intelligence said:**
> Install; 

libjpeg62:i386

Thanks for the file... at this time I have already installed Ubuntu 12.04 32-bit... and even though the initial installation worked this time without any additional faffing around by me the game still didn't want to run.

UNTIL I installed libjpeg62 (seeing as I am already in the 32-bit version) and the game is now running and downloading the patched etc... So far so good, seems we got this one to work.

Thanks all for your assistance.



404

---

### Post by sffvba[e0rt on 2012-03-13
Final post to confirm that the game works (the performance isn't on par with windows though) (might be because I am using openjdk-7).


Cheers
404

---

### Post by Perfect Storm on 2012-03-13
> **not found said:**
> Final post to confirm that the game works (the performance isn't on par with windows though) (might be because I am using openjdk-7).


Cheers
404

Aye, I'm using Oracle Java and there's no lag etc.

---

### Post by madjr on 2012-03-13
hm, am not sure what it means, but OpenJDK was suppose to be Java SE 7's Reference Implementation.

[https://blogs.oracle.com/henrik/entry/moving_to_openjdk_as_the](https://blogs.oracle.com/henrik/entry/moving_to_openjdk_as_the)
[http://www.infoq.com/news/2011/06/openjdk-bylaws](http://www.infoq.com/news/2011/06/openjdk-bylaws)


does it mean that oracle's java and openjdk are suppose to work the same, merge or drop the one from oracle at some point?

hope so, dont like this fragmentation.

---

### Post by sffvba[e0rt on 2012-03-13
AFIAK there will only be one java from now on... not sure when this will start.


404

---

### Post by eB0Y on 2012-04-11
Ok, so here is the ALL-IN-ALL Tutorial to install and run Wakfu under Ubuntu [64 bit] [intelHD 3000]

For 64 bit install these packages via apt-get from terminal:

  sudo apt-get install ia32-libs libjpeg62:i386 openjdk-7-jre

For 32 bit install install these packages:

  sudo apt-get install libjpeg62 openjdk-7-jre

Than, if you are using intel (HD) graphics:

  sudo apt-get install libgl1-mesa-dri-experimental


For all graphics, install driconf to setup openGL:

  sudo apt-get install driconf

Now open "3D Acceleration" from Unity, or where ever, and select tab 2 ("Image quality"), there you activate the first Option "Activate S3TC ..." so that you later can read there the word "yes" - force that option, if you have to.

   Forcing this option solves the square problem (look at the publishers name: square enix, lol)


Now install Wakfu with its installer (!you have to give the installer the execution (x) right to run it!), update and than run it :-)


Wakfu runs now fine here on intelHD 3000 graphics, with dualcore and openjdk-7.

---

### Post by iseijin on 2012-04-27
Thank you very much! This worked for me too.

---

### Post by naknak987 on 2012-05-12
Wakfu is now running on my 12.04 machine with no glitches. But theres just one little problem, running in windowed mode it cuts off part of the bottom of the game. so i cant see some of the buttons that are on the bottom. If I switch it to fullscreen mode it cuts off more of the game and does not cover the laucher bar or the top tool/notification bar. I'v tried searching for a way to resize the windowed game but since I cant get my mouse down to the bottom right corner of the game window I can't resize the window, and searching brings nothing up. Anyone know of a fix?

---

### Post by Tandem War Elephant on 2012-09-20
I completed these steps AFTER installing Wakfu and then updated the client. When I click play the window opens, the contents are just a blank black screen, then the window and wine closes. then nothing.

---

### Post by evilishan on 2012-09-20
Run the Wafku installer again. Should work ;)
I had the same problem.

---

### Post by thatguruguy on 2012-09-20
> **Tandem War Elephant said:**
> I completed these steps AFTER installing Wakfu and then updated the client. When I click play the window opens, the contents are just a blank black screen, then the window and wine closes. then nothing.

This is about installing and running the Linux client for Wakfu, not the Windows client under Wine.

---

### Post by davidwdurney on 2012-09-22
I got Wakfu installed and running fine, but only the first time. I tried to boot it under Terminal using the UpLauncher and it just sits spinning at the Wakfu loader window. Neither of the UpLauncher files nor the Wakfu executable seem to work and there isn't a link in the Games menu.

Anyone have this issue?

---

### Post by gstephen on 2012-09-23
> **eB0Y said:**
> Ok, so here is the ALL-IN-ALL Tutorial to install and run Wakfu under Ubuntu [64 bit] [intelHD 3000]

For 64 bit install these packages via apt-get from terminal:

  sudo apt-get install ia32-libs libjpeg62:i386 openjdk-7-jre

For 32 bit install install these packages:

  sudo apt-get install libjpeg62 openjdk-7-jre

Than, if you are using intel (HD) graphics:

  sudo apt-get install libgl1-mesa-dri-experimental


For all graphics, install driconf to setup openGL:

  sudo apt-get install driconf

Now open "3D Acceleration" from Unity, or where ever, and select tab 2 ("Image quality"), there you activate the first Option "Activate S3TC ..." so that you later can read there the word "yes" - force that option, if you have to.

   Forcing this option solves the square problem (look at the publishers name: square enix, lol)


Now install Wakfu with its installer (!you have to give the installer the execution (x) right to run it!), update and than run it 


Wakfu runs now fine here on intelHD 3000 graphics, with dualcore and openjdk-7.

You're such a wizard. All hail eBoy. All hail eBoy.
:popcorn::popcorn::popcorn::popcorn::popcorn::popcorn::popcorn::popcorn:

---

### Post by alfsagen on 2012-10-08
I had exact same problem installing soapUI on my 64 bit Ubuntu 12.04 (precise) system.
First, I uninstalled OpenJDK and installed Oracle/Sun Java 1.7_07 iaw. recommendations on other sites, but to no avail. Still getting exact same error message as reported by 'not found' in start of this thread.

What solved the problem was installing 'ia32-libs' (which has a dependency to several packages, among them 'ia32-libs-multiarch:i386', which is also installed). After running the installer shell script again, I still got some error messages (ELF versions etc.), but installer GUI actually started anyway. Running the installed (with sudo bash install_script.sh) again, the error messages from previous install were all gone...

Thanks for tips!

/alfs

---

