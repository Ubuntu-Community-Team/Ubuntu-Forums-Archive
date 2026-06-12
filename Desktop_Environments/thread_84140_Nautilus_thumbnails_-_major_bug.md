---
title: "Nautilus thumbnails - major bug?"
date: 2005-10-30
forum: Desktop Environments
---

### Post by ossi on 2005-10-30
Hi!

Today I worked with eog (eye of gnome) and Nautilus software to edit a few pictures. Somehow Nautilus turned out to become more and more buggy and finally crashed everytime I tried to access the directory where the pictures are in. The files are not broken and can be accessed without problems with konqueror and console. 

So I had a look at the hidden directories in the home directory and found the .thumbnails directory where my normal folder had grown vast. So I thought that was the problem. I deleted it and hoped that would fix the situation. It didn't. I also had a look at the fail directory. Erasing that also didnt fix the situation. After deleting i replaced the directories with folders with the exact same name. The funny thing was, that when I copied the old folder of "normal" back to its place I had no problem with accessing the rest of my hd except the folder with the new pictures. It seems, that Nautilus can't create new thumbnails anymore. I am sorry I can't give you more details because it is hard to get commandline outputs from Nautilus (btw: why that?  - isnt it supposed to be open-source?). 

I finally "solved" the situation now by simply telling Nautilus it should not create thumbnails by using preferences. It was the only option I had because otherwise it would keep crashing everytime you scroll across a picture. I am pretty sure the problem is, that Nautilus cant create new thumbnails anymore. I ve really tried for some time and, like I already mentioned before, it works without any problems with konqueror to access and preview the files. There might be some broken file in the program or library which Nautilus uses for creating thumbnails, though I didn't find anything. I even tried to simply uninstall and reinstall the nautilus package. That did not take any effect either.

Can somebody tell me how to find out and solve the problem through explaining how picture thumbnails are created? Is there any other possibility to find the problem? Why isn't the .thumbnail directory deleted when it grows so big (there most heva been some 30000 files in it)? Most files in there surely were not used for a long time? Anyway, no thumbnails generated now. Nautilus keeps crahsing consistently when I keep the option activated, thoug h the directories are there and empty now. Help requested....

---

### Post by magnusbb on 2005-10-30
A very interessting post, and possible bug, this one. I had a look at my **thumbnail** directory and it gave me "2289 items, totalling 100,9 MB".  That's ok, but it shouldn't be more than that. Looking at the dates, my directory has never been cleaned. It's possibly never going to happen, neither, and that's not good. This needs further investigation.

But a possible solution to your problem would be to open Synaptic and mark the different Nautilus packages for re-install. That has helped me a couple of times - it may be wrong - but it does no harm.

---

### Post by ossi on 2005-10-30
Well, first of all: I am using Ubuntu since Warthy and have been upgrading - not completely new installing the system. So the directory we are talking about had about 30.000 files with about 800MB size. When I tried to do a ls of the directory I got problems. So the quantity of the data might have taken its effect. Anyway, I deleted the directory. 

I know also tried to reinstall all the packages. This did not have any effect. Nautilus still shows the same behaviour. It has got troubles to build new thumbnails. Could there be some file or anything broken, that I got to unlock again??

--------------------------------- 

EDIT: Today it turned out the RAM is broken. I will exchange it and then try again and see, if the bug is gone. greets

---

### Post by chris_andrew on 2005-11-18
Have you reported the bug?

