---
title: "Which desktop search tool searches hidden files?"
date: 2009-08-22
forum: Desktop Environments
---

### Post by vickoxy on 2009-08-22
So, i need some fast desktop search tool, which searches hidden files too.

Google desktop doesn´t do it, nore tracker. 

Is there any that can be integrated in deskbar-applet, or standalone as gnome-do?

Thanks

---

### Post by aysiu on 2009-08-22
> **vickoxy said:**
> So, i need some fast desktop search tool, which searches hidden files too.

Google desktop doesn´t do it, nore tracker. 

Is there any that can be integrated in deskbar-applet, or standalone as gnome-do?

Thanks Go to Places > Search for Files and select to add the option for looking at hidden files also.

More details in the attached screenshots.

---

### Post by Ron_P on 2009-08-23
Beagle seems to be pretty good . You can install it from the repositories.

[Beagle Homepage.]("http://beagle-project.org/Main_Page")

---

### Post by vickoxy on 2009-08-23
> **Ron_P said:**
> Beagle seems to be pretty good . You can install it from the repositories.

[Beagle Homepage.]("http://beagle-project.org/Main_Page")

I installed it yesterday and deinstalled it because it was draining too much power from my dell mini9 (was hot as hell :))

---

### Post by vickoxy on 2009-08-23
> **aysiu said:**
> Go to Places > Search for Files and select to add the option for looking at hidden files also.

More details in the attached screenshots.

Thanks for answer, but i am searching for some panel bar (as deskbar)  or standalone (as gnome-do) search tool. I think that every time i have to search hidden file i have to  activate it the way you proposed?

Thanks

---

### Post by Ron_P on 2009-08-23
> **vickoxy said:**
> I installed it yesterday and deinstalled it because it was draining too much power from my dell mini9 (was hot as hell :))

Not sure what you have installed and running but it is highly configurable and I don't even know its there. You can configure it so it only indexes directories of your choice and how much of your resources it uses. I suppose depending on how its configured it could be a resource hog during the initial indexing. I think its pretty awesome .
I am using a Dell Inspiron 1521 AMD Turion about 1.8 gighertz with 2 gig ram.

---

### Post by vickoxy on 2009-08-23
> **Ron_P said:**
> Not sure what you have installed and running but it is highly configurable and I don't even know its there. You can configure it so it only indexes directories of your choice and how much of your resources it uses. I suppose depending on how its configured it could be a resource hog during the initial indexing. I think its pretty awesome .
I am using a Dell Inspiron 1521 AMD Turion about 1.8 gighertz with 2 gig ram.

Does it search hidden files too?

I have tracker with deskbar, but it does not search hidden files. 

"Initial indexing"-that menas it won´t index after every startup? How does it then update files changes?

Does it have built in search inside of pdf/doc files?

Sorry for so many questions...

Thanks

---

### Post by Ron_P on 2009-08-23
> **vickoxy said:**
> Does it search hidden files too?

I have tracker with deskbar, but it does not search hidden files. 

"Initial indexing"-that menas it won´t index after every startup? How does it then update files changes?

Does it have built in search inside of pdf/doc files?

Sorry for so many questions...

Thanks

If you go into System/Preferences/Search and Indexing it will bring up the tracker configuration screen. It has settings on that screen to save battery power on laptops during initial indexing. A bunch of  other things you can do  too  like  tell it what directories to index. I'm pretty sure it will  index hidden files.

How does Beagle update itself ? Through a program called inotify. Inotify monitors file system events .

I'm not sure about built in search but I am pretty sure you can do that. I just started using it and its great. And , yes , it does index and search your hidden files unless you create filters to not do it. The filters are easy to set up .

Hope this helps some. 

Good luck

---

### Post by vickoxy on 2009-08-23
> **Ron_P said:**
> If you go into System/Preferences/Search and Indexing it will bring up the tracker configuration screen. It has settings on that screen to save battery power on laptops during initial indexing. A bunch of  other things you can do  too  like  tell it what directories to index. I'm pretty sure it will  index hidden files.

How does Beagle update itself ? Through a program called inotify. Inotify monitors file system events .

