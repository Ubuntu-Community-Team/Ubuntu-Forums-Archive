---
title: "Some major issues, help needed!"
date: 2009-02-02
forum: General Help
---

### Post by hork1 on 2009-02-02
Ok so my major issues are that I am using Ubuntu version 6.1, I have tried twice to make a newer disk (8.04) and they do not work.

The other issues are that I cannot upgrade the version, also I cannot find or install anything from the repositories or any third parties. When I click on upgrade it gives an authentication failed error. 

The only thing that I really need is the Java Runtime Environment.

I have tried downloading and tried installing JRE over and over but no luck. I have been using this OS for nearly a year with no problems and was able to get Java easily before, until my HD was totally full and I could not log in.

Any help getting the Java Runtime Environment installed or accessing sources to do so would be greatly appreciated.

---

### Post by zvacet on 2009-02-02
Ubuntu 6.1 is not supported anymore,and you can not upgrade to the next version because it is unsupported too.Read [this.]("https://help.ubuntu.com/community/UpgradeNotes").That is why you can not update anything anymore.What kind of problem did you have trying to install Hardy?If you can be more specific on that maybe somebody can help you with install.

---

### Post by taurus on 2009-02-02
1.  When you said 8.04 doesn't work?  You mean it doesn't boot?

2.  You are using a old and expired release so you need to adjust your /etc/apt/sources.list to reflect the changes.

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

3.  How did you install jre?

4.  If your harddrive is full, you need to clean out the cache and empty your recycling/trash bin.

```
sudo apt-get clean
sudo apt-get autoremove
df -h
```

---

### Post by hork1 on 2009-02-02
Thanks for the fast reply. I had figured it was no longer supported but wondered if I could still somehow install the JRE, I was able to install a plugin for videos without a problem. 


My problems with the disks I have made were they do nothing beyond the main screen. No option will work aside from booting from the hard drive. It will not run live or install so it very well could be that the disk has a problem or this computer does not have the guts to run it. It is a bare bones system with a very small hard drive.

---

### Post by hork1 on 2009-02-02
My hard drive was full and it prevented me from logging on so I did a fresh install of edgy. I will be sure to keep it clean in the future.

I tried burning a 8.04 disk twice with no luck, it will not boot at all. 

I am not able to install the JRE, that is my only issue really because I just use this computer for the internet. I was able to install a plugin for video but not the JRE.

If there is a way to adjust the sources list to point at a working source that would solve my problems. I had this same problem before but I got the JRE to install somehow after downloading it, the simple instructions on the site no longer work though.

---

### Post by taurus on 2009-02-02
How did you install jre on your machine?  

Did you download the one from Sun's, then moved it to someplace and unpacked it?

---

### Post by hork1 on 2009-02-02
I dont think I was able to move it, that could be where I am doing something wrong. I tried downloading it from there and followed their instructions but could not get it to work.

---

### Post by taurus on 2009-02-02
This is getting nowhere.  I am trying to help you but you kept saying that it didn't work.

What have you done so far?

What is the name of the file and where it is right now?

What instruction (site) did you follow?

---

### Post by hork1 on 2009-02-02
I have a fresh install and cannot get the Java Runtime Environment to install. These are the files I have tried, and what I believe worked before.

[http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com](http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com)

---

### Post by taurus on 2009-02-02
Which version did you download, RPM or self-extracting file?  Can you post the complete name of the file that you've downloaded?

---

### Post by hork1 on 2009-02-02
I have so far tried downloading both of the top files on that site and following their instructions, both have been deleted. I was only able to download them to my desktop, that could be where my error lies..


I also tried various commands on here in the help areas that were relevant with no luck.

I am terribly sorry for how little I know about using this OS, thanks for trying to help.

---

### Post by taurus on 2009-02-02
If you haven't done so (or deleted it), go back to the link and download the self-extracting file (the second link), jre-6u11-linux-i586.bin.  Once it's done, open a terminal and do

```
cd ~/Desktop
chmod a+x jre-6u11-linux-i586.bin
sudo mv jre-6u11-linux-i586.bin /opt
cd /opt
sudo ./jre-6u11-linux-i586.bin
sudo ln -s /opt/jre1.6.0_11/bin/java /usr/bin/java
```
Log out and back in again.  Then see what is the output from this command from a terminal?

```
java -version
```

p.s.  Run one line/command at a time.

---

### Post by hork1 on 2009-02-02
That installed it, the return from the command was.

java version "1.4.2"

It still doesnt work or show I have anything on the java site though.

---

### Post by taurus on 2009-02-02
What's the output of this command from a terminal?

```
which java
```
You are now talking about the plugin.

---

### Post by hork1 on 2009-02-02
That one says...

/usr/bin/java

---

### Post by taurus on 2009-02-02
Can you post these?

```
/usr/bin/java -version
ls -la /usr/bin/java
```

---

### Post by hork1 on 2009-02-02
1. java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)

Copyright (C) 2006 Free Software Foundation, Inc.


2. lrwxrwxrwx 1 root root 22 2009-02-01 14:35 /usr/bin/java -> /etc/alternatives/java

---

### Post by taurus on 2009-02-02
Remove the link to that version and create a new one, pointing to the one you have installed.

```
sudo rm /usr/bin/java
sudo ln -s /opt/jre1.6.0_11/bin/java /usr/bin/java
ls -la /usr/bin/java
java -version
```

---

### Post by hork1 on 2009-02-02
It says its correct, but still not working for some reason. Says I am missing the JRE when I try to test it.

java version "1.6.0_11"
Java(TM) SE Runtime Environment (build 1.6.0_11-b03)
Java HotSpot(TM) Client VM (build 11.0-b16, mixed mode, sharing)

---

### Post by taurus on 2009-02-02
What you are missing right now is the plugin.

