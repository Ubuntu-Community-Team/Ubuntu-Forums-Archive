---
title: "Cant install Java aplication"
date: 2008-12-04
forum: General Help
---

### Post by hjmalves on 2008-12-04
Hi all

I am giving my first steps in Ubuntu and until now has been a pleaseant experience.
I have a Java app for remote access to a Xerox iGen3 printer called "FreeFlow Remote Print Server" that works well on Solaris 10.
I tried to install in Ubuntu and I got this errors:
> helder@ubuntu:~$ /home/helder/install.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
exec: 2314: /tmp/install.dir.6224/Solaris/resource/jre/bin/java: not found

After some Googling I found the LD_ASSUME_KERNEL issue and tried:

> helder@ubuntu:~$ cp ./install.bin ./install.bin.bak
helder@ubuntu:~$ sed -i "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" install.bin
helder@ubuntu:~$ ./install.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

exec: 2314: /tmp/install.dir.6887/Solaris/resource/jre/bin/java: not found

The shared libraries errors are gone but the installer stop with same error.
Anyone knows a solution for this.
Any help would be highy apreciated.

Thanks in advance
Helder Alves

---

### Post by binbash on 2008-12-04
[http://forums.sun.com/thread.jspa?messageID=10391504#10391504](http://forums.sun.com/thread.jspa?messageID=10391504#10391504)

---

### Post by hjmalves on 2008-12-05
Hi binbash abd thanks for your anwser.

When I was Googling for answers I had already seen that particular post in Sun forum, but apart from the first error I dont see anything similar that can help me since I just have an "installer.bin" that I run trough console, and after it gets unpacked and the installer stops, checking its contents I cant find the chsetup.sh file.
Where can I modify those values?

Thanks

---

### Post by hjmalves on 2008-12-05
One thing I cant understand is that the installer stops saying:
> exec: 2314: /tmp/install.dir.6887/Solaris/resource/jre/bin/java: not found 
But the file exists in that exact directory. Why does the installer says "not found"?

---

### Post by hjmalves on 2008-12-09
Anyone?

---

### Post by hjmalves on 2008-12-12
Any help from someone?
Any suggestion?

Please...

---

### Post by hjmalves on 2008-12-17
Thank you all for your help and time lost.

For someone like me that always worked with Microsoft Windows and decided to try Linux (in this case Ubuntu - the most popular distribution - I thought) this is something never happened to me in Microsoft forums: simply to be ignored.

Also a forum where we put a thread and after some minutes that thread disappears with 2 or 3 new pages in front of it cannot IMHO work. There is an evident bad categorization of this forum that makes many people post in the same area at the same time.

But as I said maybe this is the way things work to this new world - new at least to me - of open source software.

Once again sorry for all the trouble.

Helder Alves

---

### Post by jespdj on 2008-12-17
The people answering questions in the forums here are all volunteers, Ubuntu users like you from all over the world. They are not professionals hired to provide support for Ubuntu.

So, nobody has any obligation to answer your question, and you should not expect or demand that your question is answered, or even be disappointed when it doesn't get answered.

Your question is about a very specific piece of software, which most likely not many people have or use, so it's not strange that you don't get many answers - there are simply very few people who have experience with the software that you're trying to install.

No responses doesn't mean that somebody is being mean to you or is deliberately ignoring you; it simply means that nobody has anything useful to contribute.

Is the software that you're trying to install for Solaris? Solaris is not the same as Linux, so if that's the case than it's not surprising that you have some problems installing it.

Do you have Java installed? If not, install it first:
```
sudo apt-get install sun-java6-jre
```

---

### Post by hjmalves on 2008-12-17
jespdj

Dont get me wrong please.
I know that all people here are volunteers, and I know no one has obligation to answer to any post, specially of course if they dont know the answer.
I am just stating some facts that are evident to me at least:

1 - Forum is bad categorized meaning that many people post at same time in same forum and then your post gets multiple new pages in few minutes in top of it and hardly someone can see it.

2 - In terms of answers I am just disappointed with the level of participation because if you noticed my first post I said that I am new to Linux and Ubuntu so there are little things that more experienced users can advise, even if they aren't objective to that particular software they are general to all software, and the only answer I got was a link to another forum I already had tried.

So its not the fact that I didnt get useful help that I am disappointed, its the fact that as a newcomer to Ubuntu I didnt get any help and for the experience I have working with Windows for several years as System Administrator, that was not what I expected from an open source community where the change of ideas should in fact be bigger.

But I can be wrong...

About your suggestion, yes I already installed JRE from Sun and tested for installation and all is ok.

Sorry again but my goal is not to offend anyone, if I did I apologize.

Helder Alves

---

