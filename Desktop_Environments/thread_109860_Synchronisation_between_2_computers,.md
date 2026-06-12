---
title: "Synchronisation between 2 computers,"
date: 2005-12-29
forum: Desktop Environments
---

### Post by geearf on 2005-12-29
Hello,

I have two computers running Ubuntu, and I would like to synchronise my mails (thunderbird profile), my firefox profile, and my music.

On windows, I was using Ultra Backup which was kinda slow, but doing that, now I'd like a linux program / script to do that but I cannot find much.

Thanks,

---

### Post by mlomker on 2005-12-29
You'll want to look into rsync.  It is similar to robocopy on Windows.

---

### Post by HermanAB on 2005-12-30
Here is something to read:
[http://www.aerospacesoftware.com/rsync-ssh-howto.html](http://www.aerospacesoftware.com/rsync-ssh-howto.html)

---

### Post by marks_linux on 2005-12-30
Or this thread, which worked for me.
[http://www.ubuntuforums.org/showthread.php?t=15082&highlight=dsa](http://www.ubuntuforums.org/showthread.php?t=15082&highlight=dsa)

---

### Post by geearf on 2005-12-30
Thank you guys, I'll look at that very soon and give you my comments on those 3 links.

---

### Post by geearf on 2005-12-30
Hello,

thank you it works perfectly, I still need to look at the man I think to get the best options, but thanks :)

Also would it be possible to do that without ssh ? (I have an nfs mount of the other comp on both computers, so it should be faster from there).

Thanks,

---

### Post by marks_linux on 2005-12-31
you can do the rsync without ssh if you want.

---

### Post by geearf on 2005-12-31
Hmm, I've looked around, it seems I can use something else yes, but not something as simple as sh or bash.
Well, I'm not quite sure I need that encryption thing to transfer files in my network, I'll look around thanks.

---

### Post by hbj on 2005-12-31
I use unison to sync files between my laptop and desktop when I travel and it works great: [http://www.cis.upenn.edu/~bcpierce/unison/]("http://www.cis.upenn.edu/~bcpierce/unison/")

From the unison webpage: > **What are the differences between Unison and rsync?**
Rsync is a mirroring tool; Unison is a synchronizer. That is, rsync needs to be told ``this replica contains the true versions of all the files; please make the other replica look exactly the same.'' Unison is capable of recognizing updates in both replicas and deciding which way they should be propagated.

Both Unison and rsync use the so-called ``rsync algorithm,'' by Andrew Tridgell and Paul Mackerras, for performing updates. This algorithm streamlines updates in small parts of large files by transferring only the parts that have changed. 
```
sudo apt-get install unison unison-gtk
```
unison-gtk is a nice GUI for configuring and running unison.

---

### Post by geearf on 2005-12-31
Hello,

thanks for the post, I'll have a look at unison.

---

### Post by geearf on 2006-01-01
Hello,

A-I'm encoutering some problems with rysnc :
1- with "rsync -e ssh -zvuPlptgoD --delete /home/gee/dir/*.* gee.local:/home/gee/dir/" the delete does not work, but it would wit -r, but I do not want to synchronise every dir inside the first one, and with just "/" nothing happens ..

2- I can start the script on both comps, and they will still send files, even if they should have the same versions (same output from ls -l at least).

B- I'm look at unison-gtk right now, but it takes time to analyse my files :)

---

### Post by burningbed on 2006-01-02
The first time you run Unison, it'll take a while to analyze all the files you need to synchronize, but after this first run it is fast. I use it a lot to keep my laptop and desktop synchronized and can highly recommend it (there are also versions for Windows and Mac, if you want to synchronize files on computers running different operating systems).

---

### Post by geearf on 2006-01-03
Hello,

I cannot find much options for unison-gtk for the moment.

I want to synchronise a dir, but in a non-recursive way and I have not yet found how, but I'll look at this later.

---

### Post by burningbed on 2006-01-03
I know from the documentation that there are a lot of ways to configure synchronization / backup in unison and would, but so far have not had to tweak the configuration file myself yet. If you want a permanent solution that will work even if you add new directories that you don't want to synchronize you'll have to look through the documentation to find out how to do it. If you just want to exclude a few paths, there's an "Ignore" menu with the entry "Permanently ignore this path" that should do the trick. And of course you can always skip paths and files by hand in the selection screen.

---

