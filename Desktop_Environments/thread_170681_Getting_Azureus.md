---
title: "Getting Azureus"
date: 2006-05-05
forum: Desktop Environments
---

### Post by Rhapsody on 2006-05-05
On my continuing quest to explore the land of Linux, I have found myself in need of a BitTorrent client. Back on Windows XP, I used Azureus, and I see few reasons to not use it again. Hence, my current task is to get Azureus up and running under Kubuntu.

Hoping to not need to resort to posting a query yet again, I searched the forum and stumbled upon [this](https://wiki.ubuntu.com/AzureusHowTo) Ubuntu Wiki entry about installing Azureus. This seemed promising. It first told me to add universe and multiverse repositories (already added all possible repositories while getting amaroK to work) and then gave my command to type in. Predictably enough, this didn't work.

```
Reading package lists... Done
Building dependency tree... Done
Package j2re1.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package j2re1.4 has no installation candidate
```
This seems very similar to the error I got while trying to install an MP3 CODEC for amaroK, which was fixed by enabling more repositories. As I have now enabled all repositories, this option is no longer open to me.

So does anyone have any clues here? I tend to download a lot of torrents, and Azureus would be helpful for this.

---

### Post by Ubuntuud on 2006-05-05
Well, that package contains java. If I am correct it should be in the multiverse repo. Try using synaptic and search for it.

---

### Post by Sef on 2006-05-05
To get java, click on the link below.  (Java's towards the bottom.)

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by darkninja on 2006-05-05
If you enable the multiverse repository you can "sudo apt-get install azureus". 

However this version is a little slow and quite buggy (you can't close the popup windows) but you don't have to muck around with installing Sun's Java, as the multiverse Azureus uses a open source Java implementation.

EDIT: Oops! I see you're using Breezy, this will only work on Dapper.

---

### Post by Rhapsody on 2006-05-05
[QUOTE=Sef]To get java, click on the link below.  (Java's towards the bottom.)

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")[/QUOTE]
Got up to the part where I was to type

```
sudo apt-get install fakeroot java-package java-common
```
and got

```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package
```
Of course, the way to fix this is to add the multiverse repository. Which, as mentioned, I did about a week ago.

How did I see this coming?

---

### Post by yyagol on 2006-05-05
You need java as some say

[here you can find how to install java]("https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Java") 
after installing java Azureus will run good
all i did was ```
$sudo apt-get install j2re1.4
$bzip2 -d Azureus_2.4.0.2_linux.tar.bz2
$tar -xf Azureus_2.4.0.2_linux.tar
$cd azureus/
$./azureus

``` and that was it

---

### Post by Rhapsody on 2006-05-05
[QUOTE=yyagol]You need java as some say[/QUOTE]
I gathered that. That's why my opening post in this topic details my failures in installing Java.

[QUOTE=yyagol][here you can find how to install java]("https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Java")[/QUOTE]
Which I was already linked to in this topic, which is why my second post in this topic details how those instructions also failed.

[QUOTE=yyagol]after installing java Azureus will run good[/QUOTE]
Again I gathered this from the fact that the Java Runtime Environment started every time Azureus did while I was working under Windows (which actually crashed my PC three times) and the fact that all of the documentation I have seen for Azureus says it requires Java.

[QUOTE=yyagol]all i did was ```
sudo apt-get install j2re1.4
``` and that was it[/QUOTE]
So did I. It generated the error I posted right at the start of this topic.

---

### Post by treris on 2006-05-07
maybe a little off topic, but why not give ktorrent a try? you can download the latest version directly from the site

[http://ktorrent.pwsp.net/index.php?page=downloads](http://ktorrent.pwsp.net/index.php?page=downloads)

and give it a try, it does not need java or anything and uses a lot less resources, which is never a bad thing.

---

### Post by Rhapsody on 2006-05-08
[QUOTE=treris]maybe a little off topic, but why not give ktorrent a try? you can download the latest version directly from the site

[http://ktorrent.pwsp.net/index.php?page=downloads](http://ktorrent.pwsp.net/index.php?page=downloads)

and give it a try, it does not need java or anything and uses a lot less resources, which is never a bad thing.[/QUOTE]
Well, KTorrent would work, but Azureus has more features and I like it a lot. I tend not to be doing much while my torrents are running, so resources aren't really much of a problem. Besides, I'll have to install Java at some point. There are alternative BitTorrent clients, but what else am I to do when confronted with a Java applet?

I haven't got this problem solved yet either. All of the suggestions so far in this topic either failed or weren't relevant.

---

### Post by cjazz on 2006-05-09
Try adding this line to your /etc/apt/sources.list file:

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

and then do

sudo apt-get update

and

sudo apt-get install sun-j2re1.5.

Another option for installing java is to run the program Automatix. It can be found by searching this forum or at [this site](http://www.beerorkid.com/automatix/).

---

### Post by cjazz on 2006-05-09
Sorry. Duplicate post.

---

### Post by yyagol on 2006-05-11
sory

---

### Post by Rhapsody on 2006-05-12
[QUOTE=cjazz]Try adding this line to your /etc/apt/sources.list file:

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/QUOTE]
Quick question. How do I do that?

---

### Post by safecracker on 2006-05-12
Just open a terminal then use your favorite text editor, for example I would type:

```
vi /etc/apt/sources.list
```

then add deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free to the file and save. You can use whatever editor you are comfortable with.

after this remember to do a: 

```
sudo apt-get update
```

---

### Post by SShadow on 2006-05-16
I did as listed below and I still got the same error msg as the original author... And I just finished installing Java in order to use VNC to my home computer (and the Java is working).  This problem has nothing to do with Java, I am afraid.
The only other answer I have seen is installing Automatix - and I have issues with that as well (changes sources.list with some entries that are no longer working which totally messes up apt-get...)
Anyways, any other ideas?

[QUOTE=safecracker]Just open a terminal then use your favorite text editor, for example I would type:

```
vi /etc/apt/sources.list
```

then add deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free to the file and save. You can use whatever editor you are comfortable with.

after this remember to do a: 

```
sudo apt-get update
```[/QUOTE]

---

### Post by safecracker on 2006-05-24
[QUOTE=SShadow]I did as listed below and I still got the same error msg as the original author... And I just finished installing Java in order to use VNC to my home computer (and the Java is working).  This problem has nothing to do with Java, I am afraid.
The only other answer I have seen is installing Automatix - and I have issues with that as well (changes sources.list with some entries that are no longer working which totally messes up apt-get...)
Anyways, any other ideas?[/QUOTE]

Did you remember to set your java to:

```
sudo update-alternatives --set java /usr/lib/j2re1.5-sun/bin/java
```

---

