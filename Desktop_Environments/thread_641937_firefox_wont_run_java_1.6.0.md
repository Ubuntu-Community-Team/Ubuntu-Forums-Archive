---
title: "firefox wont run java 1.6.0"
date: 2007-12-16
forum: Desktop Environments
---

### Post by putz3000 on 2007-12-16
There is much on the web and even on these forums because java and firefox on Ubuntu lately has been a major dud.  I have been fighting with my system now for 3 days trying to get firefox to register as having a java version greater than 1.4.2.  I finaly was able to remove "gcjwebplugin" which finally tossed out the 1.4.2 status.  But when I went back to java's website and tried to verify I got an instal plugin option.  I opened it up and selected the 1.6.0 version of java that I wanted but was told it was already installed and firefox should be rebooted.  i did that and still had the same problem.  So I then ran the command: 

sudo apt-get remove sun-java* 

Then went back to the java site and this time when I selected the version of java plugin I wanted, the system went out and downloaded and installed the java.....but upon shutting down the browser and reopening it, I get the same missing plugins and when I try to install it says it is already installed again.  

How can I make this work?  I am so sick and tired of dealing with this whole ubuntu/java/firefox issue that I am ready to bag linux all together again.  Does any one actually have a fix for this?

---

### Post by k0rfain on 2007-12-16
I usually use this to install java

[http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp)
[http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

and it always works =)

---

### Post by erfahren on 2007-12-16
I've never installed Java through that pop-up, but I'm thinking that pop-up is from Ubuntu itself which is kind of a new feature. Maybe the problem you spoke of is with it (that you said is mentioned much on the forums).

Anyway, there is no need to install Java anymore with the package and instructions directly from java.

First do this: just go to Synaptic and search for sun java - scroll down to sun-java6-plugin and install it (or ensure it's installed) - it will pull in the other sun java packages needed with it.

now do this in terminal:
```

sudo update-alternatives --config java

```
you should see something like:
```

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 

```
enter the selection for the sun java version you have. That will set it for system-wide use. (I think that's what that automatic install feature isn't doing.)


Note: if you don't see sun-java6 in Synaptic you need to enable all the repositories in Software Sources or manually set up the /etc/apt/sources.list file by the instructions here (make sure to add the key for Mediubuntu): [How to add extra repositories - Manual method](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method)

---

### Post by putz3000 on 2007-12-16
> **k0rfain said:**
> I usually use this to install java

[http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp)
[http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

and it always works =)


I have already done the manual install and that does nothing for the web browser.  I will poke around in the synaptic just to make sure.  I suspect I will have uninstall again and then try reinstalling / enabling through synaptic to see what happens.  Also, I have previously ran the sudo update-alternatives --config java and it is still correctly marked but to no avail in the browser.  But assuming maybe it did not install throughout the system properly I will still play around in the synaptic area....lets keep the fingers crossed.

thank you to both of you for trying to help me on this.  Lets hope something takes.

---

### Post by erfahren on 2007-12-16
the output of
```

java -version

```
gives the version that is set to system wide use, see what that says

---

### Post by putz3000 on 2007-12-16
robert@robert-laptop:~$ java -version
The program 'java' can be found in the following packages:
 * j2re1.4
 * kaffe
 * cacao
 * java-gcj-compat
 * gij-4.1
 * jamvm
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found


robert@robert-laptop:~$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 1
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.


I finally added the 1.5.0 thinking maybe there was a problem with the latest (1.6.0) but that didn't fix anything so as you can see I switched back to the 1.6 version.  I have also through synaptic done a complete removal of all java plugins and bin and jre's as well as firefox and then reinstalled.  I have even rebooted just in case between removal and installation.  What is interesting is if I go to the java site it no longer tells me I am missing the plugin but now tells me I am missing the run time environment which I am not.  Synaptic shows the jre installed (at this time for both 1.5 and 1.6).  Also, firefox is unable to auto install the jre so it is a manual.  I have already downloaded and followed the instructions (made directory, moved file, chmod permissions for exicutable, ran the install, found the mozilla-firefox directory, cd'ed into the plugin folder, ran "sudo ln -s /usr/java/jre1.6.0_03/plugin/i386/ns7/libjavaplugin_oji.so").  but still no fix.  Firefox continues to believe there is no JRE.  It no longer seems to believe the plugin is missing, but the JRE.

---

### Post by SunnyRabbiera on 2007-12-16
well my question is, are you using AMD?

---

### Post by putz3000 on 2007-12-16
> **SunnyRabbiera said:**
> well my question is, are you using AMD?

AMD 64 x2 processor, nvidia video

---

### Post by putz3000 on 2007-12-16
I don't know if it matters, but I should also point out that I am using Ubuntu 7.10.

---

### Post by magnifica on 2007-12-17
I also struggled with Java in Firefox for several hours last night and have not resolved the problem.  If I find a fix I will let you know.

---

### Post by putz3000 on 2007-12-17
Thank you,  I have spent 3 days now on this mess and I find it very discouraging.  Especially since I finally have found a version of linux that will run and do pretty much everything I want (except gaming).  I am excited and actually don't mind using linux for the first time in my life....but I need my web browser to work..lol.

---

### Post by erfahren on 2007-12-17
@putz3000 - no one has asked this and you didn't mention it, but I'll ask just in case...
are you using the 64-bit version of Ubuntu Gutsy?

---

### Post by magnifica on 2007-12-17
Hey!  I got it working!!  w00t!  

Ok here is how I did it:

1) Through the synaptic manager, I searched for "java" and removed Java 5.0, Java 6.0 and the Icedtea Java thing.  

2) Through "add/remove programs" reinstalled Java 6.0

