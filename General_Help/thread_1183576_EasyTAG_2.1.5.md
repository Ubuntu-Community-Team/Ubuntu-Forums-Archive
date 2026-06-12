---
title: "EasyTAG 2.1.5"
date: 2009-06-10
forum: General Help
---

### Post by demonoidmaster on 2009-06-10
Ok, So I've Got This Annoying Problem In EasyTAG.

When Searching For Album Tracks Info, In **" Manual Search** "... I Search An Artist (Or Album) And It Finds It... But As Soon As I Click It To Show Its Track List It Says This Error At The Bottom Of The Screen

**The Server Returned A Wrong Answer! (HTTP/1.1 301 Moved Permanently)**

Any Ideas ???



°°~DemonoidMaster~°°

---

### Post by demonoidmaster on 2009-06-10
~Bump~

---

### Post by pmlxuser on 2009-06-10
sorry but it means the program is not able to display your querry which eould be as a result of a script error. Have you tried reinstalling the program. completely remove it and re-install it or submit it as a bug.

i would also try to use another program for doing the same task.. Like Audio tag something like that..

---

### Post by sonicb00m on 2009-06-10
are you serious? do you think this is some kind of realtime help desk support for your problems?

---

### Post by frodon on 2009-06-10
Fast bump tactic => thread locked fo 24h

---

### Post by Piraja on 2009-08-26
Well, let me bump this for a change. This problem has bugged EasyTAG users for several years now, as it seems. I just upgraded to 2.1.5 (easytag-aac in Synaptic) and the database search is still not functioning properly. 

Any suggestions for an alternative GUI tag editor?

---

### Post by kpkeerthi on 2009-08-26
> **demonoidmaster said:**
> 
When Searching For Album Tracks Info, In **" Manual Search** "... I Search An Artist (Or Album) And It Finds It... But As Soon As I Click It To Show Its Track List It Says This Error At The Bottom Of The Screen

**The Server Returned A Wrong Answer! (HTTP/1.1 301 Moved Permanently)**


Its probably trying to connect to cddb. Switch to [http://www.freedb.org/](http://www.freedb.org/) (there should be a setting somewhere in the Easytag Preference)

---

### Post by Piraja on 2009-08-26
> **kpkeerthi said:**
> Its probably trying to connect to cddb. Switch to [http://www.freedb.org/](http://www.freedb.org/) (there should be a setting somewhere in the Easytag Preference)
Sorry, but I don't think this helps. The default options in EasyTAG's preferences are freedb and gnudb.

---

### Post by thedaylights on 2009-11-23
There is a patch for EasyTAG 2.1.6 which solves this problem:
[http://sourceforge.net/projects/easytag/files/easytag%20unstable%20%28gtk%202%29/2.1.6/patch_easytag_216_cddb_manual_search_fix.diff/download](http://sourceforge.net/projects/easytag/files/easytag%20unstable%20%28gtk%202%29/2.1.6/patch_easytag_216_cddb_manual_search_fix.diff/download)

However, I do not know how to apply a patch. Can someone walk me through this please?

---

### Post by algoban on 2010-02-11
> **thedaylights said:**
> There is a patch for EasyTAG 2.1.6 which solves this problem:
[http://sourceforge.net/projects/easytag/files/easytag%20unstable%20%28gtk%202%29/2.1.6/patch_easytag_216_cddb_manual_search_fix.diff/download](http://sourceforge.net/projects/easytag/files/easytag%20unstable%20%28gtk%202%29/2.1.6/patch_easytag_216_cddb_manual_search_fix.diff/download)

However, I do not know how to apply a patch. Can someone walk me through this please?

Ok thanks for the patch file i wasnt found it. 

Ok to apply the patch u have to compile EasyTag 2.1.6 (I think is the only way). Download  the patch and the easytag tarball from souceforge. Then extract the tarball in a folder and apply the patch with:

```
patch < patch_easytag_216_cddb_manual_search_fix.diff

```

This will ask u about the file to patch. You have to search for "cddb.c" file, that is for example:
/home/user/easytag-2.1.6/src/cddb.c

Then u can compile. To compile you need the followings packages:

```
sudo apt-get install build-essential libglib2.0-dev libgtk2.0-dev libmp4v2-dev libflac-dev libmp3splt-dev 
``` 

After the install you can remove all this packages

Then u can look the install file to follow the instructions.

That is all 
Sorry for my english (u can correct me if u want)
Al

---

