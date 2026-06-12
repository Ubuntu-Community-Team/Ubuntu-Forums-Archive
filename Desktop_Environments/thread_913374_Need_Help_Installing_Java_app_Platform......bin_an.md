---
title: "Need Help Installing Java_app_Platform......bin and..."
date: 2008-09-07
forum: Desktop Environments
---

### Post by brian77095 on 2008-09-07
hi,

Not sure if this should be posted here but, that just shows how new I am at this.

I downloaded this form sun and, would like to install it on my Ubuntu HH system.

java_app_platform_sdk-5_05-linux.bin

I have searched for help but have not found anything I could use...

I also need or would like to intall this form NetBeans.

netbeans-6.1-ml-linux.sh

If it helps I have both files on my desktop and need to go form there...

Thanks for your help!!

---

### Post by brian77095 on 2008-09-07
I found this...

[https://jdk-distros.dev.java.net/ubuntu-dev.html](https://jdk-distros.dev.java.net/ubuntu-dev.html)

and it shows how to download and intall an older version of Java but, not how to install something I DLed.

---

### Post by pytheas22 on 2008-09-07
You don't need to go to so much trouble to install these applications.  You can install them easily using apt-get.

First, go to System>Administration>Software Sources and make sure that all of the boxes are checked under the "Ubuntu Software" tab.  Then run:
```

sudo apt-get install java-sdk netbeans
```

The versions of netbeans and Sun Java that you get might be slightly older than the ones available from their sites, but they're much easier to install, and for various reasons it's better to use the repositories (apt-get or Synaptic) to install them.

If for some reason you do need a higher version, please post links to the two installers (netbeans and java) that you downloaded so that we can take a look at the installation instructions.

---

### Post by coden4fun on 2008-09-07
go to your terminal and type in the following

> 
sh java_app_platform_sdk-5_05-linux.bin


if it's downloaded at the desktop which I believe is default you'll first have to change directory to the desktop which can be achieved by the following command.

> 
cd Desktop


netbeans-6.1-ml-linux.sh 

is similar except for a little tweak.

> 
# ./netbeans-6.1-ml-linux.sh  



after wards type in 

> 
sh java_app_platform_sdk-5_05-linux.bin


Doing this in order should give you a terminal of document agreements hitting enter continuously until you get a y/n agreement for the java sdk then you can hit y, then follow the wizard and it'll install the latest Java SDK on your disk.

If you need help just let me know.

---

### Post by guocangz@hotmail.com on 2008-11-22
Hi,

When I run 'sh java_app_platform_sdk-5_06-linux-ml.bin' I go the following error:

java_app_platform_sdk-5_06-linux-ml.bin: 1: Syntax error: "(" unexpected


Please help me. I am new to Linux.

Thanks.

Mike

---

### Post by pytheas22 on 2008-11-23
guocangz: you should be able to get what you need installed simply by typing:

```
sudo apt-get install java-sdk netbeans
```

If that doesn't work or you want to use the alternative method, try cd'ing into the directory where the file 'java_app_platform_sdk-5_05-linux.bin' is located (i.e. if that file is on your desktop, type 'cd ~/Desktop'), then run these commands:
```

chmod +x java_app_platform_sdk-5_05-linux.bin
./java_app_platform_sdk-5_05-linux.bin
```

This should work; if not, please let us know.

---

### Post by guocangz@hotmail.com on 2008-11-23
Thank you.

I had the netbeans installed already.

1. Here is the output after I ran 'apt-get install java-sdk netbeans':

ike@maolong:~/dowloads$ sudo apt-get install java-sdk netbeans
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package java-sdk is a virtual package provided by:
  sun-java6-jdk 6-10-0ubuntu2
  sun-java5-jdk 1.5.0-16-3
  cacao-oj6-jdk 6b12-0ubuntu5
  openjdk-6-jdk 6b12-0ubuntu6
  java-gcj-compat-dev 1.0.78-2
  default-jdk 1.6-30ubuntu3
You should explicitly select one to install.
E: Package java-sdk has no installation candidate

2. Here is the output after I ran ./java_app_platform_sdk-5_06-linux.bin:
 
./java_app_platform_sdk-5_06-linux.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory.

I have to make the sdk work as I need to install  SunStudio12.

Mike

---

### Post by pytheas22 on 2008-11-23
Sorry, I didn't realize that java-jdk wasn't a real package.  As the error message indicates, though, you could install a jdk by choosing one of those packages explicitly (probably one of the ones from Sun would be best), for example:
```

sudo apt-get install sun-java6-jdk 6-10-0ubuntu2
```

should work.

You may also want to take a look at [these instructions]("http://ubuntuforums.org/showthread.php?t=554514"), which are a bit old but should still work.

Let us know if this doesn't work.

---

### Post by guocangz@hotmail.com on 2008-11-23
I got the newest java installed already.

When I tied to install SunStudio12, java crashed with an error saying:
the package 'sun-java6-jre 6-10-0ubuntu2' failed to install or upgrade.

I then tried to prepare the system using the downloaded script: prepare_system. Here is the output:

sudo ./prepare_system -s java
error: Failed dependencies:
	glibc >= 2.1.2-11 is needed by jdk-1.5.0_09-fcs.i586
	sh-utils >= 2.0-1 is needed by jdk-1.5.0_09-fcs.i586
	fileutils >= 4.0-8 is needed by jdk-1.5.0_09-fcs.i586
	gawk >= 3.0.4-1 is needed by jdk-1.5.0_09-fcs.i586
	textutils >= 2.0-2 is needed by jdk-1.5.0_09-fcs.i586
	/bin/sh is needed by jdk-1.5.0_09-fcs.i586


There are some exceptions in running the SunStudio12 like the following:
Cannot run program "/bin/rpm": java.io.IOException: error=2, No such file or directory

Can you tell me how to get those packages installed or something else to prepare the system?

Thanks,

Mike.

---

### Post by pytheas22 on 2008-11-23
Sorry it's still not working.  I'm reading however that the ./prepare_system script won't work on Ubuntu (according to [this page]("https://answers.launchpad.net/ubuntu/+question/9540"), second-to-last post), so I wouldn't worry about what the script says.  If you're running modern Ubuntu, you should have all of those dependencies by default.

The error about '/bin/rpm": java.io.IOException: error=2' seems to be similarly related to the application not knowing that you're on Ubuntu.  It's looking for the program 'rpm', which only exists on Red Hat-based systems, not Debians like Ubuntu.

Did you install the sun-java6-jre or sun-java6-jdk package?  From what I'm reading, the latter (the jdk one) is the one that you need to run SunStudio.

You might also want to take a look at [this post]("http://ooblogger.blogspot.com/2007/04/how-tos-installing-sun-studio-11-on.html"), which gives instructions for installing SS 11; presumably SS 12 would be quite similar.

Please let me know if this still doesn't work.

---

### Post by guocangz@hotmail.com on 2008-11-24
Hi,

I installed Java5 and the SS setup is still not working, causing some exception errors in the out put, and the wizards do goes through but no files installed. 

Should start over?


Thanks,

Mike

---

### Post by pytheas22 on 2008-11-24
You could try googling the exceptions you're getting and see if it leads to answers...they may be resolvable, and some of them may not actually be a problem.

Also, if the wizard complete successfully, are you positive that it's not really installing anything?  You could use the 'locate' command to check; e.g.:
```

locate -i sunstudio
```

would return all files with 'sunstudio' (upper or lowercase) in their name...are any of these files getting copied into system directories?

If you still can't get it, then reinstalling, as you suggest, may be your best bet.  Then you could follow one of the installation guides on a clean system.

---

