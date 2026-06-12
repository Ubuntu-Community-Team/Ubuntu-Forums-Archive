---
title: "Minecraft"
date: 2010-07-23
forum: Gaming &amp; Leisure
---

### Post by kagardner on 2010-07-23
So I attempted to play Minecraft moments ago, ans it started to load it, then it just black screened. And in the bottom corner it states applet running, but all I see is black. Anyone have any ideas?

---

### Post by Klaue on 2010-07-23
Try updating your java vm or reinstalling it
I played it by coincidence yesterday and everything worked as it should, so it isn't a general linux problem but one with your config.

If reinstalling the java vm doesn't help, try removing it and installing it from java.com. I dimly remember something being wrong with the VM in the repositories (but that could've been an issue with flash, not java, my memorie's not the best.. still, worth a try)

---

### Post by kagardner on 2010-07-23
No luck there, I tried that last night. I also tried clearing the cache since it stated that might help, but that also was no dice.

Any other ideas?
I think there might be an update for java available but I don't see that being the problem.

---

### Post by Klaue on 2010-07-23
have you tried it in another browser?
Or tried out some of the multiplayer servers? (you need an account for that, but it's free and you don't even have to give it a valid email address)

EDIT: I heard about another client which seems to be better anyway:
[http://www.worldofminecraft.com/Downloads](http://www.worldofminecraft.com/Downloads) (custom client)
maybe that one works?

EDIT: I attached the script for linux to get that client to start
if you have a problem with the menu coming up everytime you click, see here: [http://www.worldofminecraft.com/StayFocus](http://www.worldofminecraft.com/StayFocus)
```
#!/bin/bash

JAVA=`which java`

DIR=`echo $0 | sed -E 's/\/[^\/]+$/\//'`
if [ "X$0" != "X$DIR" ]; then
	cd $DIR
fi

RUN=true
while [ $RUN == "true" ]; do
	$JAVA -classpath skin:lib/jinput.jar:lib/lwjgl.jar:lib/lwjgl_util.jar:lib/wom.jar:lib/minecraft.jar -Djava.library.path=native/linux -Dsun.java2d.noddraw=true -Dsun.awt.noerasebackground=true -Dsun.java2d.d3d=false -Dsun.java2d.opengl=false -Dsun.java2d.pmoffscreen=false -Xmx800M Main
	if [ $? -ne 10 ]; then RUN=false; fi
done
```

---

### Post by kagardner on 2010-07-23
The script you gave me, I need to replace "which java" with the version I'm running correct? If so, how can I tell what to put there.

---

### Post by Klaue on 2010-07-24
the command "which java" should actually get the path of your java executable. just try it, open a terminal and type it in and see what it gets you - I get "/usr/bin/java" ;)
In other words, nah, you don't need to edit anything. Just but the code in a file in the same place where the two other scripts (for windows/osx) are, make it executable (chmod +x) and run it.

you could probably just erase the line and replace "$JAVA" below with "java", but I just edited the script for os x so that stuff is still in it

You can get the version of your java by using "java -version", but you don't need that here

---

### Post by Ballsmasher on 2010-07-26
This might not be a Java issue as I experienced something similar, before loading into a save, go into the options menu and change the graphics settings from "fancy" to "fast", may solve the problem.

---

### Post by SuperWalrus on 2010-09-02
I had the same issue as you described and the way I fixed it is by making sure I didn't have any other javas running ie Icedtea cause as soon as I uninstalled that Minecraft started to work for me.

---

### Post by The-ITu on 2010-09-03
I have tried everything to get this game to work.
The script that was posted here did not seam to work:
```
sed: invalid option -- 'E'
Usage: sed [OPTION]... {script-only-if-no-other-script} [input-file]...

  -n, --quiet, --silent
                 suppress automatic printing of pattern space
  -e script, --expression=script
                 add the script to the commands to be executed
  -f script-file, --file=script-file
                 add the contents of script-file to the commands to be executed
  -i[SUFFIX], --in-place[=SUFFIX]
                 edit files in place (makes backup if extension supplied)
  -l N, --line-length=N
                 specify the desired line-wrap length for the `l' command
  --posix
                 disable all GNU extensions.
  -r, --regexp-extended
                 use extended regular expressions in the script.
  -s, --separate
                 consider files as separate rather than as a single continuous
                 long stream.
  -u, --unbuffered
                 load minimal amounts of data from the input files and flush
                 the output buffers more often
      --help     display this help and exit
      --version  output version information and exit

If no -e, --expression, -f, or --file option is given, then the first
non-option argument is taken as the sed script to interpret.  All
remaining arguments are names of input files; if no input files are
specified, then the standard input is read.

E-mail bug reports to: bonzini@gnu.org .
Be sure to include the word ``sed'' somewhere in the ``Subject:'' field.
Exception in thread "main" java.lang.NoClassDefFoundError: Main
Caused by: java.lang.ClassNotFoundException: Main
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:319)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:264)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:332)
Could not find the main class: Main. Program will exit.
```But thanks for trying anyway.
The problem with mine is after I press "play offline" it shows the loading screen and the bar is full, but then the screen just goes black and nothing happens.

---

### Post by omgitsmit on 2010-10-04
You're actually missing some needed library files (Mainly from the Java Monkey Engine). It took me HOURS and HOURS to find out how to get Minecraft to run on Ubuntu Linux.

Posted a great article on how i did it on my blog - [http://timashley.me/node/596](http://timashley.me/node/596)

Enjoy! :)

---

### Post by Greycloak on 2010-10-12
I've been running the windows version of the game using wine. I did, however, need to install the JRE for windows first.

---

### Post by danielbruce on 2010-11-28
I've had this problem also with Ubuntu 10.10 amd64.  I fixed it by switching all "java" links on my system to sun-java.  I [blogged]("http://goo.gl/wV0nn") about how I did it.

---

### Post by Cousjava on 2010-12-01
I've tried doing that too, but one of the sun-java packages is missing I think, the pluginappletviewer which (I think) should also be in /usr/lib/jvm/java-6-sun-1.6.0.22/bin and therefore that one option it still uses openjdk, which I think needs to be sun-java. Where could I get it?

---

### Post by jiggz88 on 2011-02-22
> **Greycloak said:**
> I've been running the windows version of the game using wine. I did, however, need to install the JRE for windows first.

defeats the purpose of having a native linux client though, doesnt it?

I keep actually getting the old as hell bug of it trying to create to LWJGL instances and exceptions out. :/

---

### Post by Nutbun on 2011-02-24
I have no problem running minecraft on ubuntu.
install java runtime from your package manager
Download the Linux version of minecraft from the site. 
Right click,select properties then 'permissions' tab, tick 'allow executing file as program'.  Go to 'Open with' tab and select java.  
I think you have to have the additional graphics drivers installed as well.
And that's it, double click minecraft and your away.

---

### Post by wog on 2011-02-25
I had this problem, too.

I tried this in the command-line: ```
java -version
``` and discovered in addition to Sun Java, I was also running OpenJava. I guess in Ubuntu Open Java fights with other versions, assuming it is the only "one true" java.

I eventually got rid of OpenJava in Synaptic (don't use Ubuntu Software Center, it'll just reinstall OpenJava behind your back, or not uninstall it at all). Once OpenJava was gone, minecraft ran without a hitch.

Hope this helps!

---

### Post by cbennett a7xftw on 2011-02-25
had the same problem, make sure you have sun java not the open java and if possable figure out the catalyst control center for linux, that would also fix it.

---

### Post by NRDNick on 2011-03-01
> **omgitsmit said:**
> You're actually missing some needed library files (Mainly from the Java Monkey Engine). It took me HOURS and HOURS to find out how to get Minecraft to run on Ubuntu Linux.

Posted a great article on how i did it on my blog - [http://timashley.me/node/596](http://timashley.me/node/596)

Enjoy! :)

Thanks so much for this how-to, I'm sure you saved me and many people hours of scratching their heads!

---

### Post by Tarpoon on 2011-04-03
Hello everybody,

I'm having problems getting Minecraft to run on my (nearly fresh) Ubuntu 10.10 install.

My System config:
Athlon X3 445
Radeon 5770 (using the latest ATI drivers)
8GB RAM
Java: Sun Java 6 from the repository

When I start Minecraft the main menu opens without problems, but as soon as I start creating a world the game crashes.

This is the console output from start to crash of the game:
```
christian@prekariat-lnx:~/.minecraft$ java -jar minecraft.jar 
144 recipes
Setting user: ****, **** (Censored ;))
Loading: net.java.games.input.LinuxEnvironmentPlugin
Failed to open device (/dev/input/event4): Failed to open device /dev/input/event4 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