What's the output of this command?

```
ls -la /usr/lib/mozilla
```

---

### Post by hork1 on 2009-02-02
total 32
drwxr-xr-x   3 root root  4096 2006-10-25 08:30 .
drwxr-xr-x 130 root root 24576 2009-02-01 15:19 ..
drwxr-xr-x   2 root root  4096 2006-10-25 08:30 plugins

---

### Post by taurus on 2009-02-02
Now link the java plugin too.

```
cd /usr/lib/mozilla/plugins
sudo ln -s /opt/jre1.6.0_11/plugin/i386/ns7/libjavaplugin_oji.so .
ls -la
```
You should see libjavaplugin_oji.so is pointing to /opt/jre1.6.0_11/plugin/i386/ns7/libjavaplugin_oji.so from the output of the last command.  

Now, you have to restart firefox.

---

### Post by hork1 on 2009-02-02
That did alot and the line was as you said, still nothing on the java test page though.

---

### Post by taurus on 2009-02-02
Which test site did you use?  In the address field of firefox, type

```
about:plugins
```
and see if java plugin 1.6 is on the list.

---

### Post by hork1 on 2009-02-02
I do not see java on the list, I was using the java website.

I dont understand how I can still have nothing for java installed?

---

### Post by taurus on 2009-02-02
What's the output of this command?

```
ls -la /usr/lib/mozilla/plugins
```

p.s.  Since you installed java by hand, you have to link everything by hand.  If you don't want to do all of those by hand, then you should have installed java from the repos since it will do everything for you.

---

### Post by hork1 on 2009-02-02
total 8
drwxr-xr-x 2 root root 4096 2009-02-02 14:10 .
drwxr-xr-x 3 root root 4096 2006-10-25 08:30 ..
lrwxrwxrwx 1 root root   53 2009-02-02 14:02 libjavaplugin_oji.so -> /opt/jre1.6.0_11/plugin/i386/ns7/libjavaplugin_oji.so
lrwxrwxrwx 1 root root   54 2009-02-02 14:10 libjavaplugin_oji.so. -> /opt/jre1.6.0_11/plugin/i386/ns7/libjavaplugin_oji.so.
lrwxrwxrwx 1 root root   36 2009-02-01 14:39 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root   37 2009-02-01 14:39 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root   38 2009-02-01 14:39 libtotem-complex-plugin.so -> ../../totem/libtotem-complex-plugin.so
lrwxrwxrwx 1 root root   39 2009-02-01 14:39 libtotem-complex-plugin.xpt -> ../../totem/libtotem-complex-plugin.xpt
lrwxrwxrwx 1 root root   34 2009-02-01 14:39 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   35 2009-02-01 14:39 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root   36 2009-02-01 14:39 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   37 2009-02-01 14:39 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root   42 2009-02-01 14:39 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root   43 2009-02-01 14:39 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt




Some are highlighted in colors.  54 2009-02-02 14:10 libjavaplugin_oji.so. is in a black box with red writing, is that an error or something?

---

### Post by taurus on 2009-02-02
That is an error alright.  Remove it.

```
sudo rm /usr/lib/mozilla/plugins/libjavaplugin_oji.so.
```
Be careful.  Remove the one with the . (dot) at the end.

Then, post the output of this command.

```
ls -la /opt/jre1.6.0_11/plugin/i386/ns7
```

---

### Post by hork1 on 2009-02-02
rm: cannot remove `libjavaplugin_oji.so.': No such file or directory

---

### Post by hork1 on 2009-02-02
total 148
drwxr-xr-x 2 root root   4096 2008-11-10 05:41 .
drwxr-xr-x 4 root root   4096 2008-11-10 05:41 ..
-rwxr-xr-x 1 root root 137021 2008-11-10 03:59 libjavaplugin_oji.so

---

### Post by hork1 on 2009-02-02
Do I need to put in that whole line to remove it?

---

### Post by taurus on 2009-02-02
It depends what directory you currently are.  If you already in /usr/lib/mozilla/plugins, then you don't have to include the whole path.  But if you are somewhere else, then you need to type in the whole path or else you would get that error message about file not found.

```
cd /usr/lib/mozilla/plugins
sudo rm libjavaplugin_oji.so.
ls -la
```

---

### Post by hork1 on 2009-02-02
Hmm I get the same error, this is what ls -la says,, first one is in green rest are blue.


total 8
drwxr-xr-x 2 root root 4096 2009-02-02 14:45 .
drwxr-xr-x 3 root root 4096 2006-10-25 08:30 ..
lrwxrwxrwx 1 root root   53 2009-02-02 14:02 libjavaplugin_oji.so -> /opt/jre1.6.0_11/plugin/i386/ns7/libjavaplugin_oji.so
lrwxrwxrwx 1 root root   36 2009-02-01 14:39 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root   37 2009-02-01 14:39 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root   38 2009-02-01 14:39 libtotem-complex-plugin.so -> ../../totem/libtotem-complex-plugin.so
lrwxrwxrwx 1 root root   39 2009-02-01 14:39 libtotem-complex-plugin.xpt -> ../../totem/libtotem-complex-plugin.xpt
lrwxrwxrwx 1 root root   34 2009-02-01 14:39 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   35 2009-02-01 14:39 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root   36 2009-02-01 14:39 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   37 2009-02-01 14:39 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root   42 2009-02-01 14:39 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root   43 2009-02-01 14:39 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt

---

### Post by taurus on 2009-02-02
Maybe reboot your machine.

---

### Post by hork1 on 2009-02-02
Still nothing, I dont know whats the story.

---

### Post by taurus on 2009-02-02
Which version of firefox are you using?  What's the output of this command from a terminal?

```
cd ~/.mozilla
```

---

