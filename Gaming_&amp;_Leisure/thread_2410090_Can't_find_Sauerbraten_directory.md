---
title: "Can't find Sauerbraten directory?"
date: 2019-01-10
forum: Gaming &amp; Leisure
---

### Post by Butthead on 2019-01-10
Hi,

I installed sauerbraten (probably nobody here plays it anymore though? :) ) using the Discover software center, and I wanted to add a few user created maps to it that I found over on GameBanana.  Problem is, I can't seem to find the directory it's stored in (supposedly ~/.sauerbraten from a help file I read somewhere?) on my Hard Drive anywhere.  My question is, does Ubuntu (or it's derivatives) store sauerbraten in some kind of alternative directory structure? 

I also tried searching for it's map files (*.oq(something?)) using the Dolphin File Manager (I figured since there are maps in the actual game itself that something should come up), but nothing comes up there either. :confused: 

It's really no big deal if I can't add 3rd party maps to it, but not being able to figure out how to accomplish it is driving me slightly crazy.   ](*,)

---

### Post by CatKiller on 2019-01-10
Assuming you installed through your package manager, the game files are installed to /usr/share/games. The per-user config files are stored in ~/.sauerbraten. Since that starts with a . it will be hidden by default in file managers. Ctrl-H will show hidden files.

---

### Post by Butthead on 2019-01-11
Thanks, that did the trick (sauerbraten directory structure in linux figured out). ):P

Now to figure out how to get the map to show up and actually work now? :confused:

---

### Post by TheFu on 2019-01-12
Another option is to use **locate** or **find**.  Locate is part of the updatedb package and scans the file system daily for new files and directories.  Any part of a name can be queried.  The results are nearly instant, once the indexing is complete.  The returned results are subject to permissions, so files that a userid cannot see due to permissions are not shown.

**locate -i uerbrat** would likely find it.
If you can't wait for the updatedb index process to run (I think it runs daily by default), then you can search using all sorts of file/directory properties.
**find /path/to/directory -iname "*uerbrat*" -type f -mtime -1 -print**   This command will look for **files** less than** 1 day** old from the **/path/to/directory **down, recursively.  If you have no idea, use / for that directory.  You can look for links, directories, limit to 1 file system, follow links, follow across file systems, look at creation time, access time, modified time, size (equal, smaller, larger), ownership, group, permissions and probably 20 other attributes.  Boolean logic is supported with AND/OR and parenthesis.  Limiting by mtime will speed up the search exponentially.  This search doesn't use any indexing, so it does have to walk the directory tree, recursively.  You can provide multiple first-level directories to search under, if you aren't certain.

But pretty much all end-user files will be stored in the userid's HOME unless you've gone out of you way to do something different.  Most of the time, end-users cannot write files anywhere besides their HOME and /tmp/ .

If you've solved this question, please mark the thread as solved using the "thread tools" button near the top. This helps the community.  Good question, BTW.

---

### Post by Butthead on 2019-01-12
Thanks for all the searching help!  I really should save it for the next time I need to find something. CatKiller's Ctrl-H key press (for displaying hidden files and directories) did the trick though. :guitar:

Will mark the thread solved.  Thanks again to the both of you for the excellent help! ):P

BTW - (FYI ;) ), installing user made maps into sauerbraten appears to be a nightmare.  On a Cube2 help page I found somewhere, you have to use a convoluted script file you first have to modify with all the map info inputted into it to even get them to show up in the game.  Then, on top of all that, they might even turn out to be be lousy maps...:rolleyes:

---

### Post by TheFu on 2019-01-13
Yep. I don't use file managers much. They don't exist on servers.
To see "hidden" files, which isn't really what they are, they are just files that begin with a period, .something, use **ls -a**.  The fact that config files and directories aren't shown by default is really a convenience. Nothing more.  

If you really want to hide files, name a directory "..." and most people will never notice anything inside it.  Or you can put files inside a directory then mount a partition on top of that directory.  Nobody can see those files as long as the directory is mounted without using a data recovery tool on the disk device directly.  I'm sure there are other ways to hide files too.

---

### Post by Butthead on 2019-01-13
> **TheFu said:**
> Yep. I don't use file managers much. They don't exist on servers.
To see "hidden" files, which isn't really what they are, they are just files that begin with a period, .something, use **ls -a**.  The fact that config files and directories aren't shown by default is really a convenience. Nothing more.

My problem was I coudn't find the FOSSwire Linux command sheets I usually use.  Even though I doubt that the (K)Ubuntu "Ctrl+H" hidden file key combo was shown on it, I'm sure there was something on there useful to me that would have eventually allowed me to bring up those darn hidden sauerbraten files & directories. :-k    

> **TheFu said:**
> If you really want to hide files, name a directory "..." and most people will never notice anything inside it.  Or you can put files inside a directory then mount a partition on top of that directory.  Nobody can see those files as long as the directory is mounted without using a data recovery tool on the disk device directly.  I'm sure there are other ways to hide files too.

All you have to do with me if you want to keep something secret is to hide my FOSS cheat sheets on me.  If I fart around long enough with (K)Ubuntu, it'll probably end up with me having to do a complete system re-install anyway.  Can't get anymore file secure than that. :D;)

---

