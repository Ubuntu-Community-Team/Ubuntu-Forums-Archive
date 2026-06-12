---
title: "Java w/Firefox"
date: 2005-04-03
forum: Desktop Environments
---

### Post by plewisfdx on 2005-04-03
I searched, and found exactly my problem, except his solution didn't fix my problem.

I am running Hoary on a Dell Inspiron 2500 Laptop.  Firefox doesn't display the Java APPLETS, just blank space.

Java is installed.  "about:plugins" shows all functions enabled.  A java test shows the java version, so firefox knows where java is, and how to get it.

My windows computer runs java apps, so I know its not my firewall/router.

I can run desktop java apps.  

I have linked the java plugin to the correct directory.  "~/.mozilla/plugins/..."

Java is enabled on the preferences.

Any help getting java applets to load?   Like I said, I just get a blank space where the applets are supposed to be.

thanks

phil

---

### Post by Gandalf on 2005-04-03
[QUOTE=plewisfdx]I searched, and found exactly my problem, except his solution didn't fix my problem.

I am running Hoary on a Dell Inspiron 2500 Laptop.  Firefox doesn't display the Java APPLETS, just blank space.

Java is installed.  "about:plugins" shows all functions enabled.  A java test shows the java version, so firefox knows where java is, and how to get it.

My windows computer runs java apps, so I know its not my firewall/router.

I can run desktop java apps.  

I have linked the java plugin to the correct directory.  "~/.mozilla/plugins/..."

Java is enabled on the preferences.

Any help getting java applets to load?   Like I said, I just get a blank space where the applets are supposed to be.

thanks

phil[/QUOTE]
 where did you get the documentation to install??

---

### Post by plewisfdx on 2005-04-04
I installed jre1.5.0 from the java web site.  So I used the documentation from the website.  To get java to work on firefox, I used the mozilla documentation on their website.

I noticed after my post that there is a HOWTO for this. So I tried it.

1."first you need to download J2SDK or J2RE from http://www.blackdown.org/java-linux/java-linux-d2.html"
I did this, and the file I have is : jre1.4.2.xxx.bin .

2. "$ sudo apt-get install java-package"  
This results in a "Couldn't find package java-package" error.  I have the universe repository uncommented, should I uncomment the bug-fix ones??

3. "$ fakeroot make-jpkg j2sdk-1.4.2-01-linux-i586.bin"
"Fakeroot: command not found"

4. So I can't do this next step "you don't have to fill your mail and other info asked just press enter, when this finished you will find blackdown-j2sdk1.4_1.4.2+01_i386.deb in the same folder", because I don't have that file.

So blackdown is the REQUIRED java sdk or re, the one from the Sun website won't work on hoary?

Thanks for any help,

phil

---

### Post by Gandalf on 2005-04-04
[QUOTE=plewisfdx]I installed jre1.5.0 from the java web site.  So I used the documentation from the website.  To get java to work on firefox, I used the mozilla documentation on their website.

I noticed after my post that there is a HOWTO for this. So I tried it.

1."first you need to download J2SDK or J2RE from http://www.blackdown.org/java-linux/java-linux-d2.html"
I did this, and the file I have is : jre1.4.2.xxx.bin .

2. "$ sudo apt-get install java-package"  
This results in a "Couldn't find package java-package" error.  I have the universe repository uncommented, should I uncomment the bug-fix ones??

3. "$ fakeroot make-jpkg j2sdk-1.4.2-01-linux-i586.bin"
"Fakeroot: command not found"

4. So I can't do this next step "you don't have to fill your mail and other info asked just press enter, when this finished you will find blackdown-j2sdk1.4_1.4.2+01_i386.deb in the same folder", because I don't have that file.

So blackdown is the REQUIRED java sdk or re, the one from the Sun website won't work on hoary?

Thanks for any help,

phil[/QUOTE]
 well you have to run
fakeroot make-jpkg <<file name>>
where <<file name>> is the name of the file you have downloaded from blackdown.org site, and you must be in the same directory as this file is, for example firefox download by default to the user home so cd /home/user and ls to find out what's the files in here and then run that command

---

### Post by plewisfdx on 2005-04-05
See #3 you quoted from me in your post.

---

### Post by Gandalf on 2005-04-05
[QUOTE=plewisfdx]See #3 you quoted from me in your post.[/QUOTE]
 did you sudo apt-get install fakeroot (it seems that i forgot to include that in the howto i will edit it

//EDIT: yea i forgot to include that in the TUTO, i'm sorry just sudo apt-get install fakeroot will solve the problem, sorry again :$

---

### Post by plewisfdx on 2005-04-05
I installed fakeroot, now I get an error:
  "/usr/bin/fakeroot: line 150: make-jpkg:command not found"

I downloaded j2re-1.4.2-01-linux-i586.bin from the blackdown site, and I am in the correct directory.

As I said before, I have java 5 (1.5.0) from the java site working on the computer, and, yesterday I installed Opera to test my java on that browser, and it will run java applets with my 1.5.0 directory plug-in.

Any idea why Firefox will not?  

thanks,
phil

---

### Post by Gandalf on 2005-04-05
[QUOTE=plewisfdx]I installed fakeroot, now I get an error:
  "/usr/bin/fakeroot: line 150: make-jpkg:command not found"

I downloaded j2re-1.4.2-01-linux-i586.bin from the blackdown site, and I am in the correct directory.

As I said before, I have java 5 (1.5.0) from the java site working on the computer, and, yesterday I installed Opera to test my java on that browser, and it will run java applets with my 1.5.0 directory plug-in.

Any idea why Firefox will not?  

thanks,
phil[/QUOTE]
 hmmm weird make-jpkg is the java-package that you've installed, you have installed it no?

---

### Post by plewisfdx on 2005-04-06
No, in my previous post, read #2.  I get a package not found when I try apt-get install java-package.

I do, however, again, have java 1.5 working, installed...etc

---

### Post by Gandalf on 2005-04-06
[QUOTE=plewisfdx]No, in my previous post, read #2.  I get a package not found when I try apt-get install java-package.

I do, however, again, have java 1.5 working, installed...etc[/QUOTE]
 post your /etc/apt/sources.list file please because it's weird i double checked the name and i even sudo apt-get install java-package on my PC and the result (you already have the newest version of the package java-package)

---

### Post by plewisfdx on 2005-04-08
Thanks for the help, it fixed itself.

I did the dist-upgrade from within synaptic, and uncommented the security fixes, and it works great now!

thanks again,

phil

---

