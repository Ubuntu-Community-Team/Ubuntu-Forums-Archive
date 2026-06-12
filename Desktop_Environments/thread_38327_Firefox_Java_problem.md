---
title: "Firefox Java problem"
date: 2005-05-31
forum: Desktop Environments
---

### Post by Dogmeat on 2005-05-31
hello, I had recently java working fine on Firefox, but something's broken now. If I'm not running firefox as root (i know it's insecure, im just saying it's the only way it works now) ,I can't see any java applets, i only see blank spaces!. I have the bash.bashrc updated to jre1.5.0_03 ( i noticed today it wasn't 0_02 any longer, so I updated the $PATH/$JAVA_HOME and they now are ok)

Also azureus works fine, I just can't update to 2.3.0.2 because after I reset it it just tries to update again (go figure) so I'm not really sure if those events are related, I just want firefox to show java applets again (I did some tweaking here and I thought this could be the problem, so I undid everything i had done)  :? 

I followed instructions closely on ubuntuguide.org (the old ones about java, i can't find the sun-j2re1.5 package neither use backports because I get a 403 error) and I really can't get it working, so if someone can give me a hand or two i'd really appreciate it!   ](*,)

---

### Post by fng on 2005-05-31
for azureus : [http://ubuntuforums.org/showpost.php?p=188992&postcount=4](http://ubuntuforums.org/showpost.php?p=188992&postcount=4)
It works like a charm

I have also the same problem with firefox.
Just noticed it this morning before i got to work
I'll look into it tonight.

---

### Post by jarrett.wold on 2005-05-31
Step 1: Open sources.list file for editing
```
$ sudo gedit /etc/apt/sources.list
```

Step 2: Updating Backports

## Backports
deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-backports main universe multiverse restricted
deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-backports-staging main universe multiverse restricted
deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-extras main universe multiverse restricted
deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-extras-staging main universe multiverse restricted

Step 3: Fetching Packages
```
$ sudo apt-get install sun-j2re1.5
$ java -version
```

Or as an alternate use Synaptic to install, search for: sun-j2re1.5
```
$ sudo synaptic &
$ java -version
```

Step 4: Change to Firefox plugin directory
```
$ cd /usr/lib/mozilla-firefox/plugins
```

Step 5:  Remove old symlinks, create new ones.
```
$ sudo rm -rf *java*
$ sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so
```

Step 6: Re-Launch or Launch Firefox, Type in about:plugins in the address field to verify it working.  Then hit java.com or some other java based site.

---

### Post by fng on 2005-05-31
aha, that last symlink isn't included in the ubuntuguide.org.

---

### Post by jarrett.wold on 2005-05-31
[QUOTE=fng]aha, that last symlink isn't included in the ubuntuguide.org.[/QUOTE]
Fixed? :)

---

### Post by fng on 2005-05-31
i just ssh-ed to home and made the symlink
i'll test tonight.

---

### Post by jiyuu0 on 2005-05-31
backports sun-j2re seems fine with me...
the prob is with the sdk

anyway, that is going to be fixed soon by the maintainer.

---

### Post by Dogmeat on 2005-05-31
Azureus is now working, i discovered i had to remove Azureus2.3.0.0.jar, the problem is it was owned by root, now i chowned it to myself and It automagically updates when checking. ;-) 

About java I did what jarret.wold suggested, my about:plugins looks like this:

Java(TM) Plug-in 1.5.0_03-b07

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.5.0_03

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
application/x-java-applet;jpi-version=1.5.0_03 	Java 		Yes
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
application/x-java-bean;jpi-version=1.5.0_03 	Java 		Yes

so I guess it should work, but it doesn't! I don't get any errors or anything on applets (javascript is working however) not even in the status bar, only a damned blank space where the applet should be! I wish it would generate a log or something so I could find out what is wrong  :-?

---

### Post by fng on 2005-05-31
It works
although the directory of the .so file wasn't the 1 in the example
Mine was located here :
```
$ sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so
```

I installed j2re using the backports repo's

---

### Post by jarrett.wold on 2005-05-31
Cool ;)

---

### Post by Dogmeat on 2005-06-01
A-ha I found the elusive offender!  \\:D/ I renamed my prefs.js and java applets worked, so I started removing prefs one by one to see what was causing the screw up, and here is the little bastard:

```
user_pref("general.useragent.vendorSub", "1.0 StumbleUpon/1.9993");
``` 

I never thought a different useragent could break java apps. Maybe it's lastest version got a little too picky? Anyway if java doesn't work for any of you, reset the general.useragent.vendorSub key in about:config! Thanks to everyone who replied  :grin:

---

### Post by Ride Jib on 2005-06-01
[QUOTE=jarrett.wold]Step 5:  Remove old symlinks, create new ones.
```
$ sudo rm -rf *java*
$ sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so
```
[/QUOTE]

If you installed j2sdk instead of j2re (for fellow developers) your symlink should appear like this:
```

$ sudo ln -s /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
```

---

### Post by ChamPro on 2005-06-06
I've tried the thing you guys have suggested. Java shows up in my about:plugins now, but it's still completely borked.

I thought that using the DEBs from Synaptic for Azureus and the Sun JRE would be better than just using the bins, but I've had nothing but problems. My java -version works fine. It's just that when I run Azureus or some page in Firefox that has a Java applet on it, Java uses around 250 MBs of RAM and then does nothing. I have to end the process to get it to go away.

Any suggestions?

---

### Post by desdinova on 2005-06-10
[QUOTE=ChamPro]I've tried the thing you guys have suggested. Java shows up in my about:plugins now, but it's still completely borked.