Linux plugin claims to have found 1 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see http://www.lwjgl.org)
OpenAL initialized.

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb78d6424, pid=2110, tid=1831967600
#
# JRE version: 6.0_24-b07
# Java VM: Java HotSpot(TM) Server VM (19.1-b02 mixed mode linux-x86 )
# Problematic frame:
# [thread 1833335664 also had an error]
C  [+0x424]  __kernel_vsyscall+0x10
#
# An error report file with more information is saved as:
# /home/christian/.minecraft/hs_err_pid2110.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Abgebrochen

```

Can someone help me fixing it?

- Tarpoon

-edit-

Maybe the Content of hs_err_pid2338.log in my Minecraft folder helps:

```
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb76f8424, pid=2338, tid=1830951792
#
# JRE version: 6.0_24-b07
# Java VM: Java HotSpot(TM) Server VM (19.1-b02 mixed mode linux-x86 )
# Problematic frame:
# C  [+0x424]  __kernel_vsyscall+0x10
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#

---------------  T H R E A D  ---------------

Current thread is native thread

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=-6 (FPE_FLTOVF), si_addr=0x00000922

Registers:
EAX=0x00000000, EBX=0x00000922, ECX=0x00000947, EDX=0x0000000b
ESP=0x6d22127c, EBP=0x6d221294, ESI=0x00000020, EDI=0xb76e3ff4
EIP=0xb76f8424, CR2=0xb68bc500, EFLAGS=0x00200206

Register to memory mapping:

EAX=0x00000000
0x00000000 is pointing to unknown location

EBX=0x00000922
0x00000922 is pointing to unknown location

ECX=0x00000947
0x00000947 is pointing to unknown location

EDX=0x0000000b
0x0000000b is pointing to unknown location

ESP=0x6d22127c
0x6d22127c is pointing to unknown location

EBP=0x6d221294
0x6d221294 is pointing to unknown location

ESI=0x00000020
0x00000020 is pointing to unknown location

EDI=0xb76e3ff4
0xb76e3ff4: <offset 0x16ff4> in /lib/libpthread.so.0 at 0xb76cd000


Top of Stack: (sp=0x6d22127c)
0x6d22127c:   6d221294 0000000b 00000947 b76db990
0x6d22128c:   b76e3ff4 6bffdf00 6d221398 6ba99943
0x6d22129c:   0000000b 00000000 00000000 00000000
0x6d2212ac:   00001000 00000000 00000000 00000000
0x6d2212bc:   00000000 00000000 7fffffff fffffffe
0x6d2212cc:   ffffffff ffffffff ffffffff ffffffff
0x6d2212dc:   ffffffff ffffffff ffffffff ffffffff
0x6d2212ec:   ffffffff ffffffff ffffffff ffffffff 

Instructions: (pc=0xb76f8424)
0xb76f8414:   51 52 55 89 e5 0f 34 90 90 90 90 90 90 90 eb f3
0xb76f8424:   5d 5a 59 c3 00 2e 73 68 73 74 72 74 61 62 00 2e 

Stack: [0x6d211000,0x6d222000],  sp=0x6d22127c,  free space=64k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [+0x424]  __kernel_vsyscall+0x10
C  [fglrx_dri.so+0x17eb943]
C  [libpthread.so.0+0x5cc9]


---------------  P R O C E S S  ---------------

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 PSYoungGen      total 42368K, used 11209K [0x9e240000, 0xa1660000, 0xb3790000)
  eden space 32896K, 22% used [0x9e240000,0x9e9697a0,0xa0260000)
  from space 9472K, 40% used [0xa0d20000,0xa10e8dd8,0xa1660000)
  to   space 10240K, 0% used [0xa0260000,0xa0260000,0xa0c60000)
 PSOldGen        total 43712K, used 13895K [0x73790000, 0x76240000, 0x9e240000)
  object space 43712K, 31% used [0x73790000,0x74521f10,0x76240000)
 PSPermGen       total 17408K, used 17399K [0x6f790000, 0x70890000, 0x73790000)
  object space 17408K, 99% used [0x6f790000,0x7088dc20,0x70890000)