3) Went to Yahoo games and installed the plug-in (it gives you 4 options here.  I used the second one; the Java TM 6.0 plug-in) when asked.  Restart Firefox.

4) It works!  Verified install at the Java website.  Yahoo games work.

Try this out and please let me know if it works!

---

### Post by putz3000 on 2007-12-17
> **erfahren said:**
> @putz3000 - no one has asked this and you didn't mention it, but I'll ask just in case...
are you using the 64-bit version of Ubuntu Gutsy?

As far as I know I am running the 32-bit version.  I did not want the 64-bit and am usually pretty careful on that.  I am 99.98% positive it is 32-bit.

---

### Post by rsambuca on 2007-12-17
I can't figure out why some people are having such difficulty with java and firefox.  I hope we can pin down these problems.

@putz, can you post the output of 

uname -a

---

### Post by putz3000 on 2007-12-17
> **magnifica said:**
> 

2) Through "add/remove programs" reinstalled Java 6.0


Where is "add/remove programs"?  is this the same thing as the synaptic package manager?  I see no add/remove option through out the desktop menu system.

---

### Post by putz3000 on 2007-12-17
It looks to me like I am also back to having Java installed when it is not supposed to be.  Using the synaptic package manager, I told it to completely remove all java 5 & 6 (had no icedtea stuff).  I also from terminal ran "sudo apt-get remove java*" but firefox still believes it only needs the jre which means there is still java installed some place for firefox to latch onto.  

I am starting to think seriously that I might have messed to much with the system and I would be better off reinstalling and trying this again.

---

### Post by putz3000 on 2007-12-17
> **rsambuca said:**
> I can't figure out why some people are having such difficulty with java and firefox.  I hope we can pin down these problems.

@putz, can you post the output of 

uname -a

Linux robert-laptop 2.6.22-14-gerneric #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 G
NU/Linux

---

### Post by rsambuca on 2007-12-17
Have you tried just

sudo apt-get install ubuntu-restricted-extras

---

### Post by putz3000 on 2007-12-17
I just did the restricted-extra's, but still have the same problem.  Again, it may be because of all the stuff I had been doing to my system previously.

---

### Post by magnifica on 2007-12-17
Add/Remove should be found under the "applications" drop down menu. Top left of your screen.

---

### Post by putz3000 on 2007-12-19
> **magnifica said:**
> Add/Remove should be found under the "applications" drop down menu. Top left of your screen.

Good Grief!  I can not believe I was that blind.  Thank you.

On another note, I finally got the Java plugin working in Firefox.  But I paid a steep price for it.  I decided to reinstall Ubuntu.  I was trying to make it easy and safe (I dual boot with Vista) but in my attempt to keep things safe and easy I ended up trashing my entire hard drive losing everything!  Anyhow, after I got Ubuntu 7.10 reinstalled I:

1) edited my source.list file.
2) apt-get update.
3) apt-get upgrade.
4) went to yahoo website and used the games section to install the Java 6 plugin.

Everything now works and I even pass the test at the java website.  My biggest problem the first time around was that when I was told I was missing a plugin and I clicked on the install option I selected the first option thinking I ultimately needed all of the plugins listed.  In reality it was/is critical to select the real java 6 plugin and nothing else.  The first option I believe is what is causing all of the problems (at least for all of us noobs).  anyhow, I want to thank all of you that helped me with this problem, you have truly helped make this linux experience better for me.

---

### Post by magnifica on 2007-12-19
Dude, that cool and I'm glad that I managed to help in a small way.  

Haha...  I'm actually trying to install flash in Opera at the moment which is proving to be a headache!!  lol.  I find the my cpu goes a bit nuts when I run flash in Firefox and wanna give it a go in another browser.  Wish me luck!  

Peace :)

---

