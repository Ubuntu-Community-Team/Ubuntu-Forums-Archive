---
title: "Eclipse 3.2 Repository"
date: 2006-09-09
forum: Desktop Environments
---

### Post by ccerinojr on 2006-09-09
Hello all!

Loving Ubuntu. This is distro will def be my new linux home. I especially love apt-get and the Synaptic Package Manager, but I can seem to find a repository with eclipse 3.2 in it. I want to keep all of my installs donw with the package manager, but I guess if no one has a repos then I will just install from eclipse's website.

---

### Post by kflorek on 2006-09-10
eclipse shows up in Synaptic for me.

 You could go to the Settings menu of Synaptic, choose Repository, check off any binary repositories that may not be selected, and then choose Edit for each. When editing, check all the boxes. There are a lot more files available then the defaults.

 It is also possible to add repositories.

---

### Post by ccerinojr on 2006-09-10
er....ummm?
> , but I can seem to find a repository with eclipse 3.2 in it.

that doesn't really answer my question.

---

### Post by ColinG on 2006-09-10
Eclipse is in the repositories as kflorek has said (I just searched Synaptic). I cannot tell exactly which repository but if you enable all of them in Synaptic you will find it. You can then disable them again if you so wish.

This does not tell you exactly which repository but does it matter if all you want is to install Eclipse:)

---

### Post by Cable on 2006-09-10
I'm sure he understands that Eclipse is in the Ubuntu repo's.  What's he's saying is that he wants Eclipse 3.***_2_***.  The Ubuntu repo's have 3._***1***_.

---

### Post by IanVaughan on 2006-09-10
Its not in any repository that I know of, so I just downloaded it and it runs very nicely/easyly from the startup script provided. You just bung the whole extracted folder anywhere you want.

---

### Post by ColinG on 2006-09-10
Ah yes, sorry

---

### Post by ccerinojr on 2006-09-10
Ok thank you all. I guess I shall just use the tar file from eclipse.

---

### Post by yusufk on 2006-09-13
Does anyone know of any other repository that might have Eclipse 3.2 ?

---

### Post by dom on 2006-09-19
BUMP

Anybody ?

I can't find 3.2 in the synaptics repositories either. I need Java 1.5 and Eclipes 3.2.

Unfortunately I can't find Eclipse 3.2, which is odd since it's free, but perhaps it's only out a wee while.

I'm just after finding Java1.5 in the multiverse, but have to get the doc manually, no big deal i guess, i stick it in /tmp and then installer can get it from there, must be something to do with the bloody license acceptance sun have before it lets you download it.

So I've installed sun-java5-bin,demo and doc. I guess I'll pick up eclipse 3.2 manually.

Interesting points on the sun-java installation :
[LIST=1]
[*] The terminal view of the install didn't open automatically so i was there waiting, and then after a while opened the terminal to see what the delay was, only to discover there was a few prompts waiting for input !  So I accepted the license and off it went again. :)
[*] I'm using Xubuntu and it was unable to initialise Gnome, I hope that whatever it wanted it for wasn't too important!!
[*] I was glad to see that the install system seemed to remember/recognise this java install, and didn't try to install another jvm when, for e.g., i went on to install open office.org2 :)
Yep, oo2 itself says it's using java 1.5.
[/LIST]

Off to get eclipse 3.2

---

### Post by Nadim on 2006-09-19
I just installed 3.2 myself...rather odd about that help file, wasn't it?  I wonder why they didn't just provide En and Ja docs in separate packages, rather than have a manual step in the process.

Anyway, I'm replying because, while the Eclipse 3.2 install went smoothly, I found that when I try and add packages to the base SDK (like CDT, etc.) using Help -> Software Updates in the IDE, it immediately fails with:

"An exception occured while downloading feature from "http://download.eclipse.org/callisto/releases/features/org.eclipse.cdt_3.1.0.200606261600.jar".  Do you want to retry?"

I found a couple other people reporting the same problem occuring recently, and I'm not behind a firewall (other than a standard NAT router).  I'd be curious if you see the same problem...

---

### Post by firebadger on 2006-09-20
Have a look at the error log.  It should be in your eclipse workspace in .metadata/.log - it should hopefully give you more info about the error.  Paste the relevant section here if you like...

---

### Post by Nadim on 2006-09-24
I fired up Eclipse again, tried to install CDT, and got the same error.  I looked in the log, doesn't look like anything there:

================================================
!SESSION 2006-09-24 00:09:25.102 -----------------------------------------------eclipse.buildId=M20060629-1905
java.fullversion=GNU libgcj 4.1.0 (Ubuntu 4.1.0-1ubuntu8)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.core.runtime 8 1 2006-09-24 00:14:30.603
!MESSAGE
================================================

So I dunno what's going on.  I found it odd, though, that there's no real "install" script for Eclipse, or at least I didn't see it when I downloaded the SDK.  I basically unzipped/untarred the downloaded file into ~products/eclipse, and that's it...ready to run.  Though not ready to upgrade, it seems.  Am I missing some steps?

---

### Post by firebadger on 2006-09-24
Yeah, that's all you have to do.  If you aren't behind a proxy or something and that URL is accessible then I'm not sure what the problem could be.

---

### Post by Nadim on 2006-09-25
> **firebadger said:**
> Yeah, that's all you have to do.  If you aren't behind a proxy or something and that URL is accessible then I'm not sure what the problem could be.

Yup, that would be the obvious question, I probably should have answered that one preemptively.  I am behind a NAT router, but not a proxy, so unless eclipse does some crazy handshaking, listening to some special port...but I really can't believe they'd do that...or if they did, HOWTOs would be everywhere.

