---
title: "Wimba Voice does not work"
date: 2010-08-21
forum: Education &amp; Science
---

### Post by webusr1 on 2010-08-21
I'm taking college courses and I'm being forced to use Wimba Voice that is based off the Sun Java, I mean Oracle Java Plug-in. The folks at Wimba ([http://www.wimba.com/services/support/](http://www.wimba.com/services/support/)) don't list Ubuntu as an option. I have Sun Java Plug-in 1.6.0_20 installed and it still doesn't work. What's ironic is that last semester it worked on Ubuntu 8.04, but since I upgraded to 10.04 it doesn't work. I don't know what version of Java Plug-in was loaded with  8.04. Has anyone encountered this problem??? Any help would be greatly appreciated.

Thanks! :(

---

### Post by gunksta on 2010-08-21
Not sure about 8.04. Have you tried the sun-java5-jre? It's in the repos. Java hasn't exactly been developed at the speed of light. If it's just an issue with the new version of Java (which is weird), java5 may work a trick.

When you say it doesn't work -- could you be more specific?

Another point -- that while this is the Education & Science sub-forum, it's quite possible that the general help forum may be a better place to get help on this problem. Your problem is clearly related to education, but more eyes == more better.

---

### Post by webusr1 on 2010-08-22
No, I haven't tried Java 5. More specifically, the Java Applet tries to launch but never works. The applet on the Firefox browser denotes Initializing Audio and stops. The Audio applets never starts in order to hear the audio wav file embedded in the Wimba Voice Applet. I've tried saving and down loading the file when I click on the Wimba Applet but the download of the wav files gets an error in the download window of Firefox. Java is such a hassle to uninstall and reinnstall, that I'm reluctant to change it because it works on many other applets online. 

Can I post screen shots online on this forum to show the problem?

---

### Post by webusr1 on 2010-08-22
See the attachment of the Wimba Java Applet that doesn't operate.

---

### Post by webusr1 on 2010-08-22
Here's the Screen Shots of the browser after I click on the applet. Notice how Movie Player tries to launch, but the download never completes in the browser.

---

### Post by gunksta on 2010-08-22
I looked up which version of java came with 8.04 and here's the interesting part - it didn't. I had forgotten this, but back in the Hardy days, Java Sun Java was not distributed with Ubuntu because Java was still proprietary. It has only been in the last couple of releases that Java could be legally distributed with Ubuntu.

Do you remember - did you install Sun Java on the computer manually?

I am starting to wonder if you _may_ have a version conflict from having two different versions of Java installed.

If you did NOT install Sun Java manually, you were probably using gcj. You can make sure this is installed on your new system by installing gcj-jre.

Also - since you upgraded from 8.04, are you positive you have Sun Java installed?

---

### Post by webusr1 on 2010-08-22
Q: Do you remember - did you install Sun Java on the computer manually?
A: No, I initially installed Java under 8.04 and I used SynapticPacketMGR, however, I upgraded to Java(TM) Plug-in 1.6.0_20 by hand, and believe that's when it worked under Ubuntu 8.04. I used "update-manager -d" to move from 8.04 to 10.04. It was a real pain to get Java working again after that. I removed java completely and finally get it installed in 10.04 by hand without SynapticPktMGR.

Comment: I am starting to wonder if you _may_ have a version conflict from having two different versions of Java installed.
A: I thought the same so I did some research and found that I can view the JavaControlPanel and verify that only JRE 1.6._20 is installed. I had the same problem at work, but under windoze. We have two systems that require users use the Java client Plug-in and after we upgraded the application server the users have really weird problems with their Java Plugin. I don't want to go into that scenario. This month has been Java Plugin issue month.

Q: If you did NOT install Sun Java manually, you were probably using gcj. You can make sure this is installed on your new system by installing gcj-jre.
A: I believe I only have Sun Java. When I type about:plugins in Firefox it only denotes Sun Java(TM) Plug-in 1.6.0_20. Also I reviewed and used the ubuntu JavaInstallation Wiki ([https://help.ubuntu.com/community/JavaInstallation](https://help.ubuntu.com/community/JavaInstallation)) when I installed by hand and spent a few days re-installing Sun Java. It's a hassle and there's a lot of  info.

Q: Also - since you upgraded from 8.04, are you positive you have Sun Java installed?
A: Check about:plugins the browser and JavaControlPanel and both denote Java(TM) Plug-in 1.6.0_20

I found an old Wimba Voice user guide that stated it was supported under Java 5.0 in Linux. I downloaded JDK 5.0 Update 22 last night, but I need to find another drive or system to test it under. However, I'm still pondering if I should go through that since I'm sure Wimba has changed since then and it may be a waste of effort. 

Actually you can test your system with Wimba Voice. Here's the Wimba Voice Wizard that is suppose to run with any Java 6 plugin, Click teh orange Next button and the bottom Right area of the Screen.

[http://wimba.netspot.com.au/wimba/wizard/launcher.jsp?show=wizard.frames](http://wimba.netspot.com.au/wimba/wizard/launcher.jsp?show=wizard.frames)

Also, it will immediate denote "Troubleshoot Browser " Click GoToNEXT Step under the Box and it will Test all Other Java features and it will fail very similar to my screen shot. The test will pass: Java, Signed Applet, Connectivity and Fail to initialize the Audio Playback exactly as I have describe in the first Screen shot.

Please let me know what results you get.

Thanks!

---

### Post by webusr1 on 2010-08-22
Folks, can you guys test the Wimba Voice Java application on your version of Ubuntu and see if works??? 
Here are some notes on my results:Also, it will immediate denote "Troubleshoot Browser " Click GoToNEXT  Step under the Box and it will Test all Other Java features and it will  fail very similar to my screen shot. The test will pass: Java, Signed  Applet, Connectivity and Fail to initialize the Audio Playback exactly  as I have describe in the first Screen shot.

Please let me know what results you get.


URL for TEST: [http://wimba.netspot.com.au/wimba/wi...=wizard.frames]("http://wimba.netspot.com.au/wimba/wizard/launcher.jsp?show=wizard.frames")

---

### Post by gunksta on 2010-08-22
Perhaps I am missing something on their website, but I do not see any way to download Wimba Voice from the website. Testing/figuring out proprietary problems on Linux is rarely easy and this is one of the reasons why.

---

### Post by webusr1 on 2010-08-23
The Wimba Website basically has a Setup Wizard that verifies that the Java Plugin is working on your end or the client. What we should see is the Wimba Voice Java Applet of an Audio Panel that let's you playback an audio sound clip. The main problem is that the Wimba Voice Java Applet doesn't work with Ubuntu that have Sun Java Plug-in U20 for me. So I was curious if it worked for your version of Java... So, teh crux of the matter here is that colleges are deploying these Wimba systems that do not work with Linux. They only work with M$ windoze PCs and we're back to step one or back to the M$_Mono_Culture... Thanks for trying... I don't how I be able to complete all these course requirements this semester if this silly Wimba Voice applet doesn't work on Ubuntu.

---

### Post by gunksta on 2010-08-24
Weird -- I could have sworn I wrote  a reply to this last night but I don't see it here. So, if it looks like I double posted -- Sorry!

I didn't noticed the link to the test suite. You're right -- that is darned useful and you're right they are using USer Agent strings to look for Windows/Mac. Fortunately, that's easy to get around. Just install the Firefox Extension "User Agent Switcher". Go to Tools --> Add-Ons and choose "Get Addons". Search for the term "user". The necessary extension should be your first choice.

That should get us past the first hurdle. I then ran into a problem because I am running a 64-bit version of Ubuntu and Java, in it's infinite cross-platform wisdom, is not released in a 64-bit version. 

Yeah. Awesome. And Oracle/Sun wonders why Google decided to create Dalvik.

Anywho, I digress. I'm going to have to install a 32-bit version of firefox locally to get Java to work. I'm going to do that and then try (again) to complete the process. If you are already running a 32-bit OS, you may have more luck once you install the User Agent Switcher.

Once you install the switch, you can set it up to tell the website that you want it to pretend to be Internet Explorer 8 on Windows.

Another option -- If you know anyone with a copy of the XP or Win7 disks (non-OEM) you could install Windows into a virtual machine and run the software that way. But, it's more interesting to get it to work on Linux.

---

### Post by webusr1 on 2010-08-27
NO luck... Tried User Agent, but the Java Plug-in didn't kick it. I also tried CrossOver by codeweavers using IE7, but again Java Plug-in didn't kick in... I'm stumped... Unfortunately, I'll have to find a way to run windoze... I heard that there is a Wimba Forum. I'm gonna try a post there and ask that they support Ubuntu Linux. I'll come back and post my results and response. Maybe if enough folks on the Ubuntu forum request this support, it may entice Wimba to allow it to work with Ubuntu.  Here's the Wimba Forum URL: [http://www.wimba.com/community/](http://www.wimba.com/community/)  I will find time this weekend to register and advocate support for Ubuntu on their platform.

---

### Post by sousedstvi on 2011-01-16
> **gunksta said:**
> Firefox Extension "User Agent Switcher".

That should get us past the first hurdle.

gunksta, did you actually get this to work? all reports I've seen on this experiment are negative.

in FF, I can't get past the Java test.
in chrome (which also  has a user agent switcher extension now), I can get to the audio test, but I hear no audio.

thanks for your interest
christopher

---

### Post by marseille on 2011-02-16
please keep this thread alive. wimba is killing me... i'm in the same slow boat at school, too.

my story: i'm running 10.04 on a preempt kernel with proprietary java installed (the open source version was a complete no-go on wimba). i can get all the way to the audio test. the player comes up and the little speakers indicate there's sound but in reality, there's no sound. i don't have this problem with java applets in general until i get to wimba.

also, when i took a look at wimba running on windows, it looks nothing like the test i received on ubuntu... whether or not that's important, i have no idea but it's important that i be able to get into wimba to take at least 4 tests.

thank-you. as always... i <3 my ubuntustudio ):P

---

### Post by tog on 2011-08-18
Ok, count me in on "this is not working."

Running Ubuntu 11.04 X64, and the about:plugins shows IcedTea-Web Plugin (using IcedTea-Web 1.1.1 (1.1.1-0ubuntu1~11.04.1))

I did install sun-java-6, but no help on 64bit plugin.

I get to the audio test, but can't hear any audio. 

Tog

P.S. Follow up: I ran this on a newly installed 11.04 32bit version, and with the icedTea plugin, audio works well.

---

### Post by internetprofiles1 on 2012-01-14
I recently posted about this and still no support on it. Buts Its interesting you had it working with ubuntu 8.04. I'm thinking its the java version. There was a forum about a similar issue with windows PC's experiencing the same thing and the fix was to downgrade to java6u7 I tried that with ubuntu and it was no go.

---

### Post by internetprofiles1 on 2012-01-16
Hey guys great news I'm using wimba on linux right now Jan 17 2011.

I was able to reproduce the results of webuser1  and got Wimba voice to load and it works fine. It records and plays back with no problem as quick as it does on windows. Maybe someone else might want to fool around with this..please ask me as many questions while I got this working over the next hour so I can run any command. I'm hoping if we can figure this out for why it works with Ubuntu 8.04 we can get it to work with other versions of Ubuntu

Specs in use right now.

Ubuntu version: I'm running a live cd of Ubuntu 8.04LTS for the testing.

Browser: Firefox 3.0

java versions showing us on system..I was really messing around so it shows several versions in use

ubuntu@ubuntu:~$ sudo update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/gij-4.1
*         3    /usr/bin/cacao
 +        4    /usr/lib/jvm/java-gcj/jre/bin/java


according to that list I'm using cacao for java, however I installed Java6u20 by hand like user1 said and made a symbolic like to /usr/lib/xulrunner-addons/plugins

to install java6u20 bin file you get it from the java archives, oracle requires you to sign up  now just to get s stupid archive, so i just made up anything and sending their stuff to my spam email,

link is 
[http://www.oracle.com/technetwork/java/javasebusiness/downloads/java-archive-downloads-javase6-419409.html](http://www.oracle.com/technetwork/java/javasebusiness/downloads/java-archive-downloads-javase6-419409.html)

goto 
**Java SE Runtime Environment 6u20**


download the bin to desktop
jre-6u20-linux-i586.bin



I unpacked the file with

cd Desktop
then ran chmod -x jre-6u20-linux-i586.bin
then ran ./jre-6u20-linux-i586.bin

then I went to the directory /usr/lib/xulrunner-addons/plugins

from there i ran  sudo ln -s /home/ubuntu/Desktop/jre1.6.0_20/plugin/i386/ns7/libjavaplugin_oji.so

I don't know how it just worked all of a sudden I tried several java versions and this is the only one that worked. 

I am thinking it has something to do with this part

 There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/gij-4.1
*         3    /usr/bin/cacao
 +        4    /usr/lib/jvm/java-gcj/jre/bin/java

Here is my firefox about:plugins notice it also has both java and gcj plugins in the list. Like I said this Works right now. I did get a device busy error when running from a wimba test site [http://austincc.wimba.com/austincc/wizard/launcher.jsp](http://austincc.wimba.com/austincc/wizard/launcher.jsp) 

but i just hit next and it works. When I went to my schools website it does not give me anyerrors. I been only using Ubuntu 6 months, so if anyone needs more detailed info on my current specs, to see if we can relate this to the current Ubuntu versions ask now before I shut of the live CD. again I think its a combination of the java cacao and the java6u20 that does the trick. I'll have to reboot the live CD to see if I can reproduced this everytime.

about:plugins list from Firefox 3.0

**Java(TM) Plug-in 1.6.0_20-b02**

 File name:  libjavaplugin_oji.so Java(TM) Plug-in 1.6.0_20   MIME Type Description Suffixes Enabled    application/x-java-vm Java™ Plug-in 
Yes   application/x-java-applet Java™ Plug-in Applet 
Yes   application/x-java-applet;version=1.1 Java™ Plug-in 
Yes   application/x-java-applet;version=1.1.1 Java™ Plug-in 
Yes   application/x-java-applet;version=1.1.2 Java™ Plug-in 
Yes   application/x-java-applet;version=1.1.3 Java™ Plug-in 
Yes   application/x-java-applet;version=1.2 Java™ Plug-in 
Yes   application/x-java-applet;version=1.2.1 Java™ Plug-in 
Yes   application/x-java-applet;version=1.2.2 Java™ Plug-in 
Yes   application/x-java-applet;version=1.3 Java™ Plug-in 
Yes   application/x-java-applet;version=1.3.1 Java™ Plug-in 
Yes   application/x-java-applet;version=1.4 Java™ Plug-in 
Yes   application/x-java-applet;version=1.4.1 Java™ Plug-in 
Yes   application/x-java-applet;version=1.4.2 Java™ Plug-in 
Yes   application/x-java-applet;version=1.5 Java™ Plug-in 
Yes   application/x-java-applet;version=1.6 Java™ Plug-in 
Yes   application/x-java-applet;jpi-version=1.6.0_20 Java™ Plug-in 
Yes   application/x-java-bean Java™ Plug-in JavaBeans 
Yes   application/x-java-bean;version=1.1 Java™ Plug-in 
Yes   application/x-java-bean;version=1.1.1 Java™ Plug-in 
Yes   application/x-java-bean;version=1.1.2 Java™ Plug-in 
Yes   application/x-java-bean;version=1.1.3 Java™ Plug-in 
Yes   application/x-java-bean;version=1.2 Java™ Plug-in 
Yes   application/x-java-bean;version=1.2.1 Java™ Plug-in 
Yes   application/x-java-bean;version=1.2.2 Java™ Plug-in 
Yes   application/x-java-bean;version=1.3 Java™ Plug-in 
Yes   application/x-java-bean;version=1.3.1 Java™ Plug-in 
Yes   application/x-java-bean;version=1.4 Java™ Plug-in 
Yes   application/x-java-bean;version=1.4.1 Java™ Plug-in 
Yes   application/x-java-bean;version=1.4.2 Java™ Plug-in 
Yes   application/x-java-bean;version=1.5 Java™ Plug-in 
Yes   application/x-java-bean;version=1.6 Java™ Plug-in 
Yes   application/x-java-bean;jpi-version=1.6.0_20 Java™ Plug-in 
Yes  **iTunes Application Detector**

 File name:  librhythmbox-itms-detection-plugin.so This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.   MIME Type Description Suffixes Enabled    application/itunes-plugin 

Yes  **Default Plugin**

 File name:  libnullplugin.so The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.   MIME Type Description Suffixes Enabled    * All types .* No  **Demo Print Plugin for unix/linux**

 File name:  libunixprintplugin.so The demo print plugin for unix.   MIME Type Description Suffixes Enabled    application/x-print-unix-nsplugin Demo Print Plugin for Unix/Linux .pnt Yes  **Totem Web Browser Plugin 2.22.1**

 File name:  libtotem-basic-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.22.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-ogg - ogg Yes   application/ogg Ogg multimedia ogg Yes   audio/ogg Ogg Audio oga Yes   audio/x-ogg Ogg Audio ogg Yes   video/ogg Ogg Video ogv Yes   video/x-ogg Ogg Video ogg Yes   application/annodex - anx Yes   audio/annodex - axa Yes   video/annodex - axv Yes   video/mpeg MPEG video mpg, mpeg, mpe Yes   audio/wav WAV audio wav Yes   audio/x-wav WAV audio wav Yes   audio/mpeg MP3 audio mp3 Yes   application/x-nsv-vp3-mp3 NullSoft video nsv Yes   video/flv Flash video flv Yes  **Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)**

 File name:  libtotem-complex-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.22.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    audio/x-pn-realaudio-plugin RealAudio document rpm Yes  **VLC Multimedia Plugin (compatible Totem 2.22.1)**

 File name:  libtotem-cone-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.22.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-vlc-plugin unknown 
Yes   application/vlc unknown 
Yes   video/x-google-vlc-plugin unknown 
Yes  **Windows Media Player Plug-in 10 (compatible; Totem)**

 File name:  libtotem-gmp-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.22.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-mplayer2 AVI video avi, wma, wmv Yes   video/x-ms-asf-plugin ASF video asf, wmv Yes   video/x-msvideo AVI video asf, wmv Yes   video/x-ms-asf ASF video asf Yes   video/x-ms-wmv Windows Media video wmv Yes   video/x-wmv Windows Media video wmv Yes   video/x-ms-wvx Microsoft ASX playlist wmv Yes   video/x-ms-wm ASF video wmv Yes   application/x-ms-wms Windows Media video wms Yes   application/asx Microsoft ASX playlist asx Yes   audio/x-ms-wma Windows Media audio wma Yes  **DivX® Web Player**

 File name:  libtotem-mully-plugin.so DivX Web Player version 1.4.0.233   MIME Type Description Suffixes Enabled    video/divx AVI video divx Yes  **QuickTime Plug-in 7.2.0**

 File name:  libtotem-narrowspace-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.22.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    video/quicktime QuickTime video mov Yes   video/mp4 MPEG-4 video mp4 Yes   image/x-macpaint MacPaint Bitmap image pntg Yes   image/x-quicktime QuickTime image pict, pict1, pict2 Yes   video/x-m4v MPEG-4 video m4v Yes  **GCJ Web Browser Plugin 0.96-pre**

 File name:  libgcjwebplugin.so The GCJ Web Browser Plugin executes Java applets.   MIME Type Description Suffixes Enabled    application/x-java-vm GCJ class,jar Yes   application/x-java-applet GCJ class,jar Yes   application/x-java-applet;version=1.1 GCJ class,jar Yes   application/x-java-applet;version=1.1.1 GCJ class,jar Yes   application/x-java-applet;version=1.1.2 GCJ class,jar Yes   application/x-java-applet;version=1.1.3 GCJ class,jar Yes   application/x-java-applet;version=1.2 GCJ class,jar Yes   application/x-java-applet;version=1.2.1 GCJ class,jar Yes   application/x-java-applet;version=1.2.2 GCJ class,jar Yes   application/x-java-applet;version=1.3 GCJ class,jar Yes   application/x-java-applet;version=1.3.1 GCJ class,jar Yes   application/x-java-applet;version=1.4 GCJ class,jar Yes   application/x-java-applet;version=1.4.1 GCJ class,jar Yes   application/x-java-applet;version=1.4.2 GCJ class,jar Yes   application/x-java-applet;jpi-version=1.4.2_01 GCJ class,jar Yes   application/x-java-bean GCJ class,jar Yes   application/x-java-bean;version=1.1 GCJ class,jar Yes   application/x-java-bean;version=1.1.1 GCJ class,jar Yes   application/x-java-bean;version=1.1.2 GCJ class,jar Yes   application/x-java-bean;version=1.1.3 GCJ class,jar Yes   application/x-java-bean;version=1.2 GCJ class,jar Yes   application/x-java-bean;version=1.2.1 GCJ class,jar Yes   application/x-java-bean;version=1.2.2 GCJ class,jar Yes   application/x-java-bean;version=1.3 GCJ class,jar Yes   application/x-java-bean;version=1.3.1 GCJ class,jar Yes   application/x-java-bean;version=1.4 GCJ class,jar Yes   application/x-java-bean;version=1.4.1 GCJ class,jar Yes   application/x-java-bean;version=1.4.2 GCJ class,jar Yes   application/x-java-bean;jpi-version=1.4.2_01 GCJ class,jar Yes

---

### Post by internetprofiles1 on 2012-01-16
I'm in synaptic manager, ran a search for java, here is a list of all the packages showed installed:

package     version
cacao         0.97-4
classpath    2:0.96.1
classpath-common 2:0.96.1
classpath-gtkpeer 2:0.96.1
gcj-4..1-base 4.1.2-18
gcjwebplugin 2:0.96.1
gcjwebplugin-4.1  4.1.2-18
gcjwebplugin-4.2 4.2.4-1
gij-4.1     4.1.2-18
java-gcj-compat-plugin  1.0.77-2
libgcj7-1     4.1.2-18


a search for sun just came up with the first 4 listed above.

now with this info i should be able to start revoming packages or just reload the live cd to see why this really worked and what we need to do to get this pushed to newer versions. I might try to first update the browser and see if than will cause a problem or not.

---

### Post by internetprofiles1 on 2012-01-17
Removing all other verions of java and the gcj plugin from firefox  wimba voice  still worked on ubuntu 8.04  lts running live cd. the only time it crashed and give error init voice was when i upgraded firefox from 3.0 to 3.6 evertything stopped working and the java6 u 20 plugin is not recognized by higher versions of firefox. So solution seems to be to get wimba to work we need firefix 3.0 and java 6 u 20 this is in a 32 bits ubuntu 8.04 someone can try to Get these versions of firefox and java working on ubuntu 11.10 and thing is to just dual boot the latest ubuntu with ubuntu 8.04 and we can avoid windoze all together

---

### Post by internetprofiles1 on 2012-01-21
I done a bit of trouble shooting and eventually downgraded /reinstalled to the Ubuntu 8.04LTS as my starting point. I disabled all distribution updates in the repository.
Ok like I said wimba works with firefox 3.0 with java6u20 plugin I also got it to work with the latest java version 6u 30. I installed the latest firefox 9.0 in another directory and wimba also works with the latest version of firefox. I incorrectly mention that it does not, work on firefox versions higher than 3.0, however the symbolic link for the firefox versions higher than 3.0 uses the libnpjp2.so plugin that is found in the jre1.6.0_30/lib/i368 folder and not in the plugin folder of the extracted bin file. This is all done via Ubuntu 8.04LTS. I have a live cd on 10.04 and wimba does not work with that version of Ubuntu. So it not the browser and its not a faulty java plugin, I guessing a dependency found in 8.04 is not in later versions of ubuntu. It does NOT work with the icetea6 plugins either.
this is the testing site which runs the wimba voice applet. I was able to get opera browser version 11.11 (version 11.60 is faulty and crashes a lot) so between that and firefox 3.0  and firefox 9.0 I can do anything i need for browsing I no longer need to run virtual box with windows install...guess i&#314;l be sticking with 8.04 version for a while.

[http://austincc.wimba.com/austincc/wizard/launcher.jsp](http://austincc.wimba.com/austincc/wizard/launcher.jsp)

---

### Post by marseille on 2012-02-02
Ok this is really good news! Wimba isn't going anywhere so it's good to know that there is some sort of solution. I still have my 8.10 on file so I'm going to have to try this.

And thank you so much for your hard work! :KS:KS:KS:KS:KS

---

