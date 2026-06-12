---
title: "Minecraft won't load; Gives a black screen."
date: 2010-09-08
forum: Gaming &amp; Leisure
---

### Post by anthony62490 on 2010-09-08
I'm trying to play [Minecraft]("http://en.wikipedia.org/wiki/Minecraft"), but every time I try to load up the game ([at this page]("http://minecraft.net/play.jsp")), it shows the loading bars followed by a blank black screen. My Java Packages are:
```
ca-certificates-java
gcj-4.4-jre
gcj-4.4-jre-headless
gcj-jre
gcj-jre-headless
icedtea6-plugin
java-common
libaccess-bridge-java
libaccess-bridge-java-ini
libclucene0ldbl
libgcj10
libswt-gtk-3.5-java
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib
sun-java6-bin
sun-java6-jdk
sun-java6-jre
tzdata-java
```

Any ideas?

---

### Post by donkyhotay on 2010-09-09
Which one is your default that your browser uses? I play minecraft (bought the alpha even) and don't have any issues. The only version of java I have installed is the "sun java" version. If you need all those different java's installed and don't know which one your browser is using then download the client and try running each one through the CLI.

---

### Post by chewit on 2010-09-09
Remove IceTea plugin. Install sun-java6-plugin. 

Works fine for me on Ubuntu using Firefox

---

### Post by anthony62490 on 2010-09-11
> **donkyhotay said:**
> [...D]ownload the client and try running each one through the CLI.

I'm sorry. You want me to download a Java client? Not entirely sure which package that's in. Details please?

**NOTE1:** After removing the IcedTea packages and the OpedJDK packages, Minecraft doesn't even give a black screen. The stone background shows right through.

**NOTE2:** Tried running dpkg-reconfigure sun-java6-jre and I got some strange messages.

```
anthony@anthony-desktop:~$ sudo dpkg-reconfigure sun-java6-jre
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'fonts/package'
Unknown media type in type 'interface/x-winamp-skin'
```

---

### Post by alexandrius on 2010-09-11
search in synaptic and install from there

---

### Post by anthony62490 on 2010-09-11
> **alexandrius said:**
> search in synaptic and install from there

I have tried to do this. Would you mind telling me which package is needed?

EDIT: Interesting. Typing ```
about:plugins
``` into the URL gives no mention of a Java plugin. It just lists my Flash, VLC and QuickTime plugins.

---

### Post by anthony62490 on 2010-09-11
bump

---

### Post by anthony62490 on 2010-09-11
Okay, I went ahead and bought the Alpha, so I downloaded the JAR file and it runs beautifully. So, I guess this thread is solved then. But I still can't run Java apps in Firefox.

---

### Post by alexandrius on 2010-09-12
sun-java6-plugin

---

### Post by medeshago on 2010-09-13
I'm playng in the alpha version but I don't get any sound. Is anybody else having the same issue?

---

### Post by kofrad on 2010-09-13
> **medeshago said:**
> I'm playng in the alpha version but I don't get any sound. Is anybody else having the same issue?

I have an issue where occasionally the sound drops out and stops working until I restart the game. I've yet to track down any probable source though.

---

### Post by anthony62490 on 2010-09-14
> **medeshago said:**
> I'm playng in the alpha version but I don't get any sound. Is anybody else having the same issue?

Yeah, I get the same issue. After about 15 minutes or so, the sound cuts out. Keep in mind though that it is just an Alpha version. Besides, Notch is aware of this issue. He has it posted on his To Do list. [Item #2]("http://www.toodledo.com/views/public.php?id=td4b49fbf9c05a0")

---

### Post by Killyjoe on 2010-09-22
Well, Igot two things :)

First about the Soiund Problem.
With my Windows Pc I get the Sound back when I dissable the Internet connection before I start the game..

The other thing, could anyone explain me how to run the downloadeble .jar file with ubuntu? :D
I don't get it working..

---

### Post by medeshago on 2010-09-22
> **Killyjoe said:**
> Well, Igot two things :)

First about the Soiund Problem.
With my Windows Pc I get the Sound back when I dissable the Internet connection before I start the game..

