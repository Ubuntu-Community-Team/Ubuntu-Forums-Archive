---
title: "HowTo install Power Etrade Pro"
date: 2006-01-25
forum: Desktop Environments
---

### Post by David Valentine on 2006-01-25
Having repeatedly Googled "Power Etrade Pro Linux" with somewhat negative results (e.g., forum posts claiming that Power Etrade Pro doesn't run under Linux), I stumbled upon the simple easy solution that had eluded me.  Just in case there's another Ubuntu newbie out there who wants to run Power Etrade Pro, here's what I did.

1.  Open System/Administration/Add Applications
2.  Select and install Java Web Start from the Internet category (this has to be done even if you already have Java installed--this was what I hadn't realized!)
3.  Close the Add Applications applet
4.  Log in to your Etrade account, and go to Power Etrade under trading (should be available if you're an active trader)
5.  Click the Launch button for Power Etrade Pro.  Etrade will check to see that Java Web Start is installed, and if it finds it you'll get a dialog box asking what to do with a .jnlp file.  Accept the default "launch with" option (should be Java Web Start), and it's all automated from there.  If instead you are asked about opening or downloading a .exe file, then Etrade did not find your Java Web Start and is attempting to give you the Windows setup application.  I've heard you can install and run Power Etrade Pro this way under Wine, but it is unnecessary.

---

### Post by David Valentine on 2006-01-25
Apologies to all:  the above should have been posted in the tips & tricks forum.  Can an administrator move it over?

---

### Post by solderhead on 2007-04-19
David -- I have been using PETP under Linux for quite some time now.  I've run into quite a few problems, maybe you're familiar with them.

At the time that I write this, PETP is supported on the following sub-releases of Java 1.5:  6, 9 and 10.  It is unsupported on Java 1.5 sub releases 7 and 8, and on Java 6.1.

The bottom line is that if you use one of the supported sub-releases, PETP will work.  If you use one of the unsupported sub-releases, PETP will function horribly and it will be an unreliable platform.

To get the system to be reliable, you have to either be lucky enough to have installed the correct Java sub-version, and never update it, or you have to know Debian well enough to know how to manage the installation of specific Java sub package releases.

I've found your thread by looking for information about how to fall back to a specific Java subversion.  I have been using Edgy, and I made the mistake of accepting an Adept-Updater update that killed my PETP application by installing  Java 1.5_08.  Now I need to find out how to fall back to version 7.  In my efforts to fix things, I've updated the system to Feisty Fawn.  The default Java is 1.5_11, which is no good either. :confused:

---

### Post by luis.alves@lafaspot.com on 2007-06-18
Hi,

I noticed if I use 

"sudo apt-get install ubuntu-restricted-extras"

to install java in Feisty, Firefox does not detect java web start on the etrade web site
I have no idea if this is a etrade problem or a firefox problem.

But Opera works fine to install Power Etrade Pro, and you can get Opera from this ubuntu repository

#Ubuntu Commercial
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) feisty-commercial main

After installing Power Etrade Pro using Opera, Firefox will also be able to start PETP.

---

### Post by luis.alves@lafaspot.com on 2007-06-18
Etrade MarketCaster also worked fine for me in Firefox and Opera.

---

### Post by luis.alves@lafaspot.com on 2007-06-18
- After installing the Power Etrade using Opera.
- stop Opera and start Firefox
- click on the MarketTrader icon and Firefox wiil install MarketTrader
- But not all is good. MarketTrader gets stuck on the startup sequence.


Conclusions:

Power Etrade and MarketTrader install a local JVM 1.5 in the cache of JDK 1.6: /home/{USER}/.java/deployment/cache/6.0/ext/E1182155459677/jre1.5.0_11/bin/java

MarketTrader gets stuck opening the panels.

Opera is not able to install MarketTrader

Firefox is not able to install Power Etrade Pro

MarketCaster works with no problems on both browsers in ubuntu Feisty.

Power Etrade works fine on both browsers after you find a way to install it on your system.

Etrade should:
- Do more testing on linux desktop platforms.
- Put some instructions on the configurations that they tried on their web site
- It is frustrating not being able to run these apps because some small details are missing in the WebSite autodetection code.
- Etrade web site lacks descriptions on how to make the apps work on any Linux.

---

### Post by Minosti on 2007-06-18
From my understanding the Trader application stops loading the panels when Java 1.6 is detected.  The only resolution is to completely remove all the Java on the system, then install Java 1.5 via their archive website (update 10 works the best).  The fact that you stated that Java cache was filtering through Java 6.0 means there are still components of 6.0 coming into play when launching Trader.  

Hope this helps.

---

### Post by solderhead on 2007-06-23
> **luis.alves@lafaspot.com said:**
> -
Etrade should:
- Do more testing on linux desktop platforms.
- Put some instructions on the configurations that they tried on their web site
- It is frustrating not being able to run these apps because some small details are missing in the WebSite autodetection code.
- Etrade web site lacks descriptions on how to make the apps work on any Linux.
Actually, its not eTrade's problem -- its a linux issue.  Although the information that I provided earlier on Java releseases was not obtained from a web link, it was obtained from eTrade technical support, and it was very easy to obtain.  In fact, when you call tech support and report incompatibility issues, checking your Java version is the first thing that eTrade Level 1 tech support does.  they are very well trained, and they are very quick to identify the problem.  

To anyone who has read this thread or spoken to eTrade tech support, It is well established common knowledge that  eTrade supports specific versions of Java, and if you have one of the supported versions properly installed the eTrade Java application will work. If you have the wrong versions of Java installed, the Java app will not work.  In telling you which specific versions will work and which specific versions will not work, eTrade has done their job.  

It is the USER's responsibility to assure that their OS has the correct Java implementation.  Considering that there are 1001 different flavors of Linux, its not reasonable to expect anyone to support all of them.  Bear in mind that Linux remains a computing enthusiast's operating system.  Its not Windows.

If the user chooses an OS that uses the wrong version of Java, then its the USER's responsibility to become familiar with the distribution's package management system to allow them granular control over package management.    Using a shotgun approach of installing every different browser and then complaining that they all don't work is not a reasonable solution.  Doing that only suggests that you've purposefully ignored all of the information that's already been offered  about the problem, and you've intentionally chosen the least technically appropriate approach to the problem.  I hate to say it, but choosing the most blunt tool in the toolshed is a Windows user's approach if I ever saw one.

Not that I blame you -- getting a firm grasp on the intricacies of de-installing one Java release and reinstalling another on Kubuntu isn't inherently obvious.  I tried it after the upgrade to Feisty borked my Java setup, and I found myself wandering through a dizzying array of undocumented symlinks.  The end result is that the Java version change never became functional.  I'm still looking for the answer and I haven't found it yet.  But at least I am confident that I am taking the right approach to solving the problem.  I just need information that I havent' been able to find ... yet.

---

### Post by solderhead on 2007-06-23
> **Minosti said:**
> From my understanding the Trader application stops loading the panels when Java 1.6 is detected.  The only resolution is to completely remove all the Java on the system, then install Java 1.5 via their archive website (update 10 works the best).  The fact that you stated that Java cache was filtering through Java 6.0 means there are still components of 6.0 coming into play when launching Trader.  

I think you're on target about the incompatability issue.  It sounds like you've got PETP up and running.  I hope that you don't mind if I try to pump you for technical details.

Kubuntu isn't my first linux distro.  I've been using linux for 5 years or so, and I spent the last couple of my linux years with Gentoo.  Gentoo was very helpful in developing the ability to learn where your knowledge of the OS falls short, and where you need to learn something to fill in the gaps.  With Gentoo I was forced to learn enough about OS debugging and package management to appreciate the intracacies of this sort of problem.  One of the most frustrating things for me in migrating to Kubuntu is that the Kubuntu docs and the Kubuntu forums don't seem to provide as much command line support for OS configuration -- at least it seems that most Kubuntu users seem less likely to be command line saavy, and this seems to effect the kind of advice that's available in the forums.  

This thread has been open a long time without anyone being able to provide a concrete, detailed answer to the problem.  My problem, at least as I see it, is that for people who are not debian package management gurus, its difficult to determine how to perform the java revision.  It would be very helpful if someone who knows exactly how to do this could provide step by step instructions about how to do this on the command line.  I tried doing this following detailed instructions before, and I think that the problem ended up being related to the instructions failing to identify symlinks for the previous Java implemention that needed to be removed to effect the upgrade.  As you can imagine, without a clear method of doing this sort of thing using apt-get, without a clear roadmap of how to do it manually at the command line, and without clear documentation of all of the symlinks that are required for the Java implementation, the rollback operation suffers a high risk of failure.

I have to sheepishly admit that being a seasoned linux user, I haven't been able to find the necessary expertise in the Kubuntu support docs and the forums to solve the problem.  I'm thinking that this is probably nothing more than my own personal deficiency in understanding the intracicies of Debian package management.  Perhaps it would be helpful if someone could: 

a) provide a detailed map of the necessary symlinks that Kubuntu requires for a successful Java implementation, or 

b) give detailed, line by line instructions on how to actually perform the steps to effect the java upgrade at the command line.

kubuntu has been a bit frustrating for me, in that several people have made recommendations that seem to be right on target -- unfortunately, they paint their recommendations with broad brush strokes, and not a sequence of exact detailed keystrokes that are needed to successfully perform the task.

---

