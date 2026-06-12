---
title: "How to delete multiple files / remove apps?"
date: 2005-02-04
forum: Desktop Environments
---

### Post by egg on 2005-02-04
Hi, 

so I tried installing mldonkey via apt-get... but didn't like the way it installed files everywhere.. so was wanting to try and do it manually.

I've unistalled the app via the applications gui ... but there's still lots of mldonkey files everywhere, visible when i do a search.

How can I delete these files easily?

I thought I could select them from the search box, drag them into a root terminal with sudo rm -r ... etc etc... but that didn't work. Complained of access rights etc.

please help! my disk is a mess and i've only installed 2 days ago!!  :oops:

---

### Post by kdavison007 on 2005-02-04
I normally do a "whereis applicationname" on the CLI to find out what might be left over after removing an app with apt-get or dpkg.  You can also use the find command to look for stuff.  "sudo find / filetosearchfor"  

I'm trying to think of a way to delete across directories.  I suppose if you were at / you could use sudo rm -r mldonk* and see what happens.  You'll want to be careful when using -r though because it will start working down all of your directories.

---

### Post by Marquis_de_Carabas on 2005-02-04
If you installed it via apt-get then couldn't you uninstall it simply via "apt-get remove"? As far as I know this should delete everything that was installed.

Also, how are you searching? If you're using "locate" then remember to update your database ("sudo updatedb") after making any changes (such as removing files) otherwise you'll be seeing files that are no longer there!

---

### Post by egg on 2005-02-05
thanks for the feedback guys.

As a noob, im a bit shocked that an installation puts so many files all over the place - is this normal?

And, for example.. the main mldonkley files got dumped into /usr/bin.... and not in there own directory. When the probgram runs, it creates even more files in there.

Is that normal!? what a mess :-)

---

### Post by Marquis_de_Carabas on 2005-02-05
[QUOTE=egg]thanks for the feedback guys.

As a noob, im a bit shocked that an installation puts so many files all over the place - is this normal?

And, for example.. the main mldonkley files got dumped into /usr/bin.... and not in there own directory. When the probgram runs, it creates even more files in there.

Is that normal!? what a mess :-)[/QUOTE]

'Tis the Unix way, my friend :) 

Although it takes a little getting used to for those coming from a DOS/Windows background (i.e. most of us) it does actually make a lot of sense, and is far more usable in many respects. For instance, if I want to play Unreal Tournament I only have to issue the command "ut2004" - all program binaries are kept in the same place so the system knows exactly where to look - rather than navigate to c:\games\unreal tournament and *then* type "ut2004". Just typing "man gimp" or "info gimp" will bring up tons of information on the Gimp; all the man files for every program are in the same place, so the system knows exactly where to look.

Once you get used to it it's no harder to use than the Windows way. Removing a program you've compiled yourself can sometimes be a pain, but even that doesn't take too long using "locate" and "rm -r".

There's a basic comparison of Unix and Windows filesystems [here](http://status.lsu.edu/start/2002/01/#filesystem).

By the way, installing mldonkey from source will still put the files "all over the place". For the most part you're better off sticking with "apt-get" as it makes managing all those files far easier (that's what it's there for!).

---

### Post by cacofonix on 2005-02-05
I use dpkg --purge (program name) and that usually gets rid of the left over files. 

cacofonix

---

### Post by egg on 2005-02-05
> **Marquis_de_Carabas]'Tis the Unix way, my friend :) 

Although it takes a little getting used to for those coming from a DOS/Windows background (i.e. most of us) it does actually make a lot of sense, and is far more usable in many respects. For instance, if I want to play Unreal Tournament I only have to issue the command "ut2004" - all program binaries are kept in the same place so the system knows exactly where to look - rather than navigate to c:\games\unreal tournament and *then* type "ut2004". Just typing "man gimp" or "info gimp" will bring up tons of information on the Gimp said:**
> here[/URL].

By the way, installing mldonkey from source will still put the files "all over the place". For the most part you're better off sticking with "apt-get" as it makes managing all those files far easier (that's what it's there for!).

thanks for this! and the link.... starting to make a little more sense now :-)

---

