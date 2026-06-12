---
title: "Still can't load Java"
date: 2006-03-14
forum: Desktop Environments
---

### Post by snooker on 2006-03-14
Hi ... I am still having some problems with loading Java , What I have done so far , I downloaded Sun jre_1_5_06-Linux-i586.bin file onto my desktop , I have enable universe & multiverse repositories , what I done next was >>> Applications >>> Accessories >>> Terminal and done this code below 

```

sudo 
pwd
cd ~/Desktop
chmod +x jre-1_5_0_06-linux-i586.bin

```

Afterward I would double click on the Java file on my desktop , which at this time pop up a window with
a few options , I select to open with the terminal , At this time it starts to load the Java , I agree to the license which I type " Yes " to , It starts to download the program and in the end it more or less said that it got installed , I reboot the comp , Go visit this certain site and I get alert that there additional plugin required to display all the media on the page , So if someone could be so kind as to explain where I may find these additional plugins ? Thanks 

BTW >> I have try going to Firefox site for the plugins but , It just show for a later version of sun java_1_5_01 version

---

### Post by knalle on 2006-03-14
First install some required packages:

```
sudo apt-get install fakeroot java-package java-common
```

Create the Deb file for the install:

```
fakeroot make-jpkg sun-j2sdk-1.4.2_10-linux-i586.bin
```

Install The deb file

```
sudo dpkg -i sun-j2sdk-1.4.2_10_i386.deb
```

Now make SUN Java the default by running this command and selecting it.

```
sudo update-alternatives --config java
```

You can now check your fresh SUN Java with:

```
java -version
```

Happy Hacking!

---

### Post by snooker on 2006-03-14
Hi ... Thanks for the response , If I go to the terminal and add this code first ? 

```
 sudo apt-get install fakeroot java-package java-common 
```
I get this below instead 

sn00ker@ubuntu:~$  sudo apt-get install fakeroot java-package java-common
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package
sn00ker@ubuntu:~$

---

### Post by knalle on 2006-03-14
ah, sorry, forgot, if you haven't enabeled multiverse;

```
sudo gedit /etc/apt/source.list
```
if you don't have **gedit** use any editor you want, add the word **multiverse** after the word **universe** on every line you see, save and exit your editor

refresh apt
```
sudo apt-get update
```

then try again

---

### Post by snooker on 2006-03-14
Hi ,,, Are you saying whether if I have enable the multiverse and universe in the repositories ? Because I have enable everything in there , I have place a check mark on all of them , Am I still missing something ? Thanks

---

### Post by snooker on 2006-03-15
Hi ... I finally got the java working , I just went to the "Add Applications" section and notice that there is a basic java package available , which did the trick , Thanks for help :cool:

---