The other thing, could anyone explain me how to run the downloadeble .jar file with ubuntu? :D
I don't get it working..

Yyou can run it from the command line like this:
java -jar example.jar
And if you want to run it from nautilus, you can go to the properties of the file and in "open with" select Sun Java 6

---

### Post by kristian_gjengedal on 2010-09-23
also remember to to make the file executable.

for the sound problems you can try pressing F3 + S that fixes sound for me.

---

### Post by omgitsmit on 2010-10-04
You're actually missing some needed library files (Mainly from the Java Monkey Engine). It took me HOURS and HOURS to find out how to get Minecraft to run on Ubuntu Linux.

Posted a great article on how i did it on my blog - [http://timashley.me/node/596](http://timashley.me/node/596)

Enjoy! :)

---

### Post by 9squirrels on 2010-10-26
I'm getting a similar problem.  I bought Alpha, downloaded it, ran it, all happy.
Then I tried again a few days later and it wouldn't get beyond the loading screen (it gets almost to the end of the loading bar, then stops and hangs there showing a "Loading complete" message).
I tried removing Java and re-installing it again to make sure I had the right version of Java, and only that version (there was some other non-sun Java installed as well), but I still get the same problem.  I get the exact same result going through Firefox as well.
  I tried right clicking and launching with Java, tried using the basic launch from the command line, and also tried using the more complex launch string that Notch posted on the page.

Any ideas?

---

### Post by Andq1 on 2010-11-09
it is so easy (when you guys talk about alpha) go to your computer up in the top is there a arrow computer arrow okay delete computer and type in %appdata% in there is a folder called .minecraft delete it (your worlds will also be deleted so copy the file called world)
then load the game again Wub