I'm not sure about built in search but I am pretty sure you can do that. I just started using it and its great. And , yes , it does index and search your hidden files unless you create filters to not do it. The filters are easy to set up .

Hope this helps some. 

Good luck

Thanks for answer-unfortunately tracker does not search hidden files-i checked it (can you tell me which tracker version you use-i installed it from synaptic)?.

Still,  does beagle perform indexing after each restart or it does it only once (plan to index all hard harddisk)?

---

### Post by Ron_P on 2009-08-23
> **vickoxy said:**
> Thanks for answer-unfortunately tracker does not search hidden files-i checked it (can you tell me which tracker version you use-i installed it from synaptic)?.

Still,  does beagle perform indexing after each restart or it does it only once (plan to index all hard harddisk)?


I use Gnome tracker version 0.6.6. Yes it indexes in the background but its optional. Like all indexing the initial indexing takes some time. After that its just a background indexing that only updates when innotify triggers a filesystem event , i.e. like a file changing or being added or deleted from a directory. highly configurable.

---

### Post by vickoxy on 2009-08-23
So,yyou use traacker or beagle? I use tracker with deskbar-applet,but deskbar crashes a lot.search results are very good. And what about beagle?do you use it also?

---

### Post by Ron_P on 2009-08-23
> **vickoxy said:**
> So,yyou use traacker or beagle? I use tracker with deskbar-applet,but deskbar crashes a lot.search results are very good. And what about beagle?do you use it also?

I have indexing disabled on tracker. Either Beagles website ,or Trackers web site explains how these two programs work with each other. If you have both enabled then Beagle takes priority 

I use Beagle though as my desktop search tool.Also you can disable indexing if you are on battery power.

Are you absolutely sure that tracker does'nt index hidden files ? From what I have read , it will index everything in your home directory. To me that implies that it does index and will show hidden file contents in a search. Its possible your filters are setup to not index directories with a dot (.) preceding the folder . (Hidden directories/files)

You can check by opening up your preferences in Tracker.

---

### Post by vickoxy on 2009-08-23
I am pretty sure that i read somewhere that tracker does not search for hidden files. But i ma not now sure was that beagle, or tracker, or recoll (i know for sure that google desktop search does not do that)

So, i tried almoste every desktop search tool:

1) like deskbar and his implementation od tracke-but it kepps crushing after two or three searchings.
2) gnome-do looks awesome, it is fast, but i have to add every folder to setup to make search in this folders.
3) beagle was making my computer too hot-maybe i should give another try.

I wanted some quick search panel bar /as deskbar or gnome do/ but configuration of each every one is limited (gnome-do does not index more than 3000 files-so it is impossible to index all computer, tracker would take few hours to make it for all computer-but with deskbar applet crushing-not really nice opportunity)

Does anyone has any suggestion? Or am i asking too much?

---

### Post by vickoxy on 2009-08-23
Ok, does anybody knows if beagle is searchin hidden files? I couldn´t find nothing in setup.

I installed the beagle but indexing is doing its job...

---

### Post by vickoxy on 2009-08-23
No one-beagle -hidden files?

---

### Post by vickoxy on 2009-08-23
I tried tracker 0.6.93 and beagle-but no, still i couldn´t set them to search hidden files. Can anone who  use this tools try to search something what is hidden to confirm me that they can not search hidden files. If they can could someone tell me how to do it?

Thanks

---

### Post by vickoxy on 2009-08-24
> **Ron_P said:**
> I have indexing disabled on tracker. Either Beagles website ,or Trackers web site explains how these two programs work with each other. If you have both enabled then Beagle takes priority 

I use Beagle though as my desktop search tool.Also you can disable indexing if you are on battery power.

Are you absolutely sure that tracker does'nt index hidden files ? From what I have read , it will index everything in your home directory. To me that implies that it does index and will show hidden file contents in a search. Its possible your filters are setup to not index directories with a dot (.) preceding the folder . (Hidden directories/files)

You can check by opening up your preferences in Tracker.

Just found here that tracker does not search hidden files. The thread is old but i think that is just the same today:

[http://ubuntuforums.org/showthread.php?t=520853&page=3](http://ubuntuforums.org/showthread.php?t=520853&page=3)

So, i think beagle does not search hidden files-hmmm-what to use?

---