As an added test, I copied the URL that was in the error message above (in my earlier post #11) back into a browser window, and sure enough, I could download the file just fine.  So the repository was working, my connection was working, and the link was correct...but for some reason, while Firefox could download the file just fine, Eclipse seemed unable.  I tried a couple different times, with the same results.  

I was running the Eclipse binary as the same user where I untarred the distro, so there shouldn't have been any weird permissions problems, either.  I suppose I could run Eclipse as sudo, but given that I don't know what it's doing, and all the files / dirs are owned by my user account, I'm not sure that would be a good thing, even if it helped.

Any other ideas?  Anyone else having this problem?

---

### Post by firebadger on 2006-09-26
You definately don't need to run as root.

One thing that you might try is checking your java version.  You need Java 5 (or 1.5 - Sun's naming conventions are a little bizzare).  Just open a command line and type: 
java -version

---

### Post by Nadim on 2006-10-09
> **firebadger said:**
> You definately don't need to run as root.

One thing that you might try is checking your java version.  You need Java 5 (or 1.5 - Sun's naming conventions are a little bizzare).  Just open a command line and type: 
java -version

I was a little confused about the java requirements for Eclipse.  I thought the docs said that 1.4 was okay, but some features took advantage of 1.5.  Dapper Drake installs 1.4.2 by default (in the java-common package).  I wanted to upgrade, but it looks like the java5 packages (sun-java5-bin, et.al.) don't exactly upgrade, they coexist, and they don't replace /usr/bin/java.  So, I decided not to muck with ubuntu's install too much, and left /usr/bin/java as the 1.4.2 version, and added a /usr/bin/java5 symlink.  

In any case, eclipse runs just fine and all (except for the upgrade behavior), so I'd be a bit surprised if it was the java version that was causing this problem.

---

### Post by Nadim on 2006-10-12
Well how about that...that was certainly the problem.  I guess I should know better than to trust the docs when they say 1.4.2 is okay, but 1.5 is recommended.  

After I ran:

sudo update-alternatives --config java

and selected java 1.5, bingo, it worked.  Thanks! :)

---

### Post by 4tro on 2006-10-20
But i don't understand why the new version isn't in the repo's yet, not even in the edgy eft repo's. though i can understand that eclipse 3.2 isn't priority no. uno this close to the release date of edgy ^^

*update*
it is included since the latest release candidate ^^

---

### Post by esmail on 2007-05-14
> **dom said:**
> BUMP

Anybody ?

I can't find 3.2 in the synaptics repositories either. I need Java 1.5 and Eclipes 3.2.

Unfortunately I can't find Eclipse 3.2, which is odd since it's free, but perhaps it's only out a wee while.

Off to get eclipse 3.2

Yeah, I was looking for 3.2 myself too, odd.

I am having problem with the Ruby Development Tools plugin' and wanted to try a newer version.

Hopefully the manual install won't be a PITA, one of the great things about ubuntu is the easy update/install of software.

Started out with slackware, then RH 4.2 .. etc .. been there done that, now I just want to click a few things and have the software install itself automagically.

---

### Post by jerremy-tamlin on 2007-09-07
I've installed Eclipse 3.2.2 from Ubuntu's repositories but I need the WDT and PDT addons/versions because I want to use it to build dynamic web sites as well as desktop programs.

I've downloaded the zip archives from Eclipse.org but can't seem to find the instructions on how to install them. If I just extract them and run the binary I get error messages.

I'd really prefer to use the update manager from within eclipse but can't figure out how to get it to resolve dependencies. ie it won't install PDT unless WDT is installed and WDT depends on a whole heap of stuff and I don't know where I'm supposed to get it from. I've already spent hours slogging around Eclipse.org but haven't found any clear instructions that tell me what to do.

It's like Eclipse.org expects me to already know stuff they haven't told me. Maybe it's because I'm not a trained or professional programmer just a self taught fellow who managed to do some stuff through trial and error.

Anyway if anyone can help me get up and running so I can continue to learn from trial and error I'd be most appreciative.

Thanks.
Jesse

---

### Post by jerremy-tamlin on 2007-09-07
OK I wasn't using the right version of Java either.

I'd still like to know if there is a way to get PDT and WDT installed from the repositories though, so if any one knows...

---

### Post by Inxsible on 2007-09-07
you can download Eclipse directly from [www.eclipse.org]("http://www.eclipse.org"). Its pretty easy to set up. The repo version will always be a bit slow in updating to the newer version.

I currently have Eclipse 3.3 ..also known as Eclipse Europa on  my machine. The cool thing about Europa is that you dont have to download the whole thing. If you work only in Java, then you don't need all the JEE packages. so you cna download only the version which has Java.

Of course, if you later decide to get JEE ..you can simply update the plugins or get a new copy of the JEE version of eclipse.

They do still give out the classic version which you can configure to your liking. :)

---

### Post by Inxsible on 2007-09-07
> **jerremy-tamlin said:**
> OK I wasn't using the right version of Java either.

I'd still like to know if there is a way to get PDT and WDT installed from the repositories though, so if any one knows...
Also the JEE version of Eclipse Europa has PDE and WST included in it but it requires Java 5 or higher.

---

### Post by Inxsible on 2007-09-07
If you have already downloaded the plugins, then all you have to do is extract them in the features and the plugins folders. Normally the plugins you download will have the features and the plugins folders zipped in the same file and all you have to do is extract them in the main install directory

Hope that helps !

---

