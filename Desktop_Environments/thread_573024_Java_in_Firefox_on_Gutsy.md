---
title: "Java in Firefox on Gutsy"
date: 2007-10-11
forum: Desktop Environments
---

### Post by tbresson on 2007-10-11
Yesterday I downloaded the version 6 update 3 from Java.com and tried to install it on my Gutsy. I made a symlink to the java plugin inside the firefox plugin folder but it doesn't work.

I've never had any problems installing java on my own before but suddenly it doesn't work.

I don't know if it's the new java version (I run update 1 at home on 7.04 and that works fine) or if it's related to Gutsy.

Anyone experienced the same ?

BTW: I do know there's a cool guide in Gutsy concerning plugins and I do know you can install java with the Add/Remove. That is not my question. But thanks though if you thought it would help :)

---

### Post by gibbsnich on 2007-10-12
Did you try to run any java application from the command line or via webstart, just to make sure the jre itself is installed correctly?
What does about:plugins in firefox say? Anything about java there..
You made a symlink in /usr/lib/mozilla/plugins/libjavaplugin.so to /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so (or whereever you installed it; note the 'ns7' subdirectory)?

That's all the questions I'd ask myself.. HTH!
Michael

---

### Post by tbresson on 2007-10-12
I installed it via console.

The about:plugin says:
Java(TM) Plug-in 1.6.0_03-b05

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_03

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_03 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_03 	Java 		Yes

and yes the symlink is made inside the ns7 dir.

I installed the same java on my 7.04 ubuntu at home yesterday and that worked ok. Same installation, same method on my Gutsy doesn't.

A user on a danish ubuntu forum is having the same problems as I but with 7.04 - which is strange.

---

### Post by AgentZ86 on 2007-10-12
Strange, I didn't have to install anything on Gutsy,

Basically I was browsing and is said to install missing plugins with so I did, and I't appears to work mostly, but there are some sites I go to that appears to missing some things, I think it's something to do with java but not sure.

---

### Post by jespdj on 2007-10-12
Java 6 Update 3 is already in the Ubuntu repository. Did you install it from the repository with synaptic or apt-get, or did you download it manually from Sun and are you trying to install it yourself?

Just do it from the Ubuntu repository, that's much easier. No need to try and do it manually.

---

### Post by sent17inel on 2007-10-13
When i try to install it from the repository im getting errors saying that the file needs to be owned by root and copied to the /tmp directory... but its gay cuz it never asks me for my password.. and i sudo'ed that when i started the install.... It was like sudo jre-java6 or something... and then i tried jdk and they keep giving me similiar errors without a way to input my password...

---

### Post by AgentZ86 on 2007-10-13
> **sent17inel said:**
> When i try to install it from the repository im getting errors saying that the file needs to be owned by root and copied to the /tmp directory... but its gay cuz it never asks me for my password.. and i sudo'ed that when i started the install.... It was like sudo jre-java6 or something... and then i tried jdk and they keep giving me similiar errors without a way to input my password...

That is strange, I would login as root user, from the initial login screen and try it, logged in as root, user I know that may not do anything, but it sounds strange.

Cause I didn't have to do anything I installed the 7:10 and started browsing, and it asked for missing plugins via Firefox and I clicked which ones I wanted to install and that was it.

Same for Flash and java.

I didn't even use the application/add/remove or synaptic or console or any of that. it just sort of happened on it's own.

I would try login as root and go to applications/add/remove menu and remove all the java stuff if any, webstart 5, webstart 6, 1.4 all plugins etc. 

But you may have to use synaptic to uninstall some of these if they are present, but go back to the add/remove for reinstall, I don't have any real reason for that ,but easy to look at.

Or if none exist then install webstart 6 only or the ubuntu restricted extras and that will install java and flash.

Be sure to select from the pulldown menu to the right all available applications for this or java or restricted stuff will not be in the list.

If it doesn't install something is wrong. especially if your logged in as root from startup of the gui.

It's not secure, but at least you only doing this one task and perhaps browse one page or 2 then you can go back to regular user.

It does sound strange though cause when I first installed Ubuntu Gutsy it just worked as it should.

