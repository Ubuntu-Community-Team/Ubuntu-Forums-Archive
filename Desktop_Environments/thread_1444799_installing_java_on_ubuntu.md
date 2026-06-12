---
title: "installing java on ubuntu"
date: 2010-04-01
forum: Desktop Environments
---

### Post by rongo on 2010-04-01
I new and I try to discover Ubuntu.

I would like to install Java JRE on my Ubuntu software. Via Mozilla firefox I went to [www.java.com]("http://www.java.com"), I have downloaded a bin file JRE-6u19-linux-i586.bin(name of the file). In the installation instructions I found  the command to begin the install.
I do a cd /home/roland/Downloads
I execute the command chmod a+x jre-6u19-linux-i586.bin when I press the ENTER key I receive de message file or  path not found.
Can somebody guide me.

---

### Post by mgmiller on 2010-04-01
Don't do it that way.  That's how you do it in Windows and Linux is not Windows.
The file you have downloaded is a Linux installer, but is mainly meant for Linux distros that don't have good or up to date package management systems like Debian based distros such as Ubuntu.

As a noobie, you are much better off sticking with installing anything you want from within the Ubuntu package management system.  It will automatically stay up to date with security updates along with the rest of your system this way, and has been tested to work correctly with your version of Ubuntu (theoretically).

For a gui approach, open:
 System > Administration > Synaptic Package manager

When it asks for your password, give it your regular log on password.

Click the search icon at the top and search for sun-java

When the list appears, tick off the ones you want and then click the green Apply check mark at the top.

The ones I usually install are sun-java6-bin and sun-java6-jre  You could also take the fonts and the plugin if you want to.


If you want to do this from command line:

Open a terminal:
 Applications > Accessories > Terminal

copy and past the following and hit enter:

```
sudo apt-get install sun-java6-jre
```When it asks for a password, give it your regular log on password and hit enter again.  Note you will not see it echoed to the screen.

When done, repeat for others you want.

There is also a way to string all of them together in one apt-get command, but try them one at a time to start.


Note, when installing the sun-java packages, you will have to agree to the Sun Microsystems Eula.  No biggie, just an extra step.


Finally, I believe all this has been open sourced and is part of the standard java install in Lucid.

---

### Post by doas777 on 2010-04-01
usually, after installing sun java, you need to tell ubuntu to use it by default with a line like this:
```
sudo update-java-alternatives -s java-6-sun
```here is some good info about sun java on ubuntu:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by ottabaub on 2010-04-02
Actually, using Synaptic doesn't install the latest Java release. The repositories haven't been updated. I'm running Ubuntu 9.10 and Firefox 3.6.2. I can install Sun Java using Synaptic but the Java plugin for Firefox isn't installed. Apparently since Firefox 3.6 the method of introduction of the Java plugin has changed. 

I went to the Java site and downloaded the latest Java version jre-6u19-linux-i586-rpm.bin. Using the instructions at the Java site I unpackaged the bin to jre-6u19-linux-i586.rpm. Then I installed Alien using Synaptic Pkg Mgr to convert the .rpm to a .deb. When I ran it, this is what I got:

$ sudo alien -k jre-6u19-linux-i586.rpm

