---
title: "java plugin firefox"
date: 2005-07-04
forum: Desktop Environments
---

### Post by aspak on 2005-07-04
I'm looking for a java plugin that works for mozilla firefox, but can't seem to find any with apt. Tried sun-j2rel.5 but no luck. I also tried to install gcjwebplugin, but that crashes firefox.
I'm running firefox 1.0.4.

Any ideas?

---

### Post by Martin Witte on 2005-07-04
[http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre) tells it

---

### Post by aspak on 2005-07-04
Well, I've tried to find sun-j2rel with apt, but it doesn't find it. I think I have all the needed repositories.
Any suggestions?

---

### Post by LeTon on 2005-07-04
Hi ,Aspak

I'm totally with you , I have the same problem!
Starters guide is not helping  to install Java plugin....
Please, experts,someone...Otherwise I have to go back to may windows box to read e-mails.

---

### Post by rider343 on 2005-07-04
sudo apt-get install sun-j2re1.5

---

### Post by GoldBuggie on 2005-07-04
To be able to do "sudo apt-get install sun-j2re1.5" you need to add the backports that is explained in the "How to add extra repositories?" section.

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by aspak on 2005-07-04
I have the backports repositories, in fact I have all the recommended repositories in that guide, but I still cannot find sun-j2rel.5

I really need to get a java plugin to work asap so any help is appreciated...

---

### Post by GoldBuggie on 2005-07-04
Go and get it directly from the repository then

go here: "http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/"

download the correct .deb file and use do "sudo alien -i <name of .deb file>". Then you have it installed. But it sure does sound strange that you can't find it. (you have done a update and searched for something simple as "sun" in synaptic i hope)

---

### Post by f1dave on 2005-07-05
Hi, thought my experiences with installing the SDK recently may help- not for a firefox plugin perhaps, but certainly for those installing the SDK.

Basically, download the non-rpm file from java.sun, then run it with sh install-java-blah, and answer questions and watch it create a folder. Note: if you dont want an sdk folder sitting in your home dir, make sure it's in usr/share or something. I'm just lazy.

Now, after install running java -version in your shell will make it say "dude, i don't know that command" or something more uncool. So, the way to fix this- and the step most often asked- is this:

1. Go to console and sudo nano (or your editor) ~/.bash_profile
2. Go down to the bottom and add these lines, changing to suit your directory as required:

PATH=/home/meacod01/jdk1.5.0_04/bin:$PATH:$HOME/bin:./
export PATH
export JAVA_HOME=/home/meacod01/jdk1.5.0_04
export CLASSPATH=/home/meacod01/jdk1.5.0_04/lib/tools.jar:/home/meacod01/jdk1.5.0_04/jre/lib/rt.jar:./

Then reboot or refresh your bash (using source) and yeah, it should work. Type java -version to test it.

---

### Post by dc2447 on 2005-07-05
The way I did it was

1: Went to[ sun and downloaded java](http://java.sun.com/j2se/1.5.0/download.jsp)
2: Unpacked it somewhere logical (/opt/ for me)
3: The cd into my ~/.mozilla/plugins directory and linked to the shaed object
ln -s /opt/jdk1.5.0_04/jre/plugin/i386/ns7/libjavaplugin_oji.so

Easy

---

### Post by improverrr on 2005-07-06
I went to the JRE website and downloaded JRE 5 and downloaded the update 4 BIN file (not the RPM file):

[http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp)

created a folder for it ( i used /usr/lib/java) and put this bin file in it.

open console at this new folder location and did the following command (as root):
$ sudo su
$ password
$ chmod a+x javafilename.bin
$ ./javafilename.bin
opens to the user agreement.... scroll... say Yes and it unpacks...

Now in the console, change folder directory to the firefox plugins directory:  mine is /usr/lib/mozilla-firefox/plugins

$ sudo su (if not root already)
$ password
$ ln -s /usr/lib/java/jre1.5.0_04/plugin/i386/ns7/libjavaplugin_oji.so
(or wherever you installed it, but should be very similar)

Thats it, you can goto [www.dslreports.com](www.dslreports.com) and test it by running a speed test.  works great!

good luck!

---

### Post by bgstratt on 2005-07-07
aspak, are you using an "L" or a 1, cuz it should be a 1, like the number, your post has an "L" like the letter, your best bet in using the starter guide is to copy and paste, way easier than typing in each command, plus you can just hit the ";" button inbetween commands to do multiple commands at once if you want.  

Also make sure you follow the instructions all the way through, i.e. when you add the extra repositories, make sure to apt-get update.

---

### Post by Milky on 2005-10-01
[QUOTE=bgstratt]aspak, are you using an "L" or a 1, cuz it should be a 1, like the number, your post has an "L" like the letter, your best bet in using the starter guide is to copy and paste, way easier than typing in each command, plus you can just hit the ";" button inbetween commands to do multiple commands at once if you want.  
Also make sure you follow the instructions all the way through, i.e. when you add the extra repositories, make sure to apt-get update.[/QUOTE]
Although the Ubuntu starter guide is good, it doesn't solve every problem. After adding the repositories, w32codecs, sun-j2re1.5 and mozilla-acroread "can't be found". And most of the responses people are getting when asking how to get them is to follow that guide... which they most likely already did and later, after someone told them to go there, stated that they've been there already.

---

### Post by tseliot on 2005-10-01
[QUOTE=Milky]Although the Ubuntu starter guide is good, it doesn't solve every problem. After adding the repositories, w32codecs, sun-j2re1.5 and mozilla-acroread "can't be found". And most of the responses people are getting when asking how to get them is to follow that guide... which they most likely already did and later, after someone told them to go there, stated that they've been there already.[/QUOTE]
Actually it's an [COLOR="Red"]Unofficial[/COLOR] Ubuntu 5.04 Starter Guide and maybe it's not updated every day.

---

### Post by Brando569 on 2005-10-02
[QUOTE=improverrr]I went to the JRE website and downloaded JRE 5 and downloaded the update 4 BIN file (not the RPM file):
[http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp)
created a folder for it ( i used /usr/lib/java) and put this bin file in it.
open console at this new folder location and did the following command (as root):
$ sudo su
$ password
$ chmod a+x javafilename.bin
$ ./javafilename.bin
opens to the user agreement.... scroll... say Yes and it unpacks...
Now in the console, change folder directory to the firefox plugins directory:  mine is /usr/lib/mozilla-firefox/plugins
$ sudo su (if not root already)
$ password
$ ln -s /usr/lib/java/jre1.5.0_04/plugin/i386/ns7/libjavaplugin_oji.so
(or wherever you installed it, but should be very similar)
Thats it, you can goto [www.dslreports.com](www.dslreports.com) and test it by running a speed test.  works great!
good luck![/QUOTE]


this is the way to do it! i didnt realize at first i had to create the link, then i re-read the instructions

---