Dynamic libraries:
08048000-08052000 r-xp 00000000 08:06 797385     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/bin/java
08052000-08053000 rwxp 00009000 08:06 797385     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/bin/java
080ec000-09325000 rwxp 00000000 00:00 0          [heap]
58800000-588ae000 rwxp 00000000 00:00 0 
588ae000-58900000 ---p 00000000 00:00 0 
58a00000-58ae4000 rwxp 00000000 00:00 0 
58ae4000-58b00000 ---p 00000000 00:00 0 
58bfe000-58bff000 ---p 00000000 00:00 0 
58bff000-58dff000 rwxp 00000000 00:00 0 
58dff000-58e00000 ---p 00000000 00:00 0 
58e00000-59000000 rwxp 00000000 00:00 0 
59000000-590ef000 rwxp 00000000 00:00 0 
590ef000-59100000 ---p 00000000 00:00 0 
591af000-591b2000 ---p 00000000 00:00 0 
591b2000-59200000 rwxp 00000000 00:00 0 
59200000-592fd000 rwxp 00000000 00:00 0 
592fd000-59300000 ---p 00000000 00:00 0 
59300000-593f7000 rwxp 00000000 00:00 0 
593f7000-59400000 ---p 00000000 00:00 0 
59400000-594fd000 rwxp 00000000 00:00 0 
594fd000-59500000 ---p 00000000 00:00 0 
59500000-595fd000 rwxp 00000000 00:00 0 
595fd000-59600000 ---p 00000000 00:00 0 
59600000-596fb000 rwxp 00000000 00:00 0 
596fb000-59700000 ---p 00000000 00:00 0 
59704000-63744000 rwxp 00000000 00:00 0 
63744000-63745000 ---p 00000000 00:00 0 
63745000-63f45000 rwxp 00000000 00:00 0 
63f45000-63f46000 ---p 00000000 00:00 0 
63f46000-64746000 rwxp 00000000 00:00 0 
64746000-68747000 rwxs 00000000 00:10 22979      /dev/shm/pulse-shm-2193712311
68747000-688ac000 r-xp 00000000 08:06 527003     /usr/lib/libvorbisenc.so.2.0.7
688ac000-688ad000 ---p 00165000 08:06 527003     /usr/lib/libvorbisenc.so.2.0.7
688ad000-688be000 r-xp 00165000 08:06 527003     /usr/lib/libvorbisenc.so.2.0.7
688be000-688bf000 rwxp 00176000 08:06 527003     /usr/lib/libvorbisenc.so.2.0.7
688bf000-68920000 r-xp 00000000 08:06 526909     /usr/lib/libsndfile.so.1.0.21
68920000-68921000 ---p 00061000 08:06 526909     /usr/lib/libsndfile.so.1.0.21
68921000-68922000 r-xp 00061000 08:06 526909     /usr/lib/libsndfile.so.1.0.21
68922000-68923000 rwxp 00062000 08:06 526909     /usr/lib/libsndfile.so.1.0.21
68923000-68927000 rwxp 00000000 00:00 0 
68927000-689e7000 r-xp 00000000 08:06 524490     /usr/lib/libasound.so.2.0.0
689e7000-689e8000 ---p 000c0000 08:06 524490     /usr/lib/libasound.so.2.0.0
689e8000-689ec000 r-xp 000c0000 08:06 524490     /usr/lib/libasound.so.2.0.0
689ec000-689ed000 rwxp 000c4000 08:06 524490     /usr/lib/libasound.so.2.0.0
689ed000-68a12000 r-xp 00000000 08:06 2356303    /home/christian/.minecraft/bin/natives/libopenal.so
68a12000-68a13000 rwxp 00025000 08:06 2356303    /home/christian/.minecraft/bin/natives/libopenal.so
68a13000-68b00000 rwxp 00000000 00:00 0 
68b00000-68d00000 rwxs d46c1000 00:05 7984       /dev/ati/card0
68d00000-68e00000 rwxs 03aa5000 00:05 7984       /dev/ati/card0
68e00000-68f00000 rwxs 03aa4000 00:05 7984       /dev/ati/card0
68f00000-69000000 rwxs 03aa3000 00:05 7984       /dev/ati/card0
69000000-690e3000 rwxp 00000000 00:00 0 
690e3000-69100000 ---p 00000000 00:00 0 
69114000-6915e000 r-xp 00000000 08:06 526040     /usr/lib/libFLAC.so.8.2.0
6915e000-6915f000 r-xp 00049000 08:06 526040     /usr/lib/libFLAC.so.8.2.0
6915f000-69160000 rwxp 0004a000 08:06 526040     /usr/lib/libFLAC.so.8.2.0
69160000-691a8000 r-xp 00000000 08:06 526842     /usr/lib/libpulsecommon-0.9.21.so
691a8000-691a9000 r-xp 00047000 08:06 526842     /usr/lib/libpulsecommon-0.9.21.so
691a9000-691aa000 rwxp 00048000 08:06 526842     /usr/lib/libpulsecommon-0.9.21.so
691aa000-692aa000 rwxs 03aa2000 00:05 7984       /dev/ati/card0
692aa000-69bae000 rwxp 00000000 00:00 0 
69bae000-6a2ae000 rwxs 00006000 00:05 7984       /dev/ati/card0
6a2ae000-6be73000 r-xp 00000000 08:06 532651     /usr/lib/dri/fglrx_dri.so
6be73000-6bf4d000 rwxp 01bc4000 08:06 532651     /usr/lib/dri/fglrx_dri.so
6bf4d000-6c000000 rwxp 00000000 00:00 0 
6c000000-6c076000 rwxp 00000000 00:00 0 
6c076000-6c100000 ---p 00000000 00:00 0 
6c100000-6c200000 rwxs 03aa1000 00:05 7984       /dev/ati/card0
6c200000-6c2f0000 rwxp 00000000 00:00 0 
6c2f0000-6c300000 ---p 00000000 00:00 0 
6c300000-6c3ff000 rwxp 00000000 00:00 0 
6c3ff000-6c400000 ---p 00000000 00:00 0 
6c400000-6c4f3000 rwxp 00000000 00:00 0 
6c4f3000-6c500000 ---p 00000000 00:00 0 
6c52d000-6c56c000 r-xp 00000000 08:06 524378     /usr/lib/libpulse.so.0.12.2
6c56c000-6c56d000 ---p 0003f000 08:06 524378     /usr/lib/libpulse.so.0.12.2
6c56d000-6c56e000 r-xp 0003f000 08:06 524378     /usr/lib/libpulse.so.0.12.2
6c56e000-6c56f000 rwxp 00040000 08:06 524378     /usr/lib/libpulse.so.0.12.2
6c56f000-6c700000 rwxs 00000000 00:04 9666581    /SYSV00000000 (deleted)
6c700000-6c7fc000 rwxp 00000000 00:00 0 
6c7fc000-6c800000 ---p 00000000 00:00 0 
6c815000-6c8d7000 r-xp 00000000 08:06 532626     /usr/lib/libGL.so.1.2
6c8d7000-6c8e2000 rwxp 000c2000 08:06 532626     /usr/lib/libGL.so.1.2
6c8e2000-6c8f7000 rwxp 00000000 00:00 0 
6c8f7000-6ca88000 rwxs 00000000 00:04 8290321    /SYSV00000000 (deleted)
6ca88000-6cd00000 rwxp 00000000 00:00 0 
6cd00000-6cdfb000 rwxp 00000000 00:00 0 
6cdfb000-6ce00000 ---p 00000000 00:00 0 
6ce05000-6ce08000 ---p 00000000 00:00 0 
6ce08000-6ce56000 rwxp 00000000 00:00 0 
6ce56000-6ce59000 ---p 00000000 00:00 0 
6ce59000-6cea7000 rwxp 00000000 00:00 0 
6cea7000-6cefe000 r-xp 00000000 08:06 2356295    /home/christian/.minecraft/bin/natives/liblwjgl.so
6cefe000-6ceff000 r-xp 00056000 08:06 2356295    /home/christian/.minecraft/bin/natives/liblwjgl.so
6ceff000-6cf00000 rwxp 00057000 08:06 2356295    /home/christian/.minecraft/bin/natives/liblwjgl.so
6cf00000-6d000000 rwxp 00000000 00:00 0 
6d00a000-6d04a000 rwxs 00012000 00:05 7984       /dev/ati/card0
6d04a000-6d0af000 rwxs 00000000 00:04 9633811    /SYSV00000000 (deleted)
6d0af000-6d0b2000 ---p 00000000 00:00 0 
6d0b2000-6d100000 rwxp 00000000 00:00 0 
6d100000-6d1fb000 rwxp 00000000 00:00 0 
6d1fb000-6d200000 ---p 00000000 00:00 0 
6d211000-6d212000 ---p 00000000 00:00 0 
6d212000-6d222000 rwxp 00000000 00:00 0 
6d222000-6d229000 r-xp 00000000 08:06 2093245    /lib/libwrap.so.0.7.6
6d229000-6d22a000 r-xp 00006000 08:06 2093245    /lib/libwrap.so.0.7.6
6d22a000-6d22b000 rwxp 00007000 08:06 2093245    /lib/libwrap.so.0.7.6
6d22b000-6d28b000 rwxs 00000000 00:04 8159250    /SYSV00000000 (deleted)
6d28b000-6d28e000 r-xs 00027000 08:06 797349     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/ext/sunjce_provider.jar
6d28e000-6d295000 r-xs 00094000 08:06 654604     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/jsse.jar
6d295000-6d298000 ---p 00000000 00:00 0 
6d298000-6d2e6000 rwxp 00000000 00:00 0 
6d2e6000-6d2e9000 ---p 00000000 00:00 0 
6d2e9000-6d337000 rwxp 00000000 00:00 0 
6d337000-6d33a000 ---p 00000000 00:00 0 
6d33a000-6d388000 rwxp 00000000 00:00 0 
6d388000-6d392000 r-xp 00000000 08:06 2093112    /lib/libudev.so.0.9.1
6d392000-6d393000 r-xp 00009000 08:06 2093112    /lib/libudev.so.0.9.1
6d393000-6d394000 rwxp 0000a000 08:06 2093112    /lib/libudev.so.0.9.1
6d394000-6d3a7000 r-xp 00000000 08:06 524253     /usr/lib/libgvfscommon.so.0.0.0
6d3a7000-6d3a8000 r-xp 00012000 08:06 524253     /usr/lib/libgvfscommon.so.0.0.0
6d3a8000-6d3a9000 rwxp 00013000 08:06 524253     /usr/lib/libgvfscommon.so.0.0.0
6d3a9000-6d3cc000 r-xp 00000000 08:06 525306     /usr/lib/gio/modules/libgvfsdbus.so
6d3cc000-6d3cd000 r-xp 00022000 08:06 525306     /usr/lib/gio/modules/libgvfsdbus.so
6d3cd000-6d3ce000 rwxp 00023000 08:06 525306     /usr/lib/gio/modules/libgvfsdbus.so
6d3ce000-6d408000 r-xp 00000000 08:06 526599     /usr/lib/libibus.so.2.0.0
6d408000-6d409000 r-xp 00039000 08:06 526599     /usr/lib/libibus.so.2.0.0
6d409000-6d40a000 rwxp 0003a000 08:06 526599     /usr/lib/libibus.so.2.0.0
6d40a000-6d444000 r-xp 00000000 08:06 2103741    /lib/libdbus-1.so.3.5.2
6d444000-6d445000 r-xp 00039000 08:06 2103741    /lib/libdbus-1.so.3.5.2
6d445000-6d446000 rwxp 0003a000 08:06 2103741    /lib/libdbus-1.so.3.5.2
6d448000-6d44c000 r-xp 00000000 08:06 2093301    /lib/libnss_dns-2.12.1.so
6d44c000-6d44d000 r-xp 00004000 08:06 2093301    /lib/libnss_dns-2.12.1.so
6d44d000-6d44e000 rwxp 00005000 08:06 2093301    /lib/libnss_dns-2.12.1.so
6d44e000-6d450000 r-xp 00000000 08:06 2093173    /lib/libnss_mdns4_minimal.so.2
6d450000-6d451000 r-xp 00001000 08:06 2093173    /lib/libnss_mdns4_minimal.so.2
6d451000-6d452000 rwxp 00002000 08:06 2093173    /lib/libnss_mdns4_minimal.so.2
6d452000-6d455000 r-xs 00013000 08:06 654614     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/jce.jar
6d455000-6d459000 r-xp 00000000 08:06 523820     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
6d459000-6d45a000 r-xp 00003000 08:06 523820     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
6d45a000-6d45b000 rwxp 00004000 08:06 523820     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
6d45b000-6d4aa000 r-xp 00000000 08:06 1180946    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
6d4aa000-6d500000 r-xp 00000000 08:06 1179151    /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf
6d500000-6d600000 rwxp 00000000 00:00 0 
6d601000-6d603000 r-xp 00000000 08:06 2093448    /lib/libutil-2.12.1.so
6d603000-6d604000 r-xp 00001000 08:06 2093448    /lib/libutil-2.12.1.so
6d604000-6d605000 rwxp 00002000 08:06 2093448    /lib/libutil-2.12.1.so
6d605000-6d607000 r-xp 00000000 08:06 524512     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
6d607000-6d608000 r-xp 00001000 08:06 524512     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
6d608000-6d609000 rwxp 00002000 08:06 524512     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
6d609000-6d60a000 r-xs 00000000 08:06 1575286    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
6d60a000-6d610000 r-xs 00000000 08:06 1575285    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
6d610000-6d613000 r-xs 00000000 08:06 1575284    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
6d613000-6d616000 r-xs 00000000 08:06 1575283    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
6d616000-6d619000 r-xs 00000000 08:06 1575282    /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
6d619000-6d61a000 r-xs 00000000 08:06 1575281    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
6d61a000-6d61d000 r-xs 00000000 08:06 1575280    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
6d61d000-6d61e000 r-xs 00000000 08:06 1575279    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
6d61e000-6d61f000 r-xs 00000000 08:06 1575278    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
6d61f000-6d620000 r-xs 00000000 08:06 1575277    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
6d620000-6d624000 r-xs 00000000 08:06 1575276    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
6d624000-6d62b000 r-xs 00000000 08:06 1575275    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
6d62b000-6d636000 r-xs 00000000 08:06 1575274    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
6d636000-6d639000 r-xs 00000000 08:06 1575273    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
6d639000-6d63a000 r-xs 00000000 08:06 1575272    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
6d63a000-6d642000 r-xs 00000000 08:06 1575247    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
6d642000-6d64a000 r-xs 00000000 08:06 1575364    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
6d64a000-6d65e000 r-xp 00000000 08:06 1053668    /usr/share/locale-langpack/de/LC_MESSAGES/glib20.mo
6d65e000-6d673000 r-xp 00000000 08:06 526053     /usr/lib/libICE.so.6.3.0
6d673000-6d674000 r-xp 00014000 08:06 526053     /usr/lib/libICE.so.6.3.0
6d674000-6d675000 rwxp 00015000 08:06 526053     /usr/lib/libICE.so.6.3.0
6d675000-6d677000 rwxp 00000000 00:00 0 
6d677000-6d67d000 r-xp 00000000 08:06 1052915    /usr/share/locale-langpack/de/LC_MESSAGES/gdk-pixbuf.mo
6d680000-6d687000 r-xp 00000000 08:06 526074     /usr/lib/libSM.so.6.0.1
6d687000-6d688000 r-xp 00006000 08:06 526074     /usr/lib/libSM.so.6.0.1
6d688000-6d689000 rwxp 00007000 08:06 526074     /usr/lib/libSM.so.6.0.1
6d689000-6d6bb000 r-xp 00000000 08:06 532639     /usr/lib/libatiadlxx.so
6d6bb000-6d6bc000 rwxp 00031000 08:06 532639     /usr/lib/libatiadlxx.so
6d6bc000-6d6bf000 ---p 00000000 00:00 0 
6d6bf000-6d70d000 rwxp 00000000 00:00 0 
6d70d000-6d710000 ---p 00000000 00:00 0 
6d710000-6d75e000 rwxp 00000000 00:00 0 
6d75e000-6d761000 ---p 00000000 00:00 0 
6d761000-6d7af000 rwxp 00000000 00:00 0 
6d7af000-6d7b2000 ---p 00000000 00:00 0 
6d7b2000-6d800000 rwxp 00000000 00:00 0 
6d800000-6d8ff000 rwxp 00000000 00:00 0 
6d8ff000-6d900000 ---p 00000000 00:00 0 
6d900000-6d903000 r-xp 00000000 08:06 2093493    /lib/libuuid.so.1.3.0
6d903000-6d904000 r-xp 00002000 08:06 2093493    /lib/libuuid.so.1.3.0
6d904000-6d905000 rwxp 00003000 08:06 2093493    /lib/libuuid.so.1.3.0
6d905000-6d925000 rwxs f7de0000 00:05 7984       /dev/ati/card0
6d925000-6d93f000 r-xp 00000000 08:06 2093135    /lib/libgcc_s.so.1
6d93f000-6d940000 r-xp 00019000 08:06 2093135    /lib/libgcc_s.so.1
6d940000-6d941000 rwxp 0001a000 08:06 2093135    /lib/libgcc_s.so.1
6d941000-6d949000 r-xs 00115000 08:06 656537     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/resources.jar
6d94a000-6d94d000 r-xp 00000000 08:06 527032     /usr/lib/libxcb-atom.so.1.0.0
6d94d000-6d94e000 r-xp 00002000 08:06 527032     /usr/lib/libxcb-atom.so.1.0.0
6d94e000-6d94f000 rwxp 00003000 08:06 527032     /usr/lib/libxcb-atom.so.1.0.0
6d94f000-6d950000 r-xp 00000000 08:06 526076     /usr/lib/libX11-xcb.so.1.0.0
6d950000-6d951000 r-xp 00000000 08:06 526076     /usr/lib/libX11-xcb.so.1.0.0
6d951000-6d952000 rwxp 00001000 08:06 526076     /usr/lib/libX11-xcb.so.1.0.0
6d953000-6d957000 r-xp 00000000 08:06 527371     /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
6d957000-6d958000 r-xp 00003000 08:06 527371     /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
6d958000-6d959000 rwxp 00004000 08:06 527371     /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
6d959000-6d964000 r-xp 00000000 08:06 1049911    /usr/share/locale-langpack/de/LC_MESSAGES/pulseaudio.mo
6d964000-6d966000 rwxs 00002000 00:05 7984       /dev/ati/card0
6d966000-6d971000 r-xs 00135000 08:06 2356284    /home/christian/.minecraft/bin/minecraft.jar
6d971000-6d974000 r-xs 0001f000 08:06 2356276    /home/christian/.minecraft/bin/lwjgl_util.jar
6d974000-6d979000 r-xs 00033000 08:06 2356275    /home/christian/.minecraft/bin/jinput.jar
6d979000-6d982000 r-xs 000ac000 08:06 2356270    /home/christian/.minecraft/bin/lwjgl.jar
6d982000-6d985000 r-xp 00000000 08:06 2356288    /home/christian/.minecraft/bin/natives/libjinput-linux.so
6d985000-6d986000 r-xp 00002000 08:06 2356288    /home/christian/.minecraft/bin/natives/libjinput-linux.so
6d986000-6d987000 rwxp 00003000 08:06 2356288    /home/christian/.minecraft/bin/natives/libjinput-linux.so
6d987000-6d98e000 r-xp 00000000 08:06 532646     /usr/lib/libatiuki.so.1.0
6d98e000-6d98f000 rwxp 00006000 08:06 532646     /usr/lib/libatiuki.so.1.0
6d98f000-6d992000 r-xs 000cb000 08:06 797348     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/ext/localedata.jar
6d992000-6d999000 r-xp 00000000 08:06 797437     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libnio.so
6d999000-6d99a000 rwxp 00006000 08:06 797437     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libnio.so
6d99a000-6d9ae000 r-xp 00000000 08:06 797496     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libnet.so
6d9ae000-6d9af000 rwxp 00013000 08:06 797496     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libnet.so
6d9af000-6d9dc000 r-xp 00000000 08:06 530224     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
6d9dc000-6d9dd000 r-xp 0002c000 08:06 530224     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
6d9dd000-6d9de000 rwxp 0002d000 08:06 530224     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
6d9de000-6d9e5000 r-xp 00000000 08:06 526688     /usr/lib/libltdl.so.7.2.1
6d9e5000-6d9e6000 r-xp 00006000 08:06 526688     /usr/lib/libltdl.so.7.2.1
6d9e6000-6d9e7000 rwxp 00007000 08:06 526688     /usr/lib/libltdl.so.7.2.1
6d9e7000-6d9f4000 r-xp 00000000 08:06 526950     /usr/lib/libtdb.so.1.2.1
6d9f4000-6d9f5000 r-xp 0000c000 08:06 526950     /usr/lib/libtdb.so.1.2.1
6d9f5000-6d9f6000 rwxp 0000d000 08:06 526950     /usr/lib/libtdb.so.1.2.1
6d9f6000-6d9fb000 r-xp 00000000 08:06 526765     /usr/lib/libogg.so.0.7.0
6d9fb000-6d9fc000 r-xp 00004000 08:06 526765     /usr/lib/libogg.so.0.7.0
6d9fc000-6d9fd000 rwxp 00005000 08:06 526765     /usr/lib/libogg.so.0.7.0
6d9fd000-6da23000 r-xp 00000000 08:06 527001     /usr/lib/libvorbis.so.0.4.4
6da23000-6da24000 r-xp 00025000 08:06 527001     /usr/lib/libvorbis.so.0.4.4
6da24000-6da25000 rwxp 00026000 08:06 527001     /usr/lib/libvorbis.so.0.4.4
6da25000-6da2c000 r-xp 00000000 08:06 527005     /usr/lib/libvorbisfile.so.3.3.2
6da2c000-6da2d000 r-xp 00006000 08:06 527005     /usr/lib/libvorbisfile.so.3.3.2
6da2d000-6da2e000 rwxp 00007000 08:06 527005     /usr/lib/libvorbisfile.so.3.3.2
6da2e000-6da3c000 r-xp 00000000 08:06 526213     /usr/lib/libcanberra.so.0.2.4
6da3c000-6da3d000 r-xp 0000d000 08:06 526213     /usr/lib/libcanberra.so.0.2.4
6da3d000-6da3e000 rwxp 0000e000 08:06 526213     /usr/lib/libcanberra.so.0.2.4
6da3e000-6da42000 r-xp 00000000 08:06 526211     /usr/lib/libcanberra-gtk.so.0.1.6
6da42000-6da43000 r-xp 00003000 08:06 526211     /usr/lib/libcanberra-gtk.so.0.1.6
6da43000-6da44000 rwxp 00004000 08:06 526211     /usr/lib/libcanberra-gtk.so.0.1.6
6da46000-6da49000 r-xs 00000000 08:06 1575246    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
6da49000-6da50000 r-xp 00000000 08:06 530225     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
6da50000-6da51000 ---p 00007000 08:06 530225     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
6da51000-6da52000 r-xp 00007000 08:06 530225     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
6da52000-6da53000 rwxp 00008000 08:06 530225     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
6da53000-6da58000 r-xp 00000000 08:06 530246     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
6da58000-6da59000 r-xp 00004000 08:06 530246     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
6da59000-6da5a000 rwxp 00005000 08:06 530246     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
6da5a000-6da83000 r-xp 00000000 08:06 1052971    /usr/share/locale-langpack/de/LC_MESSAGES/gtk20-properties.mo
6da83000-6daa6000 r-xp 00000000 08:06 1049934    /usr/share/locale-langpack/de/LC_MESSAGES/libc.mo
6daa6000-6daad000 r-xs 00000000 08:06 524735     /usr/lib/gconv/gconv-modules.cache
6daad000-6dad1000 r-xp 00000000 08:06 2093128    /lib/libexpat.so.1.5.2
6dad1000-6dad3000 r-xp 00024000 08:06 2093128    /lib/libexpat.so.1.5.2
6dad3000-6dad4000 rwxp 00026000 08:06 2093128    /lib/libexpat.so.1.5.2
6dad4000-6daee000 r-xp 00000000 08:06 2093217    /lib/libselinux.so.1
6daee000-6daef000 r-xp 00019000 08:06 2093217    /lib/libselinux.so.1
6daef000-6daf0000 rwxp 0001a000 08:06 2093217    /lib/libselinux.so.1
6daf0000-6db00000 r-xp 00000000 08:06 2093308    /lib/libresolv-2.12.1.so
6db00000-6db01000 r-xp 00010000 08:06 2093308    /lib/libresolv-2.12.1.so
6db01000-6db02000 rwxp 00011000 08:06 2093308    /lib/libresolv-2.12.1.so
6db02000-6db04000 rwxp 00000000 00:00 0 
6db04000-6db37000 r-xp 00000000 08:06 2093193    /lib/libpcre.so.3.12.1
6db37000-6db38000 r-xp 00032000 08:06 2093193    /lib/libpcre.so.3.12.1
6db38000-6db39000 rwxp 00033000 08:06 2093193    /lib/libpcre.so.3.12.1
6db39000-6db3f000 r-xp 00000000 08:06 527040     /usr/lib/libxcb-render.so.0.0.0
6db3f000-6db40000 r-xp 00005000 08:06 527040     /usr/lib/libxcb-render.so.0.0.0
6db40000-6db41000 rwxp 00006000 08:06 527040     /usr/lib/libxcb-render.so.0.0.0
6db41000-6db43000 r-xp 00000000 08:06 527042     /usr/lib/libxcb-shm.so.0.0.0
6db43000-6db44000 r-xp 00001000 08:06 527042     /usr/lib/libxcb-shm.so.0.0.0
6db44000-6db45000 rwxp 00002000 08:06 527042     /usr/lib/libxcb-shm.so.0.0.0
6db45000-6dba1000 r-xp 00000000 08:06 526808     /usr/lib/libpixman-1.so.0.18.4
6dba1000-6dba4000 r-xp 0005c000 08:06 526808     /usr/lib/libpixman-1.so.0.18.4
6dba4000-6dba5000 rwxp 0005f000 08:06 526808     /usr/lib/libpixman-1.so.0.18.4
6dba5000-6dc72000 r-xp 00000000 08:06 2093490    /lib/libglib-2.0.so.0.2600.1
6dc72000-6dc73000 r-xp 000cc000 08:06 2093490    /lib/libglib-2.0.so.0.2600.1
6dc73000-6dc74000 rwxp 000cd000 08:06 2093490    /lib/libglib-2.0.so.0.2600.1
6dc74000-6dc77000 r-xp 00000000 08:06 524131     /usr/lib/libgthread-2.0.so.0.2600.1
6dc77000-6dc78000 r-xp 00003000 08:06 524131     /usr/lib/libgthread-2.0.so.0.2600.1
6dc78000-6dc79000 rwxp 00004000 08:06 524131     /usr/lib/libgthread-2.0.so.0.2600.1
6dc79000-6dc7b000 r-xp 00000000 08:06 524108     /usr/lib/libgmodule-2.0.so.0.2600.1
6dc7b000-6dc7c000 r-xp 00002000 08:06 524108     /usr/lib/libgmodule-2.0.so.0.2600.1
6dc7c000-6dc7d000 rwxp 00003000 08:06 524108     /usr/lib/libgmodule-2.0.so.0.2600.1
6dc7d000-6dcbe000 r-xp 00000000 08:06 524021     /usr/lib/libgobject-2.0.so.0.2600.1
6dcbe000-6dcbf000 r-xp 00040000 08:06 524021     /usr/lib/libgobject-2.0.so.0.2600.1
6dcbf000-6dcc0000 rwxp 00041000 08:06 524021     /usr/lib/libgobject-2.0.so.0.2600.1
6dcc0000-6dcee000 r-xp 00000000 08:06 526357     /usr/lib/libfontconfig.so.1.4.4
6dcee000-6dcef000 r-xp 0002d000 08:06 526357     /usr/lib/libfontconfig.so.1.4.4
6dcef000-6dcf0000 rwxp 0002e000 08:06 526357     /usr/lib/libfontconfig.so.1.4.4
6dcf0000-6dd62000 r-xp 00000000 08:06 523500     /usr/lib/libfreetype.so.6.6.0
6dd62000-6dd66000 r-xp 00071000 08:06 523500     /usr/lib/libfreetype.so.6.6.0
6dd66000-6dd67000 rwxp 00075000 08:06 523500     /usr/lib/libfreetype.so.6.6.0
6dd67000-6dda6000 r-xp 00000000 08:06 524279     /usr/lib/libpango-1.0.so.0.2800.2
6dda6000-6dda7000 ---p 0003f000 08:06 524279     /usr/lib/libpango-1.0.so.0.2800.2
6dda7000-6dda8000 r-xp 0003f000 08:06 524279     /usr/lib/libpango-1.0.so.0.2800.2
6dda8000-6dda9000 rwxp 00040000 08:06 524279     /usr/lib/libpango-1.0.so.0.2800.2
6dda9000-6ddcd000 r-xp 00000000 08:06 524319     /usr/lib/libpangoft2-1.0.so.0.2800.2
6ddcd000-6ddce000 r-xp 00023000 08:06 524319     /usr/lib/libpangoft2-1.0.so.0.2800.2
6ddce000-6ddcf000 rwxp 00024000 08:06 524319     /usr/lib/libpangoft2-1.0.so.0.2800.2
6ddcf000-6deb7000 r-xp 00000000 08:06 524211     /usr/lib/libgio-2.0.so.0.2600.1
6deb7000-6deb9000 r-xp 000e7000 08:06 524211     /usr/lib/libgio-2.0.so.0.2600.1
6deb9000-6deba000 rwxp 000e9000 08:06 524211     /usr/lib/libgio-2.0.so.0.2600.1
6deba000-6debb000 rwxp 00000000 00:00 0 
6debb000-6dede000 r-xp 00000000 08:06 2093205    /lib/libpng12.so.0.44.0
6dede000-6dedf000 r-xp 00022000 08:06 2093205    /lib/libpng12.so.0.44.0
6dedf000-6dee0000 rwxp 00023000 08:06 2093205    /lib/libpng12.so.0.44.0
6dee0000-6df8e000 r-xp 00000000 08:06 523915     /usr/lib/libcairo.so.2.11000.0
6df8e000-6df8f000 ---p 000ae000 08:06 523915     /usr/lib/libcairo.so.2.11000.0
6df8f000-6df90000 r-xp 000ae000 08:06 523915     /usr/lib/libcairo.so.2.11000.0
6df90000-6df91000 rwxp 000af000 08:06 523915     /usr/lib/libcairo.so.2.11000.0
6df91000-6df93000 rwxp 00000000 00:00 0 
6df93000-6e027000 r-xp 00000000 08:06 526398     /usr/lib/libgdk-x11-2.0.so.0.2200.0
6e027000-6e029000 r-xp 00094000 08:06 526398     /usr/lib/libgdk-x11-2.0.so.0.2200.0
6e029000-6e02a000 rwxp 00096000 08:06 526398     /usr/lib/libgdk-x11-2.0.so.0.2200.0
6e02a000-6e3f2000 r-xp 00000000 08:06 526546     /usr/lib/libgtk-x11-2.0.so.0.2200.0
6e3f2000-6e3f6000 r-xp 003c8000 08:06 526546     /usr/lib/libgtk-x11-2.0.so.0.2200.0
6e3f6000-6e3f8000 rwxp 003cc000 08:06 526546     /usr/lib/libgtk-x11-2.0.so.0.2200.0
6e3f8000-6e3fa000 rwxp 00000000 00:00 0 
6e3fa000-6e3fb000 r-xs 00000000 08:06 1575286    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
6e3fb000-6e401000 r-xs 00000000 08:06 1575285    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
6e401000-6e404000 r-xs 00000000 08:06 1575284    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
6e404000-6e407000 r-xs 00000000 08:06 1575283    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
6e407000-6e40b000 r-xs 00000000 08:06 1575276    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
6e40b000-6e412000 r-xs 00000000 08:06 1575275    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
6e412000-6e41d000 r-xs 00000000 08:06 1575274    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
6e41d000-6e430000 r-xp 00000000 08:06 2093250    /lib/libz.so.1.2.3.4
6e430000-6e431000 r-xp 00012000 08:06 2093250    /lib/libz.so.1.2.3.4
6e431000-6e432000 rwxp 00013000 08:06 2093250    /lib/libz.so.1.2.3.4
6e432000-6e449000 r-xp 00000000 08:06 526400     /usr/lib/libgdk_pixbuf-2.0.so.0.2200.0
6e449000-6e44a000 r-xp 00017000 08:06 526400     /usr/lib/libgdk_pixbuf-2.0.so.0.2200.0
6e44a000-6e44b000 rwxp 00018000 08:06 526400     /usr/lib/libgdk_pixbuf-2.0.so.0.2200.0
6e44b000-6e463000 r-xp 00000000 08:06 526158     /usr/lib/libatk-1.0.so.0.3209.1
6e463000-6e464000 ---p 00018000 08:06 526158     /usr/lib/libatk-1.0.so.0.3209.1
6e464000-6e465000 r-xp 00018000 08:06 526158     /usr/lib/libatk-1.0.so.0.3209.1
6e465000-6e466000 rwxp 00019000 08:06 526158     /usr/lib/libatk-1.0.so.0.3209.1
6e466000-6e468000 r-xp 00000000 08:06 526091     /usr/lib/libXdamage.so.1.1.0
6e468000-6e469000 r-xp 00001000 08:06 526091     /usr/lib/libXdamage.so.1.1.0
6e469000-6e46a000 rwxp 00002000 08:06 526091     /usr/lib/libXdamage.so.1.1.0
6e46a000-6e46c000 r-xp 00000000 08:06 526087     /usr/lib/libXcomposite.so.1.0.0
6e46c000-6e46d000 r-xp 00001000 08:06 526087     /usr/lib/libXcomposite.so.1.0.0
6e46d000-6e46e000 rwxp 00002000 08:06 526087     /usr/lib/libXcomposite.so.1.0.0
6e46e000-6e478000 r-xp 00000000 08:06 524313     /usr/lib/libpangocairo-1.0.so.0.2800.2
6e478000-6e479000 r-xp 00009000 08:06 524313     /usr/lib/libpangocairo-1.0.so.0.2800.2
6e479000-6e47a000 rwxp 0000a000 08:06 524313     /usr/lib/libpangocairo-1.0.so.0.2800.2
6e47a000-6e480000 r-xp 00000000 08:06 526115     /usr/lib/libXrandr.so.2.2.0
6e480000-6e481000 r-xp 00005000 08:06 526115     /usr/lib/libXrandr.so.2.2.0
6e481000-6e482000 rwxp 00006000 08:06 526115     /usr/lib/libXrandr.so.2.2.0
6e482000-6e484000 r-xp 00000000 08:06 526105     /usr/lib/libXinerama.so.1.0.0
6e484000-6e485000 r-xp 00001000 08:06 526105     /usr/lib/libXinerama.so.1.0.0
6e485000-6e486000 rwxp 00002000 08:06 526105     /usr/lib/libXinerama.so.1.0.0
6e486000-6e489000 ---p 00000000 00:00 0 
6e489000-6e4d7000 rwxp 00000000 00:00 0 
6e4d7000-6e4db000 r-xp 00000000 08:06 526097     /usr/lib/libXfixes.so.3.1.0
6e4db000-6e4dc000 r-xp 00003000 08:06 526097     /usr/lib/libXfixes.so.3.1.0
6e4dc000-6e4dd000 rwxp 00004000 08:06 526097     /usr/lib/libXfixes.so.3.1.0
6e4dd000-6e4e5000 r-xp 00000000 08:06 526117     /usr/lib/libXrender.so.1.3.0
6e4e5000-6e4e6000 r-xp 00007000 08:06 526117     /usr/lib/libXrender.so.1.3.0
6e4e6000-6e4e7000 rwxp 00008000 08:06 526117     /usr/lib/libXrender.so.1.3.0
6e4e7000-6e4ef000 r-xp 00000000 08:06 526089     /usr/lib/libXcursor.so.1.0.2
6e4ef000-6e4f0000 r-xp 00007000 08:06 526089     /usr/lib/libXcursor.so.1.0.2
6e4f0000-6e4f1000 rwxp 00008000 08:06 526089     /usr/lib/libXcursor.so.1.0.2
6e4f1000-6e500000 r-xp 00000000 08:06 1053603    /usr/share/locale-langpack/de/LC_MESSAGES/gtk20.mo
6e500000-6e600000 rwxp 00000000 00:00 0 
6e602000-6e60a000 r-xs 00000000 08:06 1575247    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
6e60a000-6e60d000 ---p 00000000 00:00 0 
6e60d000-6e65b000 rwxp 00000000 00:00 0 
6e65b000-6e6d4000 r-xp 00000000 08:06 797498     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libfontmanager.so
6e6d4000-6e6de000 rwxp 00078000 08:06 797498     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libfontmanager.so
6e6de000-6e6e3000 rwxp 00000000 00:00 0 
6e6e3000-6e6fb000 r-xp 00000000 08:06 527044     /usr/lib/libxcb.so.1.1.0
6e6fb000-6e6fc000 r-xp 00017000 08:06 527044     /usr/lib/libxcb.so.1.1.0
6e6fc000-6e6fd000 rwxp 00018000 08:06 527044     /usr/lib/libxcb.so.1.1.0
6e6fd000-6e709000 r-xp 00000000 08:06 526103     /usr/lib/libXi.so.6.1.0
6e709000-6e70a000 r-xp 0000b000 08:06 526103     /usr/lib/libXi.so.6.1.0
6e70a000-6e70b000 rwxp 0000c000 08:06 526103     /usr/lib/libXi.so.6.1.0
6e70b000-6e824000 r-xp 00000000 08:06 526078     /usr/lib/libX11.so.6.3.0
6e824000-6e825000 r-xp 00118000 08:06 526078     /usr/lib/libX11.so.6.3.0
6e825000-6e827000 rwxp 00119000 08:06 526078     /usr/lib/libX11.so.6.3.0
6e827000-6e828000 rwxp 00000000 00:00 0 
6e828000-6e836000 r-xp 00000000 08:06 526095     /usr/lib/libXext.so.6.4.0
6e836000-6e837000 r-xp 0000d000 08:06 526095     /usr/lib/libXext.so.6.4.0
6e837000-6e838000 rwxp 0000e000 08:06 526095     /usr/lib/libXext.so.6.4.0
6e838000-6e839000 rwxs 00005000 00:05 7984       /dev/ati/card0
6e839000-6e83c000 r-xs 00000000 08:06 1575282    /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
6e83c000-6e83f000 r-xs 00000000 08:06 1575280    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
6e83f000-6e847000 r-xs 00000000 08:06 1575364    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
6e847000-6e88a000 r-xp 00000000 08:06 797474     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/xawt/libmawt.so
6e88a000-6e88c000 rwxp 00043000 08:06 797474     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/xawt/libmawt.so
6e88c000-6e88d000 rwxp 00000000 00:00 0 
6e88d000-6e911000 r-xp 00000000 08:06 797431     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libawt.so
6e911000-6e918000 rwxp 00084000 08:06 797431     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libawt.so
6e918000-6e93c000 rwxp 00000000 00:00 0 
6e93c000-6e93d000 ---p 00000000 00:00 0 
6e93d000-6e9bd000 rwxp 00000000 00:00 0 
6e9bd000-6e9c0000 ---p 00000000 00:00 0 
6e9c0000-6ea0e000 rwxp 00000000 00:00 0 
6ea0e000-6ea11000 ---p 00000000 00:00 0 
6ea11000-6ea8f000 rwxp 00000000 00:00 0 
6ea8f000-6ea92000 ---p 00000000 00:00 0 
6ea92000-6eae0000 rwxp 00000000 00:00 0 
6eae0000-6ec00000 r-xp 00178000 08:06 525663     /usr/lib/locale/locale-archive
6ec00000-6ee00000 r-xp 00000000 08:06 525663     /usr/lib/locale/locale-archive
6ee00000-6ef00000 rwxp 00000000 00:00 0 
6ef00000-6ef01000 r-xs 00000000 08:06 1575281    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
6ef01000-6ef02000 r-xs 00000000 08:06 1575279    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
6ef02000-6ef03000 r-xs 00000000 08:06 1575278    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
6ef03000-6ef06000 r-xs 00000000 08:06 1575273    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
6ef06000-6ef09000 ---p 00000000 00:00 0 
6ef09000-6ef87000 rwxp 00000000 00:00 0 
6ef87000-6ef8a000 ---p 00000000 00:00 0 
6ef8a000-6efd8000 rwxp 00000000 00:00 0 
6efd8000-6efdb000 ---p 00000000 00:00 0 
6efdb000-6f029000 rwxp 00000000 00:00 0 
6f029000-6f02a000 ---p 00000000 00:00 0 
6f02a000-6f0de000 rwxp 00000000 00:00 0 
6f0de000-6f276000 r-xs 03027000 08:06 656515     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/rt.jar
6f276000-6f277000 ---p 00000000 00:00 0 
6f277000-6f2f7000 rwxp 00000000 00:00 0 
6f2f7000-6f2f8000 ---p 00000000 00:00 0 
6f2f8000-6f378000 rwxp 00000000 00:00 0 
6f378000-6f379000 ---p 00000000 00:00 0 
6f379000-6f402000 rwxp 00000000 00:00 0 
6f402000-6f419000 rwxp 00000000 00:00 0 
6f419000-6f42f000 rwxp 00000000 00:00 0 
6f42f000-6f56f000 rwxp 00000000 00:00 0 
6f56f000-6f578000 rwxp 00000000 00:00 0 
6f578000-6f58f000 rwxp 00000000 00:00 0 
6f58f000-6f5a5000 rwxp 00000000 00:00 0 
6f5a5000-6f6e4000 rwxp 00000000 00:00 0 
6f6e4000-6f6ff000 rwxp 00000000 00:00 0 
6f6ff000-6f700000 ---p 00000000 00:00 0 
6f700000-6f78f000 rwxp 00000000 00:00 0 
6f78f000-70890000 rwxp 00000000 00:00 0 
70890000-73790000 rwxp 00000000 00:00 0 
73790000-76240000 rwxp 00000000 00:00 0 
76240000-9e240000 rwxp 00000000 00:00 0 
9e240000-a1660000 rwxp 00000000 00:00 0 
a1660000-a17e0000 ---p 00000000 00:00 0 
a17e0000-b3790000 rwxp 00000000 00:00 0 
b3790000-b3793000 r-xs 00000000 08:06 1575246    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b3793000-b3797000 r-xp 00000000 08:06 526093     /usr/lib/libXdmcp.so.6.0.0
b3797000-b3798000 r-xp 00003000 08:06 526093     /usr/lib/libXdmcp.so.6.0.0
b3798000-b3799000 rwxp 00004000 08:06 526093     /usr/lib/libXdmcp.so.6.0.0
b3799000-b37a2000 rwxp 00000000 00:00 0 
b37a2000-b3859000 rwxp 00000000 00:00 0 
b3859000-b3a99000 rwxp 00000000 00:00 0 
b3a99000-b6859000 rwxp 00000000 00:00 0 
b6859000-b6868000 r-xp 00000000 08:06 797438     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libzip.so
b6868000-b686a000 rwxp 0000e000 08:06 797438     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libzip.so
b686a000-b6874000 r-xp 00000000 08:06 2093302    /lib/libnss_files-2.12.1.so
b6874000-b6875000 r-xp 00009000 08:06 2093302    /lib/libnss_files-2.12.1.so
b6875000-b6876000 rwxp 0000a000 08:06 2093302    /lib/libnss_files-2.12.1.so
b6876000-b687f000 r-xp 00000000 08:06 2093304    /lib/libnss_nis-2.12.1.so
b687f000-b6880000 r-xp 00008000 08:06 2093304    /lib/libnss_nis-2.12.1.so
b6880000-b6881000 rwxp 00009000 08:06 2093304    /lib/libnss_nis-2.12.1.so
b6881000-b6887000 r-xp 00000000 08:06 2093300    /lib/libnss_compat-2.12.1.so
b6887000-b6888000 r-xp 00006000 08:06 2093300    /lib/libnss_compat-2.12.1.so
b6888000-b6889000 rwxp 00007000 08:06 2093300    /lib/libnss_compat-2.12.1.so
b6889000-b688a000 r-xs 00000000 08:06 1575277    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b688a000-b688e000 r-xp 00000000 08:06 526123     /usr/lib/libXtst.so.6.1.0
b688e000-b688f000 r-xp 00003000 08:06 526123     /usr/lib/libXtst.so.6.1.0
b688f000-b6890000 rwxp 00004000 08:06 526123     /usr/lib/libXtst.so.6.1.0
b6890000-b6898000 rwxs 00000000 08:06 2228609    /tmp/hsperfdata_christian/2338
b6898000-b68ab000 r-xp 00000000 08:06 2093299    /lib/libnsl-2.12.1.so
b68ab000-b68ac000 r-xp 00012000 08:06 2093299    /lib/libnsl-2.12.1.so
b68ac000-b68ad000 rwxp 00013000 08:06 2093299    /lib/libnsl-2.12.1.so
b68ad000-b68af000 rwxp 00000000 00:00 0 
b68af000-b68b1000 r-xp 00000000 08:06 526082     /usr/lib/libXau.so.6.0.0
b68b1000-b68b2000 r-xp 00001000 08:06 526082     /usr/lib/libXau.so.6.0.0
b68b2000-b68b3000 rwxp 00002000 08:06 526082     /usr/lib/libXau.so.6.0.0
b68b3000-b68b5000 r-xs 00014000 08:06 2356214    /home/christian/.minecraft/minecraft.jar
b68b5000-b68bb000 r-xp 00000000 08:06 797456     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/native_threads/libhpi.so
b68bb000-b68bc000 rwxp 00006000 08:06 797456     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/native_threads/libhpi.so
b68bc000-b68bd000 rwxp 00000000 00:00 0 
b68bd000-b68be000 r-xp 00000000 00:00 0 
b68be000-b68e1000 r-xp 00000000 08:06 797428     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libjava.so
b68e1000-b68e3000 rwxp 00023000 08:06 797428     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libjava.so
b68e3000-b68ea000 r-xp 00000000 08:06 2093309    /lib/librt-2.12.1.so
b68ea000-b68eb000 r-xp 00006000 08:06 2093309    /lib/librt-2.12.1.so
b68eb000-b68ec000 rwxp 00007000 08:06 2093309    /lib/librt-2.12.1.so
b68ec000-b68ef000 ---p 00000000 00:00 0 
b68ef000-b693d000 rwxp 00000000 00:00 0 
b693d000-b6961000 r-xp 00000000 08:06 2093297    /lib/libm-2.12.1.so
b6961000-b6962000 r-xp 00023000 08:06 2093297    /lib/libm-2.12.1.so
b6962000-b6963000 rwxp 00024000 08:06 2093297    /lib/libm-2.12.1.so
b6963000-b70f0000 r-xp 00000000 08:06 797453     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/server/libjvm.so
b70f0000-b7143000 rwxp 0078d000 08:06 797453     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/server/libjvm.so
b7143000-b7562000 rwxp 00000000 00:00 0 
b7562000-b76b9000 r-xp 00000000 08:06 2093293    /lib/libc-2.12.1.so
b76b9000-b76bb000 r-xp 00157000 08:06 2093293    /lib/libc-2.12.1.so
b76bb000-b76bc000 rwxp 00159000 08:06 2093293    /lib/libc-2.12.1.so
b76bc000-b76bf000 rwxp 00000000 00:00 0 
b76bf000-b76c1000 r-xp 00000000 08:06 2093296    /lib/libdl-2.12.1.so
b76c1000-b76c2000 r-xp 00001000 08:06 2093296    /lib/libdl-2.12.1.so
b76c2000-b76c3000 rwxp 00002000 08:06 2093296    /lib/libdl-2.12.1.so
b76c3000-b76ca000 r-xp 00000000 08:06 797442     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/jli/libjli.so
b76ca000-b76cc000 rwxp 00006000 08:06 797442     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/jli/libjli.so
b76cc000-b76cd000 rwxp 00000000 00:00 0 
b76cd000-b76e2000 r-xp 00000000 08:06 2093307    /lib/libpthread-2.12.1.so
b76e2000-b76e3000 ---p 00015000 08:06 2093307    /lib/libpthread-2.12.1.so
b76e3000-b76e4000 r-xp 00015000 08:06 2093307    /lib/libpthread-2.12.1.so
b76e4000-b76e5000 rwxp 00016000 08:06 2093307    /lib/libpthread-2.12.1.so
b76e5000-b76e7000 rwxp 00000000 00:00 0 
b76e7000-b76e8000 r-xs 00000000 08:06 1575272    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b76e8000-b76e9000 r-xp 00000000 08:06 797440     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libjawt.so
b76e9000-b76ea000 rwxp 00000000 08:06 797440     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libjawt.so
b76ea000-b76f5000 r-xp 00000000 08:06 797469     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libverify.so
b76f5000-b76f6000 rwxp 0000b000 08:06 797469     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/libverify.so
b76f6000-b76f8000 rwxp 00000000 00:00 0 
b76f8000-b76f9000 r-xp 00000000 00:00 0          [vdso]
b76f9000-b7715000 r-xp 00000000 08:06 2093059    /lib/ld-2.12.1.so
b7715000-b7716000 r-xp 0001b000 08:06 2093059    /lib/ld-2.12.1.so
b7716000-b7717000 rwxp 0001c000 08:06 2093059    /lib/ld-2.12.1.so
bfe81000-bfea2000 rwxp 00000000 00:00 0          [stack]