Are you using a 64bit Ubuntu ??? or something different

---

### Post by tbresson on 2007-10-15
jespdj; Thank you for your reply. But did you really read my post? I doesn't seem like it.

---

### Post by tbresson on 2007-10-16
On java.com when I check my install it keeps on searching but it doesn't find anything.
The plugin-finder doesn't popup either.

I tried removing the java I installed and removed the java plugin aswell. This time Firefox notices that the java plugin is missing and fires up the plugin finder. I decided not to install anything.

Then I went into Add/Remove programs and searched for java and I installed the Ubuntu restrictive stuff; says something about java, flash, encoding mp3's with LAME etc.

After installing this I checked on the java.com - veryfing my installation of java and now everything is fine.

I don't know what the difference is from my install to the "ubuntu add/remove installation" but I'd like to know though if anyone knows.

---

### Post by AgentZ86 on 2007-10-16
> **tbresson said:**
> Yesterday I downloaded the version 6 update 3 from Java.com and tried to install it on my Gutsy. I made a symlink to the java plugin inside the firefox plugin folder but it doesn't work.

I've never had any problems installing java on my own before but suddenly it doesn't work.

I don't know if it's the new java version (I run update 1 at home on 7.04 and that works fine) or if it's related to Gutsy.

Anyone experienced the same ?

BTW: I do know there's a cool guide in Gutsy concerning plugins and I do know you can install java with the Add/Remove. That is not my question. But thanks though if you thought it would help :)

Perhaps you needed to also install the java to your mozilla/plugins folder and add symlink to mozilla/plugins and see what happens. there as well.

Anyhow nice job on uninstalling then installing again. there are also other ways to do this, but basically if you were to select the via firefox method in general it ends up doing the same thing and also adding this installed item to your add/remove package list as being installed. 

So if you do it the via firefox request/popup thing, then basically you can still uninstall it via add/remove method cause it basically brings up the installer anyhow.

Try it a few times and play with it, don't worry it won't break I've uninstalled all the java stuff, and then re-installed various ways and it basically ends up the same either way.
But the only thing I didn't like was that I coudn't uninstall it unless I went to synaptic to uninstall those the jave stuff, then re-install via add/remove 

Well, anyhow glad it's working and happy hacking I hope this helps.

---

### Post by shanen on 2007-10-28
I'm also having problems with it. It actually worked okay after the upgrade, but there were some other problems so I decided to try a complete reinstallation from the 7.10 CD. That seemed to work, but the machine could no longer boot to Ubuntu, so I had to rebuild it from the 7.04 CD and then go through all the upgrades again. However, this time when I finally got back to Gutsy, I was absolutely not able to get Java to work from Firefox. Tried many things, but most uninstalls and reinstalls of the two Java systems (with two different versions available for Sun's system).

---

### Post by AgentZ86 on 2007-10-29
> **shanen said:**
> I'm also having problems with it. It actually worked okay after the upgrade, but there were some other problems so I decided to try a complete reinstallation from the 7.10 CD. That seemed to work, but the machine could no longer boot to Ubuntu, so I had to rebuild it from the 7.04 CD and then go through all the upgrades again. However, this time when I finally got back to Gutsy, I was absolutely not able to get Java to work from Firefox. Tried many things, but most uninstalls and reinstalls of the two Java systems (with two different versions available for Sun's system).

NO need to install manually, however it is strange to have java problem like this on my system it all just works and I can uninstall and install at will from the applications/add-remove feature of the standard ubuntu installation.

I did have to pull down the menu to include all available applications so that I could find the java 6 webstart with installs everything for java, or the extras file which installs also flash for your firefox etc.

Anyhow I'm not sure if this will help but it's very strange.

when you go to firefox and type about:plugins in the address bar do you see your java as installed and enabled or not ?

---

### Post by KUMARPTb on 2008-04-15
I am also having problem in linking java plugin to firefox. I am unable to find the ns7 folder after the installation of java 6.0.3.  I am not able to link the java plugin to firefox. I had installed java through apt-get. If anyone had faced this issue kindly let me know how to resolve.

---

