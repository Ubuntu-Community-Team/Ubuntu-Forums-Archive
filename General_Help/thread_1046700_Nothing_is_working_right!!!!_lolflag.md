---
title: "Nothing is working right!!!! :lolflag:"
date: 2009-01-21
forum: General Help
---

### Post by Meohme3 on 2009-01-21
Okay, 1st of all I want to thank you for helping me if you do. Now, my Internet will randomly freeze then close when I try to go on certain websites, Including Yahoo, Runescape, Youtube, and Google. Secondly, I was trying to download a Java Sun Microsystem applet for Linux (my computer's running system) and I am lost.

---

### Post by Crafty Kisses on 2009-01-21
You really didn't give a lot of details but what Java application are you trying to install? When you say your Internet "freezes" do you mean it crashes? What are your system specs?

---

### Post by Meohme3 on 2009-01-21
I am using the system; xubuntu 6.06 and Firefox closes out randomly, I guess it crashes. I'm trying to get the free downloads off of Java that are specified for linux and I am having trouble installing them. Is there any way to do so without messing around with the terminal?

---

### Post by spcwingo on 2009-01-21
Java is available in the repositories.  It would be much easier installing from there instead of compiling from source (I'm sure that's what sun offers).

---

### Post by Crafty Kisses on 2009-01-21
You could check the repositories and see if the application you want is in Synaptic, Synaptic is click and install. If you're downloading directly off of Sun's website, you probably have to compile the application from source, which isn't too hard, just make sure you have the correct dependencies installed and what not. Here is a great link for more information on compiling software: [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

Now on to the Firefox problem, open up the Terminal while Firefox is running, and type the following:
```
top
```
Post the results back here at the forum, and I or someone else can help you further.

---

### Post by Meohme3 on 2009-01-21
Let me explain what happened. I went on the Runescape website and clicked 'Play Free Users'. A notice poped up on the screen stating I need Java Sun Microsystems applet. so I told it to download and IT SAID iT WASN'T AVAILABLE, AND TO INSTALL IT MANUALLY.

---

### Post by 2hot6ft2 on 2009-01-21
For Java and Flash open a terminal put this in and hit Enter

```
sudo apt-get install ubuntu-restricted-extras

```
Then your password and Enter (your password will not be displayed)

It will fix that as well as other missing multimedia you haven't found out about yet.

When it gets to the agreement hit Tab then Enter to accept the Java agreement.

---

### Post by Therion on 2009-01-21
> **Meohme3 said:**
> Is there any way to do so without messing around with the terminal?
Can you Copy and Paste ONE command into the Terminal without coming apart at the seams?  If so, try this one:

```
sudo apt-get install ubuntu-restricted-extras
```

Enter your password when prompted and you're good to go.

---

### Post by Meohme3 on 2009-01-21
I tried typing in top, now this looks like the task manager on Windows A little bit.

---

### Post by 2hot6ft2 on 2009-01-21
Applications>Accessories>Terminal

guess it's in the same place in xubuntu as ubuntu

---

### Post by Crafty Kisses on 2009-01-21
Yes, now copy and paste the results of "top" so I or someone else can take a look at it.

---

### Post by Meohme3 on 2009-01-21
The file is downloaded, not installed, so I just need to know how to install it, but it can't be to complicated can it?

---

### Post by Meohme3 on 2009-01-21
Here are the results of Top

top - 17:39:19 up  1:20,  2 users,  load average: 0.36, 0.75, 0.58
Tasks:  69 total,   3 running,  65 sleeping,   0 stopped,   1 zombie
Cpu(s): 14.0%us,  1.3%sy,  0.0%ni, 84.0%id,  0.0%wa,  0.3%hi,  0.3%si,  0.0%st
Mem:    255024k total,   161100k used,    93924k free,     2568k buffers
Swap:   433712k total,    17612k used,   416100k free,    51900k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3812 root      15   0  106m  23m 6712 R  7.6  9.2   5:54.48 Xorg               
 4549 matt      15   0 45280  13m 8340 R  7.6  5.3   0:02.67 xfce4-terminal     
 4610 matt      15   0  2248 1100  844 R  0.3  0.4   0:00.08 top                
    1 root      16   0  1628  540  448 S  0.0  0.2   0:01.87 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 events/0           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 khelper            
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kblockd/0          
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   11 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
   73 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  105 root      16   0     0    0    0 S  0.0  0.0   0:00.03 pdflush            
  106 root      15   0     0    0    0 S  0.0  0.0   0:00.27 kswapd0            
  107 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0

---

### Post by ugm6hr on 2009-01-21
I would suggest you start from the beginning.

1. What computer are you using (i.e. RAM, CPU)?

2. Why have you installed Xubuntu 6.06, which is nearing the end of its support period?

I suspect that you would have better luck if you tried Xubuntu 8.04.

EDIT: I see you have 256MB RAM.  This is enough for Xubuntu 8.04.

---

### Post by Meohme3 on 2009-01-21
I'm no computor wiz so I have no idea of any of my proporties, I use this computor for school work and gaming

---

### Post by ugm6hr on 2009-01-21
So who installed Xubuntu for you?

---

### Post by Meohme3 on 2009-01-21
My computor teacher, It was a computor he didn't use anymore, and he said it ran perfectly fine.

---

### Post by ugm6hr on 2009-01-21
He has installed an old version of Xubuntu for you.

Unfortunately, a lot of the "automatic" features are not present.

Could he install a newer version for you?  Or do you have a fast internet connection with about 1GB downloads to spare to upgrade it yourself?

---

### Post by Meohme3 on 2009-01-21
I don't know!!!!
Ive been on here for an hour!!!
I'm getting tired of all this computor language!!!
I just wanna know how to get my Java Plug in, please Mr. whoever you are.
I'm only going to use this computor for abiword and gaming.

---

### Post by Crafty Kisses on 2009-01-21
First that's no way to get help, yelling at people that are trying to help you, just saying. If you follow my instructions you might be able to play Runescape. First you need to go into Terminal** (Applications -> Accessories -> Terminal)** once you're in Terminal, run the following command:
```
sudo apt-get install sun-java6-plugin ; sudo update-java-alternatives -s java-6-sun
```
Once that's installed restart Firefox, and try again. I understand Linux can be frustrating but you must follow some of the instructions people on here are giving you. If you want to know how to install a later version of Xubuntu, here is a great link on how to do that, it's very simple: [http://developer.novell.com/wiki/index.php/HOWTO:_Install_Xubuntu](http://developer.novell.com/wiki/index.php/HOWTO:_Install_Xubuntu). As the above post stated, you may not have all the features of the newest version of Xubuntu, so you may want to think about upgrading, it's very simple.

---

### Post by archolman on 2009-01-21
[B]2hot6ft2;  
That  (install) code just sorted out some problems I was having with a couple of WebPages. Thankyou very much[/B]

---

### Post by Meohme3 on 2009-01-21
these are the results of the code codename gave me.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-plugin
sudo: update-java-alternatives: command not found

---

### Post by Meohme3 on 2009-01-21
I am sorry for the way I acted, I need help, I am only 13 and not very knowledgeable of this new Linux system.

---

### Post by Crafty Kisses on 2009-01-21
Then run the following command:
```
sudo apt-get update
```
Then try again, if that doesn't work you can always try:
```
sudo apt-get install ubuntu-restricted-extras
```
I'm not sure if that package works with Xubuntu, but I'm pretty sure it does.

---

### Post by Meohme3 on 2009-01-21
here is what my terminal screen has to say.....

---

### Post by Meohme3 on 2009-01-21
Sorry I forgot to copy.

matt@matt-desktop:~$ sudo apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
matt@matt-desktop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras
matt@matt-desktop:~

---

### Post by Crafty Kisses on 2009-01-21
I'm pretty sure since you're using 6.10, it's a little bit different, so try installing the following package:
```
sudo apt-get install sun-java5-bin
```

---

### Post by Meohme3 on 2009-01-21
these are my results, where am I going to get this file it ways I don't have?
The name of the bin file I have is: jre-6u11-linux-x64-rpm.bin and it is saved to my desktop, I don't know If this will help.

matt@matt-desktop:~$ sudo apt-get install sun-java5-bin
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java5-bin

---

### Post by Crafty Kisses on 2009-01-21
Here, try the following, download the latest version of java from [http://www.java.com/en/download/index.jsp](http://www.java.com/en/download/index.jsp). Once you have downloaded it, move it to the following directory:
```
/usr/lib/jvm
```
You can do that by running the following command:
```
sudo mv jre*version-number*.bin /usr/lib/jvm
```
I'm guessing you don't have a Java directory yet, so make a Java directory by doing the following:
```
sudo mkdir jvm
```
Make sure you change the directory to the following:
```
/usr/lib/jvm
```
You then need to make the file an executable, if you haven't done that already it's fairly simple, so run the following:
```
sudo chmod +x jre*version-number*.bin
```
Then once you have made the file an executable, you can finally run the .bin file via Terminal, and you can do that by running the following:
```
sudo ./jre*version-number*.bin
```
Make sure the symlink is removed in /etc/alternatives because if you don't remove it, there maybe some conflicts, so you can remove it by doing the following:
```
sudo rm /etc/alternatives/java
```
Then you have the option to create a new symlink, so you can create a new one by doing the following:
```
sudo ln -s /usr/lib/jvm/jre1.6.0_07/bin/java /etc/alternatives/java
```
Then after that, you need to make sure you're running the latest version of Java, so in other words to make sure the install went well and actually went through, depending on the Java version, you will get different results:
```
java -version
```
You should get some results similar to this:
```
java version "1.6.0_0"
```
Like I said, that will vary depending on what Java version you get. The last step, is you need to create a symlink to Firefox, this is pretty simple, if you already have one you don't really have to do it, but if you don't, you can make one by doing the following:
```
sudo ln -s /usr/lib/jvm/jre1.6.0_07/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox-3.0.1/plugins/libjavaplugin_oji.so
```
Remember that's all depending on your Java version, so substitute your own information / Java version. So if it's still not working, you may need to update your Java alternatives, to make sure your running the right version of Java, you can do that by doing the following:
```
sudo update-alternatives --config java
```

---

### Post by Meohme3 on 2009-01-21
The terminal once again says I have no such file.

---

### Post by Crafty Kisses on 2009-01-21
Make sure you downloaded this one: [http://javadl.sun.com/webapps/download/AutoDL?BundleId=26214](http://javadl.sun.com/webapps/download/AutoDL?BundleId=26214). You also need to make sure you make the file an executable because if you don't you're going to be getting errors, that's the main thing. You also need to make sure your moving it to the right directories and what not. So remember make the file an executable.

You can make the file an executable by doing the following, as I stated above:
```
chmod a+x jre-6u<version>-linux-i586.bin
```
Once you've done that you can run the .bin file and start installing it.

---

### Post by Meohme3 on 2009-01-21
It says I have no such file or directory exactly. I don't know about you but I think this computer is crazy!!! What do we have to do to get this information through it's thick, almost brainless hardrive?

---

### Post by Meohme3 on 2009-01-21
anybody there?!?!

---

### Post by Crafty Kisses on 2009-01-21
You're not typing in the correct directories, remember in Linux the directories are case sensitive, so assuming the the file is called java.bin, or something to that nature and the file is saved on your desktop, you need to do the following:
```
cd ~/Desktop
chmod +x java.bin
sudo mv java.bin /opt
cd /opt
sudo ./java.bin
```
Once you've done that it will start unzipping the files in the /opt directory, there should be a new directory, and not sure what it would be called, but navigate to it:
```
cd jre_directory/bin
sudo ln -s /opt/jre_directory/bin/java /usr/local/bin/java
```
There is indeed a plugin directory in there, so you need to put that in your ~/.mozilla/plugins directory, these are the same instructions my good friend Taurus gave you, if you follow that, it will work. You may also want to think about updating Xubuntu 6.10, to a later version, seeing as how there is no more support for Edgy to my knowledge. So here is a great link on how to upgrade Xubuntu, it's very simple and can be done in less than 45 minuets depending on your hardware: [http://developer.novell.com/wiki/index.php/HOWTO:_Install_Xubuntu](http://developer.novell.com/wiki/index.php/HOWTO:_Install_Xubuntu).

Remember to have at least 1GB of free space on the drive, at this point I can't really help you much further, the instructions above is how you install Java, I can't do it for you, not being rude, just stating facts. So I'm guessing once you install a newer version of Xubuntu, it will be easier for you to navigate packages, and you will definitely have a bigger selection.

---

### Post by Meohme3 on 2009-01-22
Java problem solved, now I need help with the firefox problem.

---

### Post by jamesstansell on 2009-01-25
Hi Meohme3,

You are running xubuntu 6.10, which is no longer supported, so you seriously need to upgrade.  I'm thinking 8.04 LTS might be a good choice for you.

Try to get in touch with the Wisconsin Loco; someone might be able to meet you to get the upgrade done.

[http://ubuntuforums.org/forumdisplay.php?f=263](http://ubuntuforums.org/forumdisplay.php?f=263)

Best regards,

-james.

---

### Post by Meohme3 on 2009-01-29
alright, i'm not running 6.10, i'm running 6.06. and I don't know how to get the upgrade.

---

### Post by ugm6hr on 2009-01-30
> **Meohme3 said:**
> alright, i'm not running 6.10, i'm running 6.06. and I don't know how to get the upgrade.

Your post #26 labels all repositories (online software collections for Ubuntu) as specific for "edgy" whih is 6.10.

The following may clarify:
```
sudo lsb_release -a
cat /etc/issue
uname -a
```

If you are genuinely running 6.06, then someone has manually edited your repository list, which is unhelpful.

If you have 6.06, you can upgrade directly to 8.04, although you have to fix your repository list first.  If you have 6.10, it would be easier to just wipe everything and re-install.  However, if you struggle with computers, it may be better to ask your teacher for help.

I asked earlier:
Do you have a fast internet connection?
Do you have a CD-writer?

Given you have 256MB RAM, your best option is to use the Xubuntu 8.04 Alternate CD to install, although the Live CD will work if you use the manual partitioning option and maintain your current swap partition.

---

### Post by Meohme3 on 2009-02-12
That said I was running 6.10.... so maybe I was wrong but my web browser start up screen said "welcome to 6.06" so I don't know.

---

### Post by ugm6hr on 2009-02-13
I suspect that your computer originally had 6.06, but has since been upgraded to 6.10.

I've completely forgotten what the problem was, but my last advice was to use 8.04, which still stands.

---