VM Arguments:
java_command: minecraft.jar
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=christian
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386/server:/usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.24/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x708f80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x708f80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x5c4100], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00001000, sa_flags=0x10000000
SIGXFSZ: [libjvm.so+0x5c4100], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x5c4100], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x5c70e0], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x5c6cc0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x5c6cc0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x5c6cc0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x5c6cc0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:squeeze/sid

uname:Linux 2.6.35-27-generic-pae #48-Ubuntu SMP Tue Feb 22 21:46:58 UTC 2011 i686
libc:glibc 2.12.1 NPTL 2.12.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:0,21 0,08 0,13

/proc/meminfo:
MemTotal:        8259920 kB
MemFree:         6840736 kB
Buffers:           57964 kB
Cached:           430092 kB
SwapCached:            0 kB
Active:           935912 kB
Inactive:         278696 kB
Active(anon):     726988 kB
Inactive(anon):     9272 kB
Active(file):     208924 kB
Inactive(file):   269424 kB
Unevictable:          16 kB
Mlocked:              16 kB
HighTotal:       7474888 kB
HighFree:        6192728 kB
LowTotal:         785032 kB
LowFree:          648008 kB
SwapTotal:       1952764 kB
SwapFree:        1952764 kB
Dirty:               268 kB
Writeback:             0 kB
AnonPages:        726660 kB
Mapped:           148712 kB
Shmem:              9700 kB
Slab:              39640 kB
SReclaimable:      27516 kB
SUnreclaim:        12124 kB
KernelStack:        2768 kB
PageTables:         6736 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     6082724 kB
Committed_AS:    1656548 kB
VmallocTotal:     122880 kB
VmallocUsed:       30152 kB
VmallocChunk:      90004 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:        8184 kB
DirectMap2M:      905216 kB