error: incorrect format: unknown tag
Warning: Skipping conversion of scripts in package jre: postinst postrm prerm
Warning: Use the --scripts parameter to include the scripts.
chown: cannot access `jre-1.6.0_19//usr/java/jre1.6.0_19/lib/charsets.jar': No such file or directory
failed chowning /usr/java/jre1.6.0_19/lib/charsets.jar to 0:0: Illegal seek at /usr/share/perl5/Alien/Package/Rpm.pm line 265, <GETPERMS> line 38.

So my quest for the java plugin in Firefox 3.6.2 remains unfulfilled. And my feeling that linux is still untamed and way more frustrating to use than Windows remains as true as it was 5 years ago.

I've searched the forums and, so far, not one has the solution. This isn't the first time I've found the repositories behind in their support. Who's responsible? Why isn't the most recent version of java available to us?

---

### Post by tripolitan on 2010-04-11
Have you found a way to run java in firefox 3.6?

---

### Post by HegonBadde on 2010-04-11
> **rongo said:**
> I new and I try to discover Ubuntu.
...
I execute the command chmod a+x jre-6u19-linux-i586.bin when I press the ENTER key I receive de message file or  path not found.
Can somebody guide me.

that's because your proboably sudo su.
which means . isn't on your path.

would would want to change it to 
#>chmod a+x ./jre-6u19-linux-i586.bin

you might not be in right directory, you might be in ~/Desktop but you changed downloads to the ~/Downloads Directory.

try 
#>ls -ln ./jre<tab>
and see if it pops up in the list.

And you might be a good user and didnt sudo su.

then you would want to change it to
~>sudo chmod a+x ./jre-6u19-linux-i586.bin

* Safety Message*
You would want to perform the chown with sudo because it's own by another user and you don't have any rights to it.
so you need root to let you update it.

Don't run the bin as sudo either. you want to trick the jvm into a user only mode.
Then add it to you paths as desired.
Ubuntu doesn't like it when mess with default java, and sometimes fight hard to change it back.

If you absolutely must install java and control it's environment, installing under a user account is best.
If you must have the java envrionment to work with the System, grab ubuntu-restricted-extras instead.

---

### Post by QIII on 2010-04-11
Hold the boat, folks.

Far and away the easiest method is to use this guy's instructions:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

It is clean, easy and gives you the option to completely remove Java by simply deleting a directory.  You also know exactly where it is being installed.

The repositories are not "behind".  Canonical has decided to support OpenJDK, which is the open source version of Java.  This is in keeping with Canonical's goal of providing only open source applications and software.  You will find the most recent OpenJDK in the repositories.

---

### Post by tripolitan on 2010-04-16
Why didn't they just tell us to remove old jpackage, install new one and sym link libnpjp2.so instead of libjavaplugin_oji.so???
thats all I had to do yesterday and viola, JAVA works!

---

### Post by micio on 2010-04-16
For Ubuntu 10.04
If you have previously installed openjdk remove it by

```
sudo apt-get remove openjdk-6-jre
sudo apt-get autoremove
```  

then

```
sudo add-apt-repository ppa:yofel/off-ppa && sudo apt-get update &&  sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin
```

---

### Post by tripolitan on 2010-04-17
...tried all that, it does not work for the downloaded version of Firefox 3.6.3 and for other programs that require/utilize Java at the same time. I only wanted one version of Java that can be used by all packages that use Java.

---

### Post by shaka_zulu on 2010-04-17
I am trying to understand if you are looking for java plug in for Firefox or Java package which you can install from repository?

---

### Post by tripolitan on 2010-04-18
I (and many others) were trying to find a way to make java plugin work with Firefox 3.6.3 the package from the repository only works with 3.5.X. As I mentioned, my problem was solved once I found out that the file name for the plugin has changed, made a new symlink ...

---

### Post by Andre-D on 2010-04-21
the easiest way is to install "sudo apt-get remove openjdk-6-jre"  - but it's not available from the default repository (why?)

I know that adding 
adding this repository fixes it:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

---

### Post by tripolitan on 2010-04-21
sudo apt-get anything does not do it for the plugin, under the conditions I mentioned.

---

### Post by CivilizationII on 2012-02-17
the best is to code 

sudo apt-get install sun-java6-jre

Firefox plugin is then automatically installed

---

### Post by jcoles on 2012-02-17
> **CivilizationII said:**
> the best is to code 

sudo apt-get install sun-java6-jre

Firefox plugin is then automatically installed

> sudo apt-get install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jre' has no installation candidate


Something's missing. Can you tell me the exact repository entry I need?

The binary package from Oracle doesn't work either. 

How do I install the basic standard Java runtime? 
Searching in Synaptic for 'java' is just confusing! 
> $ java
The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless

What do I need?
Why is this so difficult? Java should be a built-in no-brainer.

---

### Post by QIII on 2012-02-17
Java is no longer licensed by Oracle to be in the Ubuntu repositories.  

What you will find, if you can, is out-dated and dangerously unsafe.

I know this thread is two years old, but please look back at my earlier post and use this guide:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

