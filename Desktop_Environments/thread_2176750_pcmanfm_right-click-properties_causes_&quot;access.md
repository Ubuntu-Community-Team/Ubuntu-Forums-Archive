---
title: "pcmanfm right-click-properties causes &quot;access content&quot; property to change recursively"
date: 2013-09-25
forum: Desktop Environments
---

### Post by Dreamer Fithp Apprentice on 2013-09-25
Using Lubuntu 13.04, 32 bit on an ext3 file system querying properties of a directory with the context menu in pcmanfm will frequently cause the "access content" property to silently change to "nobody" recursively. This makes the folder seem empty when I open it or take another properties later. I'm afraid I deleted several "empty" folders that weren't really empty before I figured out what was happening. What tipped me off was that it did it a couple of times to folders that had files belonging to root somewhere in the there and it popped an error box saying it was unable to change those.

Any idea what would cause this or what I can do to prevent it? If I can't be sure of stopping it, is there any reason to think it's NOT a pcmanfm problem specifically? Because I'll switch to Thunar if I can't be sure of fixing this with pcmanfm.

If nothing else, anybody got any idea for some kind of workaround? Maybe some kind of monitor that will call attention to this when it happens?

---

### Post by walterorlin on 2013-09-26
Do not empty the trash as that will get rid of all of your files. Have you tried using lxterminal to get to the files and and then still seeing if you can change directory. This link will be useful to you to change the folders back to having the correct permisson which says they need execute and you need to be able to access them and modify them if you want. [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) Although this is tricky and recursively chmoding can lead to a bad system so might be better to do them one at a time.

---

### Post by mörgæs on 2013-09-26
Is this the bug?
[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1131789](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1131789)

---

### Post by vasa1 on 2013-09-26
> **mörgæs said:**
> Is this the bug?
[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1131789](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1131789)
That bug was or is about **Package: pcmanfm 0.9.10-0ubuntu2**

```
[07:34 AM] ~ $ apt-cache policy pcmanfm
pcmanfm:
  Installed: 1.1.0-0ubuntu2
  Candidate: 1.1.0-0ubuntu2
  Version table:
 *** 1.1.0-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ raring/universe i386 Packages
        100 /var/lib/dpkg/status
[07:53 AM] ~ $ 

```

---

### Post by mörgæs on 2013-09-27
Yes, and if noone has fixed he bug it's also about all subsequent versions.

---

### Post by Dreamer Fithp Apprentice on 2013-09-27
> **walterorlin said:**
> Do not empty the trash as that will get rid of all of your files.Thanks, Walter. Good advice indeed. I hadn't given much thought to the contents of the "empty" folders I deleted in the past. I just remember occasionally being surprised they were empty.  Come to think of it, I'm not sure pcmanfm would LET me delete directories if I didn't have permission to access the content. That would be extremely bad design, so perhaps they truly were empty. Anyway, I doubt I deleted anything important or I would have had a memorable hissy fit at the time. Still, I probably should look through the trash to see if there is anything I want to recover. Good idea.> **walterorlin said:**
> Have you tried using lxterminal to get to the files . . . Yes. Same story as with pcmanfm. Not showing the files isn't really ALL that odd, although it would be better if double clicking a folder I don't have permission to access the contents of, didn't show something that looks exactly like what I see when I double click an empty folder. The STRANGE thing is the spontaneous silent resetting of permissions.> **walterorlin said:**
>  . . . and and then still seeing if you can change directory.Change the directory permissions you mean? Yes, that's no problem. I can chmod -R 777 and get the normal expected behaviour. The problem is that I shouldn't have to keep doing that over and over again.

