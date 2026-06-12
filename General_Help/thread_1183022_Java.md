---
title: "Java"
date: 2009-06-09
forum: General Help
---

### Post by Steakumz on 2009-06-09
Heya. I'm trying to install java on my computer. All of the linux files on the java website wont work for me. I know how to do install .deb files but thats it. So an idiot proof walkthrough or a .deb version of java for me to install would be helpful. 

Thanks in advance

---

### Post by michy99 on 2009-06-09
You should be able to install java from the repositories without having to download anything from the website. Open a terminal and enter```
sudo apt-get install sun-java6-bin sun-java6-plugin
```

When it asks you to accept the agreement, use the tab key to select the answer and then enter.

---

### Post by Steakumz on 2009-06-09
ok well i typed the code and got this result

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-bin

---

### Post by TrakerJon on 2009-06-09
This should work from a terminal window...

**sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts**

Then visit...

**[http://ubuntuforums.org/showthread.php?t=1181327]("http://ubuntuforums.org/showthread.php?t=1181327")**

---

### Post by Steakumz on 2009-06-09
ok this time it responded with

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

---

### Post by michy99 on 2009-06-09
Which version of Ubuntu are you running?

---

### Post by Hund on 2009-06-09
I would recomend the open source version: **openjdk-6-jre**. Works really great. :)

---

### Post by TrakerJon on 2009-06-09
Many of these installations require access to the Medibuntu Repository and enabling some additional software sources. Directions are on this site: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) or if you have Ubuntu 9.04 "Jaunty Jackalope" simply do the following from a terminal window:

sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

Then type: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update ;)

---

### Post by michy99 on 2009-06-09
Personally I think the sun version works best with most programs.

Go to System->Administration->Software Sources. Make sure that the first four selections are checked on the first tab. On the second tab make sure all the boxes are checked. Close. Then try to install again.

---

### Post by TrakerJon on 2009-06-09
I agree as well...the Sun version(s) seem to "play well with others".

---

### Post by TrakerJon on 2009-06-09
Mishy is right as well...go to the System menu > select Administration > select Software Sources > Check the first four boxes under the Ubuntu Software and Updates tabs > Close and Reload

---