Credits Marc2540 for telling me this (he's not on this forum)


enjoy

---

### Post by dopple on 2010-11-09
For anyone getting the black screen issue I removed all java installations apart from the official installation and plugin and it works fine.

---

### Post by omgitsmit on 2010-11-10
> **dopple said:**
> For anyone getting the black screen issue I removed all java installations apart from the official installation and plugin and it works fine.

Are you playing in a browser or from the .jar JRE file?

---

### Post by robsonic on 2010-11-17
I have the exact same problem but can't download the Sun Java 6.0 Plugin from the software center because i run 64bit. What else is there I could do? I've been at this for days.

---

### Post by omgitsmit on 2010-11-17
> **robsonic said:**
> I have the exact same problem but can't download the Sun Java 6.0 Plugin from the software center because i run 64bit. What else is there I could do? I've been at this for days.

In my article i'm running it just fine on 64bit...

[http://timashley.me/node/596](http://timashley.me/node/596)

---

### Post by dopple on 2010-11-18
> **omgitsmit said:**
> Are you playing in a browser or from the .jar JRE file?

In browser.

---

### Post by 0akash0 on 2010-12-29
> **omgitsmit said:**
> In my article i'm running it just fine on 64bit...

[http://timashley.me/node/596](http://timashley.me/node/596)


Thank you, it's working properly now, on 10.10 AMD64.

---

### Post by omgitsmit on 2010-12-29
> **0akash0 said:**
> Thank you, it's working properly now, on 10.10 AMD64.

Good to hear! Enjoy! :cool:

---

### Post by minimatt1 on 2011-01-11
it wont let me play come up with a black screen can someone help me :(

---

### Post by dopple on 2011-01-23
> **minimatt1 said:**
> it wont let me play come up with a black screen can someone help me :(

Which version of java are you using? If you use the sun version it worked ok for me. Also, I'm using the Java(TM) Plug-in 1.6.0_22.

---

### Post by luciform on 2011-03-19
I've solved the black screen problem (after an update to 1.3) by installing xrandr. Hope it helps.

---

### Post by TheCommissar on 2011-05-21
Hey folks. I've been running minecraft for ages w/out problems, and am on 11.04 at the moment. I've suddenly been confronted with the blank screen problem. I've been trying all the solutions here and elsewhere. I uninstalled all java via Synaptic and reinstalled the latest one, and am still getting the same problem.

When I run the .jar file, I get the login screen, but when I click "login" after "done loading" I get a black screen. 

When I try and run it in browser (chromium), I get a white screen, but it doesn't even get to logging in.

Any advice?

EDIT: I reinstalled minecraft and java. No joy. It must be a recent update.

---

### Post by dawheat on 2011-05-27
[FONT=Comic Sans MS]I Have The Same Prob[/FONT]
[FONT=Comic Sans MS]PLEASE HELP!!!!!!!!!!!!! :mad: :evil: :lolflag:[/FONT]

---

### Post by dawheat on 2011-05-27
1.open minecraft
2.click options
3.click force update
4.click ok
5.login
6.it should redownload all the packages
7.PLAY:popcorn:
 
> This Worked For Me!!!:KS

---

### Post by dawheat on 2011-05-27
> **dawheat said:**
> 1.open minecraft
2.click options
3.click force update
4.click ok
5.login
6.it should redownload all the packages
7.PLAY:popcorn:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Reccomended :lolflag:

---

### Post by Happeh on 2011-08-26
> **anthony62490 said:**
> Yeah, I get the same issue. After about 15 minutes or so, the sound cuts out. Keep in mind though that it is just an Alpha version. Besides, Notch is aware of this issue. He has it posted on his To Do list. [Item #2]("http://www.toodledo.com/views/public.php?id=td4b49fbf9c05a0")

If you haven't fixed it yet, iv'e fixed my problems with audio/minecraft by installing the sun java 6, instead of using openjdk

---

### Post by redbikemaster on 2011-08-27
I'm trying to run it online (I don't have the money to buy it right now). I have the Java plugin installed, because when I used to run it in Chrome, I'd just get a black screen after a screen flashed saying, "Switching applet", under the word Minecraft. Now, after I installed it, it acts like it's going to run, then, after it's loaded I get this error message:
```
java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.

```
The title of the dialog box that the error appears in is titled,
```

Failed to start Minecraft

```
What do these things mean and how do I fix them?

---

### Post by redbikemaster on 2011-09-11
OK, so I figured out that the problem was graphics driver-related. Never mind.

---

### Post by willyd357 on 2012-05-12
> **redbikemaster said:**
> OK, so I figured out that the problem was graphics driver-related. Never mind.

What was the problem? I'm having the same issue and I think it's being caused by my graphics drivers but I can't seem to nail it down.

---

### Post by redbikemaster on 2012-05-12
I never was able to fix it. I tried the documentation on the Ubuntu site. But I gave up. Then I acquired a Windows machine that runs it (barely). My problem was probably also due to old hardware that couldn't run it even if the drivers were fine.

---

### Post by regor210 on 2012-05-12
Open a terminal, press ctrl+alt+t all at the same time. Cut and paste the following commands into the terminal window one line at a time minus the $.

$ sudo apt-get update
$ sudo apt-get upgrade

# Run these and post what you get.

$ sudo apt-get install mesa-utils

# video driver 3D test FPS
$ glxgears

#video card and driver information
$ lspci -vmk | grep -A 8 -B 2 VGA

---

### Post by clarksonfisher on 2012-09-04
Hey all.

I'm having black-sreen issue too.

For the first time I just downloaded the minecraft jar and I installed OpenJDK Java 7 Runtime through the Ubuntu Software Center.

Maybe someone can help me out.

I tried the Force Update thing to no avail. Minecraft downloads updates and then when it goes to launch I only have a black screen.

I just ran the commands posted by Regor210 and got the following:

```

duk3@duke:~$ sudo apt-get update
[sudo] password for duk3: 
Ign http://us.archive.ubuntu.com precise InRelease
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://us.archive.ubuntu.com precise Release                               
Hit http://plexapp.com lucid InRelease                                         
Get:2 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://archive.canonical.com precise InRelease                             
Ign http://extras.ubuntu.com precise InRelease                                 
Hit http://us.archive.ubuntu.com precise-backports Release                     
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:3 http://us.archive.ubuntu.com precise-updates/main Sources [159 kB]       
Get:4 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://plexapp.com lucid/main i386 Packages                                
Hit http://archive.canonical.com precise Release.gpg                           
Get:5 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Ign http://plexapp.com lucid/main TranslationIndex                             
Get:6 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://extras.ubuntu.com precise Release                                   
Hit http://archive.canonical.com precise Release                               
Get:7 http://us.archive.ubuntu.com precise-updates/restricted Sources [3,285 B]
Get:8 http://us.archive.ubuntu.com precise-updates/universe Sources [50.1 kB]  
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://archive.canonical.com precise/partner i386 Packages                 
Get:9 http://us.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]
Get:10 http://us.archive.ubuntu.com precise-updates/main i386 Packages [379 kB]
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:11 http://security.ubuntu.com precise-security/main Sources [41.4 kB]      
Get:12 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]
Get:13 http://security.ubuntu.com precise-security/universe Sources [12.2 kB]  
Get:14 http://security.ubuntu.com precise-security/multiverse Sources [1,386 B]
Get:15 http://security.ubuntu.com precise-security/main i386 Packages [163 kB] 
Get:16 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [6,732 B]
Get:17 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [127 kB]
Ign http://plexapp.com lucid/main Translation-en_US                            
Ign http://plexapp.com lucid/main Translation-en                               
Get:18 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:19 http://security.ubuntu.com precise-security/universe i386 Packages [41.6 kB]
Get:20 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,672 B]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Get:21 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,369 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://archive.canonical.com precise/partner Translation-en_US             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en    
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://archive.canonical.com precise/partner Translation-en                
Hit http://security.ubuntu.com precise-security/main Translation-en     
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 1,106 kB in 2s (435 kB/s)                 
Reading package lists... Done
duk3@duke:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  firefox firefox-globalmenu firefox-gnome-support firefox-locale-en
  libssl1.0.0 openssl python-gst0.10 thunderbird thunderbird-globalmenu
  thunderbird-gnome-support thunderbird-locale-en thunderbird-locale-en-us
12 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 44.4 MB of archives.
After this operation, 2,699 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libssl1.0.0 i386 1.0.1-4ubuntu5.5 [1,003 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main openssl i386 1.0.1-4ubuntu5.5 [519 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main firefox-globalmenu i386 15.0+build1-0ubuntu0.12.04.1 [47.5 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main firefox i386 15.0+build1-0ubuntu0.12.04.1 [19.8 MB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main firefox-gnome-support i386 15.0+build1-0ubuntu0.12.04.1 [9,268 B]
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main firefox-locale-en i386 15.0+build1-0ubuntu0.12.04.1 [463 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main python-gst0.10 i386 0.10.22-3ubuntu0.1 [272 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main thunderbird-globalmenu i386 15.0+build1-0ubuntu0.12.04.1 [47.7 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main thunderbird i386 15.0+build1-0ubuntu0.12.04.1 [21.8 MB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main thunderbird-gnome-support i386 15.0+build1-0ubuntu0.12.04.1 [9,210 B]
Get:11 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main thunderbird-locale-en i386 1:15.0+build1-0ubuntu0.12.04.1 [366 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main thunderbird-locale-en-us all 1:15.0+build1-0ubuntu0.12.04.1 [15.6 kB]
Fetched 44.4 MB in 1min 12s (609 kB/s)                                         
Preconfiguring packages ...
(Reading database ... 181852 files and directories currently installed.)
Preparing to replace libssl1.0.0 1.0.1-4ubuntu5.3 (using .../libssl1.0.0_1.0.1-4ubuntu5.5_i386.deb) ...
Unpacking replacement libssl1.0.0 ...
Setting up libssl1.0.0 (1.0.1-4ubuntu5.5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 181852 files and directories currently installed.)
Preparing to replace openssl 1.0.1-4ubuntu5.3 (using .../openssl_1.0.1-4ubuntu5.5_i386.deb) ...
Unpacking replacement openssl ...
Preparing to replace firefox-globalmenu 14.0.1+build1-0ubuntu0.12.04.1 (using .../firefox-globalmenu_15.0+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement firefox-globalmenu ...
Preparing to replace firefox 14.0.1+build1-0ubuntu0.12.04.1 (using .../firefox_15.0+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-gnome-support 14.0.1+build1-0ubuntu0.12.04.1 (using .../firefox-gnome-support_15.0+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement firefox-gnome-support ...
Preparing to replace firefox-locale-en 14.0.1+build1-0ubuntu0.12.04.1 (using .../firefox-locale-en_15.0+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement firefox-locale-en ...
Preparing to replace python-gst0.10 0.10.22-3 (using .../python-gst0.10_0.10.22-3ubuntu0.1_i386.deb) ...
Unpacking replacement python-gst0.10 ...
Preparing to replace thunderbird-globalmenu 14.0+build1-0ubuntu0.12.04.1 (using .../thunderbird-globalmenu_15.0+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement thunderbird-globalmenu ...
Preparing to replace thunderbird 14.0+build1-0ubuntu0.12.04.1 (using .../thunderbird_15.0+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement thunderbird ...
Preparing to replace thunderbird-gnome-support 14.0+build1-0ubuntu0.12.04.1 (using .../thunderbird-gnome-support_15.0+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement thunderbird-gnome-support ...
Preparing to replace thunderbird-locale-en 1:14.0+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en_1%3a15.0+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement thunderbird-locale-en ...
Preparing to replace thunderbird-locale-en-us 1:14.0+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en-us_1%3a15.0+build1-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement thunderbird-locale-en-us ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up openssl (1.0.1-4ubuntu5.5) ...
Setting up firefox (15.0+build1-0ubuntu0.12.04.1) ...
update-alternatives: using /usr/bin/chromium-browser to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode.
update-alternatives: using /usr/bin/chromium-browser to provide /usr/bin/x-www-browser (x-www-browser) in auto mode.
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (15.0+build1-0ubuntu0.12.04.1) ...
Setting up firefox-gnome-support (15.0+build1-0ubuntu0.12.04.1) ...
Setting up firefox-locale-en (15.0+build1-0ubuntu0.12.04.1) ...
Setting up python-gst0.10 (0.10.22-3ubuntu0.1) ...
Setting up thunderbird (15.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-globalmenu (15.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-gnome-support (15.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en (1:15.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en-us (1:15.0+build1-0ubuntu0.12.04.1) ...
duk3@duke:~$ sudo apt-get install mesa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mesa-utils is already the newest version.
mesa-utils set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
duk3@duke:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
300 frames in 5.0 seconds = 59.970 FPS
300 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 59.996 FPS
301 frames in 5.0 seconds = 60.003 FPS
300 frames in 5.0 seconds = 59.999 FPS
300 frames in 5.0 seconds = 59.998 FPS
300 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 59.999 FPS
300 frames in 5.0 seconds = 59.999 FPS
300 frames in 5.0 seconds = 59.998 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 6913 requests (6913 known processed) with 0 events remaining.
duk3@duke:~$ lspci -vmk | grep -A 8 -B 2 VGA

Device:	01:00.0
Class:	VGA compatible controller
Vendor:	Advanced Micro Devices [AMD] nee ATI
Device:	RV516 XT Radeon X1600 Series (Primary)
SVendor:	Micro-Star International Co., Ltd.
SDevice:	Device 0400
Driver:	radeon
Module:	radeon

Device:	01:00.1

```

Does this info tell you what the issue is?

Is there something else that someone can recommend I try?

THANKS!


EDIT:
I posted too soon. Tried one more thing and it worked. Went back to Ubuntu Software Center and looked again at OpenJDK Java 7 Runtime and saw this time that I could optionally add icetea6-plugin. I did, Force Updated Minecraft again and it worked 8D

---

### Post by dopple on 2012-09-05
I would scrap the OpenJDK and use the official sun version. This sorted it out for me when I was having problems.

---

### Post by R33D3M33R on 2012-09-05
Is there any way to install OpenJDK 6? I'm using it on my system and it works flawlessly with minecraft. It's pretty slow on the opensource driver with X1300, but it works.

---