CPU:total 3 (3 cores per cpu, 1 threads per core) family 16 model 5 stepping 3, cmov, cx8, fxsr, mmx, sse, sse2, sse3, popcnt, mmxext, 3dnow, 3dnowext, lzcnt, sse4a

Memory: 4k page, physical 8259920k(6840736k free), swap 1952764k(1952764k free)

vm_info: Java HotSpot(TM) Server VM (19.1-b02) for linux-x86 JRE (1.6.0_24-b07), built on Feb  2 2011 16:51:52 by "java_re" with gcc 3.2.1-7a (J2SE release)

time: Sun Apr  3 12:21:23 2011
elapsed time: 6 seconds

```

---

### Post by christopher.mountford on 2011-04-15
I'm having the exact same problem as this I've been told its something to do with the graphics card I have an ATI Radeon HD 5570. I cant believe this still hasn&#8217;t been fixed tbh it seems to happen in a number of Java Apps/Games if im running a Java app locally it'll disappear randomly and if if using a web Java app the programme will just go a blank white.

[edit] Also seems to be a problem in the new 11.04 beta:( although I am loving the new beta apart from that [/edit]

---

### Post by youknowwhat4q on 2011-04-18
> **omgitsmit said:**
> You're actually missing some needed library files (Mainly from the Java Monkey Engine). It took me HOURS and HOURS to find out how to get Minecraft to run on Ubuntu Linux.

Posted a great article on how i did it on my blog - [http://timashley.me/node/596](http://timashley.me/node/596)

Enjoy! :)

```
x@x laptop:~/.minecraft$ java -jar minecraft.jar
Unable to access jarfile minecraft.jar

```

Anyone?

---

### Post by ALEXNIM on 2011-05-17
Pls, I got BIG problems with minecraft! I love to play minecraft but when i start it it stands 


No JVM could be found on your system. Please define EXE4J_JAVA_HOME to point to an installed 32-bit JDK or JRE or download a JRE from [www.java.com]("http://www.java.com").


What am i supposed to do?! I tried to download and install JRE... Download=great :)  Installation=What the H**L!?:mad::(

can anyone pls help me, all help is welcome! :) :P

---

### Post by Perfect Storm on 2011-05-18
enable 'Partner' repositories in Ubuntu Software Center - then you have sun java available to download install the easy way.

---

### Post by theophysics1102 on 2011-06-12
i dont know if this will help but here's what i did:
1) downloaded the minecraft.exe from minecraft.net ( the windows one obviously ) 
2) right clicked the minecraft.exe and selected open with and hit other application.
3) selected open JDK 6 Runtime
4) played minecraft

i have wine 1.2.2 installed as well 
hope that helps

---

