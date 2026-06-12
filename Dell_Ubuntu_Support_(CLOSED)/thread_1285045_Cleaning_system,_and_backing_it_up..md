---
title: "Cleaning system, and backing it up."
date: 2009-10-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Arndtwe on 2009-10-07
I have a Dell mini 9, running Ubuntu jaunty 9.04.

My question (issue) is this: I would like to know if there is a way to get a list of every single file on my hard drive that is not used to operate either the operating system or any of the applications on my system. In other words, is there a piece of software, or a terminal command that will list all files that can be removed from my system without touching any sort of config settings, programs, etc? I would like to reduce my hard drive occupation space to the smallest amount possible. All I want is a list, from there I would manually remove each file,as there are still some I want to keep, like documents, pictures, music... 

The second task I wish to accomplish, after cleaning my system to the max, is backing it up. I've looked into a number of programs, methods for doing this and am not sure which would be best. Ido not simply want to backup my personal files, I want to back up the whole operating system, the programs I have installed, their settings, everything! What's the best way to do this? I've read about TAR'ing the entire filesystem, that sounds like it would do it. What are your thoughts?

---

### Post by c0mput3r_n3rD on 2009-10-07
I wouldn't touch any of the system files, they're all pretty much necessary.  How ever, if you would like remove applications like evolution, use apt-get
Ex:
```

sudo apt-get remove evolution

```

And you can do that for other such applications like your games; note that if you remove one of the pre-installed games you have remove all of the ones (that you didn't install) because it's a package.  You can always google whether you can remove a certain application so you don't remove anything necessary.

---

### Post by ElSlunko on 2009-10-07
For back up I use Back In Time. You can pretty much back up anything you'd like. For the whole system I suppose you would back up "/" and not exclude anything.

I personally just back up the home Directory and exclude all hidden files with Back In Time. I did a week of snapshots and did a full reinstall of Ubuntu, installed Back In Time, and a few hours laters all 650gbs of my data was restored. Then I simply had to install my programs & reconfigure them. I guess I could probably back up the entire system, but I haven't tried it.

As for your first question, no idea!

---

### Post by Arndtwe on 2009-10-07
> **c0mput3r_n3rD said:**
> I wouldn't touch any of the system files, they're all pretty much necessary.  How ever, if you would like remove applications like evolution, use apt-get
Ex:
```

sudo apt-get remove evolution

```

And you can do that for other such applications like your games; note that if you remove one of the pre-installed games you have remove all of the ones (that you didn't install) because it's a package.  You can always google whether you can remove a certain application so you don't remove anything necessary.
That is why I would like a list of all files that are not system files. See, I would like to produce a list of all the files that have no affect on how the system runs or functions. For instance, a text document in my home folder that contains the words "hello world" would show up in the list. You could delete that file, and nothing would happen to your system. I simply want to get a list of every file in "/" that would not have an effect if deleted. Make sense?

---

### Post by Arndtwe on 2009-10-07
> **ElSlunko said:**
> For back up I use Back In Time. You can pretty much back up anything you'd like. For the whole system I suppose you would back up "/" and not exclude anything.

I personally just back up the home Directory and exclude all hidden files with Back In Time. I did a week of snapshots and did a full reinstall of Ubuntu, installed Back In Time, and a few hours laters all 650gbs of my data was restored. Then I simply had to install my programs & reconfigure them. I guess I could probably back up the entire system, but I haven't tried it.

As for your first question, no idea!

I will have to look into that one and see whats features it has! Thanks!!!

---

### Post by ElSlunko on 2009-10-07
There is also Deja Vu. It can back up to cloud storage and some other really amazing features. I considered going that way but I'm sticking with Back In Time for now because I KNOW it works on my system. Data backup is contingent on reliability :)

---

### Post by Arndtwe on 2009-10-10
Bump

---

### Post by ugm6hr on 2009-10-12
> **Arndtwe said:**
> That is why I would like a list of all files that are not system files. See, I would like to produce a list of all the files that have no affect on how the system runs or functions. For instance, a text document in my home folder that contains the words "hello world" would show up in the list. You could delete that file, and nothing would happen to your system. I simply want to get a list of every file in "/" that would not have an effect if deleted. Make sense?

Any file in /home other than hidden folders are personal files.  Hidden folders in the directories are generally personal settings, which can be removed, but the relevany applications would then default back to original settings.

Unless you deliberately store personal files outside /home, every other directory contains necessary files and cannot be modified, other than perhaps root trash.  See: [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by Arndtwe on 2009-10-12
> **ugm6hr said:**
> Any file in /home other than hidden folders are personal files.  Hidden folders in the directories are generally personal settings, which can be removed, but the relevany applications would then default back to original settings.

Unless you deliberately store personal files outside /home, every other directory contains necessary files and cannot be modified, other than perhaps root trash.  See: [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

Ok, let me give you a little more detail as what I am refering to. I'm sorry if I have been unclear in previous posts. I would like to remove everything that is not necessary. Everything. For instance, I used to have python2.5 installed next to python2.6. I have since removed pthyo2.5 and used deborphan + ubuntu tweak to get rid of anything unnecessary off of my system. According to those to programs, my sytem is now free of anything related to python2.5. As it turns out, doing a file search of my system, using the term "python2.5" produces over 30 files and folders that are named python2.5. I don't need these, and they are taking up precious disk space.

I can manually remove these, which is the solution. The problem: there are a number of other programs and packages that I have removed in the past and the exact same problem is there. Since They were in the past, and that time I was not worried about it, I cannot remember the names of those programs and packages. Therefore I cannot do a search for them to remove anything that is not necessary.

All I want to be able to do is get a list of all files and folders like the "python2.5" example, so that way I can manually remove them. Solutions anyone?

---

### Post by gbrainin on 2009-10-13
Open the Synaptec Package Manager (under System->Administration).  In the file menu, you can pull up the history of every package you have installed, removed, or upgraded.

---

### Post by ugm6hr on 2009-10-13
> **Arndtwe said:**
> For instance, I used to have python2.5 installed next to python2.6. I have since removed pthyo2.5 and used deborphan + ubuntu tweak to get rid of anything unnecessary off of my system. According to those to programs, my sytem is now free of anything related to python2.5. As it turns out, doing a file search of my system, using the term "python2.5" produces over 30 files and folders that are named python2.5. I don't need these, and they are taking up precious disk space.

Are these files outside /home?

---

### Post by Arndtwe on 2009-10-13
> **ugm6hr said:**
> Are these files outside /home?

Yes. Every single one of them was outside of /home. Most were in /usr/lib/... but they were also in /usr/share/... and /usr/local/... . Other places as well, but I do not remember where. If you would like a complete list of file paths I can dig them up from my terminal history.

---

### Post by Arndtwe on 2009-10-13
> **gbrainin said:**
> Open the Synaptec Package Manager (under System->Administration).  In the file menu, you can pull up the history of every package you have installed, removed, or upgraded.

My synaptic only has history throughout October 2009. This is helpful, but there is still more.

---

### Post by Jon_J on 2009-10-13
What about removing "cups" related files and libs?
I'll never use my mini-10 to print anything.
Many times when browsing symatic and looking at installations, there's a "cups" related file or lib shown.
I have Xubuntu 9.04 installed.

---

### Post by gbrainin on 2009-10-13
> **Arndtwe said:**
> My synaptic only has history throughout October 2009. This is helpful, but there is still more.

That's very odd.  Mine has history back to the day I installed this version (not including the installation itself, of course).

Of course, if you want a really clean system, you can always reinstall instead of upgrading.  If you back up (or don't overwrite) your /home, you won't lose anything.

---