I shouldn't have thrown in a red herring by mentioning remembering deleting "empty" folders that I was surprised were empty in the past and now wondering what I deleted. I wasn't deleting files when I noticed this odd behaviour. I was using pcmanfm to copy a large directory (large in terms of the total contents of the sub and sub-sub,etc. directories, from an ex3 system on one drive to an ex3 system on a newer drive and useing properties to check the total byte content of both to make sure they matched, taking that as an adequate indication that the copy was probably good. I realise there are ways of being more absolutely certain but they take longer and I assume the chance of getting a corrupt copy that is exacty the right size is low enough that I'm usually willing to ignore it. Normally if I don't get an exact match I can narrow the problem down to individual files and try again. But I kept getting weirdly low numbers on both the original AND the copy and kept finding the access set to nobody. I didn't at first realize that the resetting went with taking the properties.> **walterorlin said:**
>  . . . recursively chmoding can lead to a bad system so might be better to do them one at a time.Indeed. It is surprising how much havoc you can cause with a system partition that way. Found that out by doing it a year or 2 ago. I'm still not sure why that is. Seems if everything was 777 it still ought to work even if becomes dangerously insecure. But not an issue in this case anyway as source and copy are both pure data partitions.

> **mörgæs said:**
> Is this the bug?
[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1131789](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1131789)Good question, Mörgæs. Could be at least related. Post # 3 at that link certainly makes it sound similar at any rate. Although the OP there seems to me to be saying it is only a particular file that isn't showing up, not the whole directory's content. And also that ls in a terminal emulator shows the file. I don't think ls showed anything in my case but I'll have to wait for this to recur or figure a way to induce it consistently before I can be absolutely certain. So the manifestation is not exactly the same, and if I report it as a bug, which I guess I should, I'll file it seperately and include a link to that. Thanks.
> **vasa1 said:**
> That bug was or is about **Package: pcmanfm 0.9.10-0ubuntu2**

```
[07:34 AM] ~ $ apt-cache policy pcmanfm
pcmanfm:
  Installed: 1.1.0-0ubuntu2
  Candidate: 1.1.0-0ubuntu2
  Version table:
 *** 1.1.0-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ raring/universe i386 Packages
        100 /var/lib/dpkg/status
[07:53 AM] ~ $ 

```Thanks, Vasa1. I didn't know that command. Here's mine:```
$ apt-cache policy pcmanfm
pcmanfm:
  Installed: 1.1.0-0ubuntu2
  Candidate: 1.1.0-0ubuntu2
  Version table:
 *** 1.1.0-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ raring/universe i386 Packages
        100 /var/lib/dpkg/status
```

So, all in all, guys: Do you think this is most likely a pcmanfm bug? As opposed to some config file somewhere I need to edit and as opposed to some bug somewhere else that is likely to affect other gui file managers the same way? Because if the odds are good that it is, I'll be a good cit and report it and meanwhile switch to thunar. I've been kind of on the fence about doing that anyway. The godawful crashing of versions < 1 in pcmanfm seems to be fixed in 1.1 but thunar still does custom actions better than any of the gui fms I've used.  Thanks for your thoughts.

---

### Post by Dreamer Fithp Apprentice on 2013-09-27
> **Dreamer Fithp Apprentice said:**
>  . . .  I don't think ls showed anything in my case but I'll have to wait for this to recur or figure a way to induce it consistently before I can be absolutely certain. 
I'm wrong about that. It happened again now and ls will show the filenames. 
And for what it is worth this time was on a different drive.
========================
Added with edit a day later:
For now I'm trying thunar to see if the same thing happens with it. So far, it hasn't. On a folder tree that pcmanfm properties had set the access permission to "nobody" I tried changing it back with thunar rather than the cli and it popped up a xenity-like box that said:

"The folder permissions are inconsistent, you may not be able to work with files in this folder. " Then I believe there was a button to "[Correct folder permissions . . . ]" which I clicked.

That brought forth another box saying:
"Correct foldr permissions automatically?
The folder permissions will be reset to a consisternt state. Only users allowed to read the contents of this folder will be allowed to enter the folder afterwards."
with 2 buttons like this:
"[Cancel] [Correct folder permissions]"
I clicked [Correct folder permissions].

I'm not sure what to make of that but perhaps someone will.

---