I thought that using the DEBs from Synaptic for Azureus and the Sun JRE would be better than just using the bins, but I've had nothing but problems. My java -version works fine. It's just that when I run Azureus or some page in Firefox that has a Java applet on it, Java uses around 250 MBs of RAM and then does nothing. I have to end the process to get it to go away.

Any suggestions?[/QUOTE]
 I have exactly the same issue

---

### Post by ChamPro on 2005-06-10
Then I'm not the only one with this problem. The only solution I've found is uninstall Azureus and the Sun JRE. Reboot. Install Azureus and the JRE again. Java will work until the next reboot. After the next reboot, Java is back to using up a lot of RAM and not doing anything.

---

### Post by Dogmeat on 2005-06-12
which version of java are you using? I'm using...

```
java version "1.5.0_02"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_02-b09)
Java HotSpot(TM) Client VM (build 1.5.0_02-b09, mixed mode, sharing)

```

...nd it's been working great since I uninstalled and did everything I saw on this thread. Have you tried installing a different JRE version? also check /usr/lib/mozilla-firefox/plugins/ if the libjavaplugin_osi.so is pointing to the correct place (ie /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so in my version)

Also you should NOT have any files in the plugins folder, only symbolic links. I installed the plugins systemwide, so my ~/.mozilla/plugins folder is empty.

---

### Post by b3nw on 2005-06-12
I also had this problem, and am now a opera fan   :wink:

---

### Post by desdinova on 2005-06-12
Whats odd is that Galeon works ok, as does Epiphany - but FF freezes with Java.

---

### Post by ChamPro on 2005-06-17
[QUOTE=Dogmeat]which version of java are you using? I'm using...

```
java version "1.5.0_02"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_02-b09)
Java HotSpot(TM) Client VM (build 1.5.0_02-b09, mixed mode, sharing)

```

...nd it's been working great since I uninstalled and did everything I saw on this thread. Have you tried installing a different JRE version? also check /usr/lib/mozilla-firefox/plugins/ if the libjavaplugin_osi.so is pointing to the correct place (ie /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so in my version)

Also you should NOT have any files in the plugins folder, only symbolic links. I installed the plugins systemwide, so my ~/.mozilla/plugins folder is empty.[/QUOTE]
Everything has the right settings. Even have the newest stuff from the repositories (Backports).

However, I did notice something. After booting, if I start Azureus first and then run Firefox later, my Java works. If I run Firefox first, and then try to run Azureus, Java hangs. I'm not sure what causes this... any ideas?

---

### Post by kiwibird on 2005-06-19
I've got a similar problem here (same as certain ones here, but there seems to be a multitude of problems with Java on this thread..)

I've got jdk1.5.0_03 installed fine, put it in /usr/lib and symlinked java and javac from /usr/bin, my ~/.mozilla directory has no plugins, i just symlinked in /usr/lib/mozilla-firefox/plugins so it looks like this:
```
kiwibird@kiwishiba:/usr/lib/mozilla-firefox/plugins$ ls -la
totalt 12
drwxr-xr-x   2 root root 4096 2005-06-19 14:35 .
drwxr-xr-x  11 root root 4096 2005-06-19 14:40 ..
lrwxrwxrwx   1 root root   37 2005-04-17 18:26 flashplayer.xpt -> ../../mozilla/plugins/flashplayer.xpt
lrwxrwxrwx   1 root root   39 2005-04-17 18:26 libflashplayer.so -> ../../mozilla/plugins/libflashplayer.so
lrwxrwxrwx   1 root root   61 2005-06-19 14:35 libjavaplugin_oji.so -> /usr/lib/jdk1.5.0_03/jre/plugin/i386/ns7/libjavaplugin_oji.so
lrwxrwxrwx   1 root root   35 2005-06-18 17:42 mozplugger.so -> ../../mozilla/plugins/mozplugger.so
lrwxrwxrwx   1 root root   40 2005-06-18 17:26 nphelix.so -> /usr/local/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx   1 root root   41 2005-06-18 17:26 nphelix.xpt -> /usr/local/RealPlayer/mozilla/nphelix.xpt
```

I go into firefox and look at about: plugins, and it tells me I have Java, same as the previous poster here who pasted from about: plugins. And, same as the previous poster, it does not seem to connect any suffixes to the plugin. If I look into preferences-download-plugins, it tells me CLASS files are of type CLASS-file (duh), but there's no mention of .jnlp or anything more Java-related. When I look at [http://java.sun.com/applets/other/TumblingDuke/index.html](http://java.sun.com/applets/other/TumblingDuke/index.html) I get a blank area where Opera (which I've given the libjavaplugin_oji.so-folder in preferences) shows a tumbling duke (a .class-file). Running firefox as root gives me the tumbling duke, though, and when I removed the prefs.js file in my user folder, .class-files ran. (But then I couldn't get my extensions back when I put the old prefs.js-file there again :-? )

None of the browsers will start .jnlp-files though. Anyone got any tips for those?

---

### Post by jarrett.wold on 2005-06-19
I guess Web Start (jnlp) is separate [http://java.sun.com/products/javawebstart/download.jsp](http://java.sun.com/products/javawebstart/download.jsp)

---

### Post by pguerrer on 2006-08-31
This solved my problem as well.

> **fng said:**
> It works
although the directory of the .so file wasn't the 1 in the example
Mine was located here :
```
$ sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so
```

I installed j2re using the backports repo's

However, for the JRE 1.4.2_05-b04 that I had installed, the .so file was in:

... jre/plugin/i386/ns610-gcc32/libjavaplugin_oji.so

---