[http://bugzilla.ximian.com/simple-bug-guide.html](http://bugzilla.ximian.com/simple-bug-guide.html)

Thanks,

Chris.

---

### Post by poptones on 2005-11-18
Is it a bug? Manicuring that folder could take some time. I have maybe half a million images on my filesystem and you can imagine the size of this folder - I've simply made it a link in my home to a hidden thumbnail directory on main storage because  I have only a 6GB /home and the .thumbnail folder has grown to more than 5GB.

It can take a while just to delete this folder. I would imagine "scanning" it to make sure the files it created are still active would be even slower. 

Frankly, this is just one more example, I think, of why nautilus is such a poor tool in the first place - metadata on a folder belongs in hidden storage in the folder, not in the user's profile. If you have a custom view set for a folder and you delete it, that metadata remains in your profile; every thumbnail of every file in every folder, even after that folder has been moved or deleted, remains in your thumbnail directory. But reporting this as a bug won't help - I've looked over the lists and it appears the core devs consider this all a "feature" until gnome-vfs "is complete" -- whenever that may be.

---

### Post by magnusbb on 2005-11-18
Please don't jump to conclusions. And let's be constructive; if it is a bug, report it.

Nautilus is a great tool. I enjoy it.

---

### Post by ossi on 2005-11-23
Well, it seems to be a bug. My RAM works again, but previewing images still does not work. So I ll report it. I don't have any other problems with Nautilus yet. I don't think it's a bad software, but probably something could be done to integrate it in the Gnome desktop even better. greets

---

### Post by bicchi on 2006-02-13
To get the size ocupied by the thumbnails go the directory ~/.thumbnails and  issue the command
```
du -h .
```
In my case the output happens to be:
97M     ./normal
580K    ./fail/gnome-thumbnail-factory
584K    ./fail
8.6M    ./large
106M    .

So all my thumbnails add up to 106M and I have been using breezy on a fresh install for about 4 months now.

A bug seems to have been filed allready.
[http://bugzilla.gnome.org/show_bug.cgi?id=150483]("http://bugzilla.gnome.org/show_bug.cgi?id=150483")
[http://bugzilla.gnome.org/show_bug.cgi?id=141073]("http://bugzilla.gnome.org/show_bug.cgi?id=141073")

Here is an [image showing the patch]("http://bugzilla.gnome.org/attachment.cgi?id=36044&action=view") that could have been applied to nautilus.

---

### Post by Kateikyoushi on 2007-02-16
My thumbnails folder also grew to a huge size it reached 800 MB already and I use it for half a year only, a pity the clean thumbnails button r to set limit did not make it to gnome 2.16 yet.

---

### Post by yabbadabbadont on 2007-02-16
I don't use Gnome any longer, but certain applications will insist on writing to the .thumbnails directory no matter what.  So I just made my ~/.thumbnails be a symlink to /dev/null and problem solved.  ;)

---

### Post by Kateikyoushi on 2007-02-16
Yeah but in that case it wouldn't work, I could just turn thumbnails off, setting a maximum size would be the best now have to purge it once  a month, well I can live with it.

---

### Post by yabbadabbadont on 2007-02-16
Actually, you will still be able to view thumbnails.  It just means that they will have to be recreated every time you want to see them.  (since they get thrown away when the program closes)

---

### Post by Kateikyoushi on 2007-02-16
Sounds good I give it a try, thanks for the idea, if wouldn't work might put it in a small ramdrive.

---

### Post by ardchoille42 on 2007-02-16
I am using Ubuntu Dapper Drake and I have a daily cronjob that does

```

rm -r ~/.thumbnails

```

I found I had to do this because there was no way to turn off thumbnail creation and the thumbnail directory grows and grows until you empty it... which is stupid in my opinion. There should be a way of limiting or turning off thumbnails in Dapper but I haven't found a way to do that. My thumbnails directory gets deleted every day (along with other junk files like ~/.recently-used and ~/.xsession-errors) and I haven't seen any problems with this practice.

---

### Post by cb474 on 2007-08-12
> **yabbadabbadont said:**
> I don't use Gnome any longer, but certain applications will insist on writing to the .thumbnails directory no matter what.  So I just made my ~/.thumbnails be a symlink to /dev/null and problem solved.  ;)

Could someone explain precisely how to do this? I would love to not have thumbnail images saved!

---

### Post by AZzKikR on 2007-08-13
Take a look at the ln command:
```
$ man ln
```
You'd have to execute something like this:
```
$ cd ~
$ ln -s /dev/null .thumbnails
```
I am not at my Ubuntu at the moment, please check the manual page for information, not sure if the command will work like this :)

---

### Post by cb474 on 2007-08-13
Thanks. That seems to work. Although I found I had to remove the existing .thumbnails folder first.

---

