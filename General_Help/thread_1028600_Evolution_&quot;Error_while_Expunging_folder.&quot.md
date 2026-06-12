---
title: "Evolution: &quot;Error while Expunging folder.&quot;"
date: 2009-01-02
forum: General Help
---

### Post by nwu on 2009-01-02
I'm using Evolution 2.24.2 on Ubuntu 8.10, and recently have found that there are (just a few) e-mails in my Trash folder that can't be deleted; when I try to do so I just get "Error while Expunging folder." I've looked up this error in a few places online, which recommended deleting some files in ~/.evolution/mail/local, but the e-mails still refuse to be deleted. Any ideas?

Thanks.

---

### Post by dcstar on 2009-01-02
> **nwu said:**
> I'm using Evolution 2.24.2 on Ubuntu 8.10, and recently have found that there are (just a few) e-mails in my Trash folder that can't be deleted; when I try to do so I just get "Error while Expunging folder." I've looked up this error in a few places online, which recommended deleting some files in ~/.evolution/mail/local, but the e-mails still refuse to be deleted. Any ideas?


I can only suggest you have a look in your .evolution folders and see if any files have strange permissions.

---

### Post by jeremybar on 2009-03-18
I am using Evolution 2.24.3 with local mail fetching from gmail with POP3, and was faced with the same problem.

I found that the following script fixed things a bit by cleaning up old or corrupt index files.

Before running this script, don't forget to perform a backup of ~/.evolution directory.

After running the script, run evolution, and be patient while it re-creates all the mail indexes.

```

#!/bin/bash
export LANG=C
set -e
evolution --force-shutdown
tar -zcf dot_evolution_$$.tgz ~/.evolution/
for each in index data cmeta; do
 find ~/.evolution/mail/local -type f -iname "*.$each" | while read f; do rm -f "$f"; done
done
rm ~/.evolution/mail/local/folders.db

```

Let us know if it helps.

This should work with spaces in the mailbox names.
Jeremy

---

### Post by paulchinnz on 2009-03-27
Thanks jeremybar.

Got stuck here:
```
root@Thermopylae:/home/paulchinnz# tar -zcf dot_evolution_$$.tgz ~/.evolution/
tar: Removing leading `/' from member names
tar: /root/.evolution: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors
root@Thermopylae:/home/paulchinnz# tar -zcf dot_evolution_$$.tgz ~/.evolution/
```

What happened?

---

### Post by jeremybar on 2009-03-27
You have to edit a file and paste this code in it.  Then you can run it.

Also, you shouldn't run this as root, only as your user name.

---

### Post by paulchinnz on 2009-03-27
Cheers, that seemed to do the trick

---

### Post by habtool on 2009-05-07
> **jeremybar said:**
> I am using Evolution 2.24.3 with local mail fetching from gmail with POP3, and was faced with the same problem.

I found that the following script fixed things a bit by cleaning up old or corrupt index files.

Before running this script, don't forget to perform a backup of ~/.evolution directory.

After running the script, run evolution, and be patient while it re-creates all the mail indexes.

```


#!/bin/bash
export LANG=C
set -e
evolution --force-shutdown
tar -zcf dot_evolution_$$.tgz ~/.evolution/
for each in index data cmeta; do
 find ~/.evolution/mail/local -type f -iname "*.$each" | xargs rm
done
rm ~/.evolution/mail/local/folders.db


```

Let us know if it helps.

Jeremy

Thanks, that worked perfectly :)

---

### Post by crosslink on 2009-05-11
I had same issue (in Jaunty), and the script solved it. Thank you!

---

### Post by damianpeterson on 2009-06-22
I found that simply renaming ~/.evolution/mail/local/folders.db fixed the same issue. I later deleted the newly renamed file as Evolution recreated this the next time I launched it.

---

### Post by HyRax on 2009-07-01
> **damianpeterson said:**
> I found that simply renaming ~/.evolution/mail/local/folders.db fixed the same issue. I later deleted the newly renamed file as Evolution recreated this the next time I launched it.

Deleting that one file worked brilliantly for me on my Jaunty setup! When restarting Evolution there's a short delay as it rebuilds that file, and my expunging error was gone - could empty trash without any issue. Cheers!

---

### Post by paulchinnz on 2009-08-23
I had to use this when I made a 5th generation (not sure of right word for this) folder and all the emails in it disappeared. That's by the way, but interesting that renaming folders.db not only fixed the problem but returned me some HDD space (in this case 6.6Mb down to 240Kb on the recreated folders.db file).

---

### Post by kauboy on 2009-10-29
**Renaming ~/.evolution/mail/local/folders.db** (to newbies: ~ means /home/YourUsername and "View->Show Hidden Files" in file browser unhides the .evolution hidden folder in your ~ folder) and **restarting Evolution** did the trick!!

And it seems to be a bit zippier too! The older (now renamed) file was much larger (4MB), compared to the newly created one (50KB). Thanks to damianpeterson :D

---

### Post by Mini_Piddy on 2009-11-11
Brilliant! Had about 400 emails in my deleted items folder! Thank you! :p

---

### Post by Skip Da Shu on 2009-11-30
> **jeremybar said:**
> I am using Evolution 2.24.3 with local mail fetching from gmail with POP3, and was faced with the same problem.

I found that the following script fixed things a bit by cleaning up old or corrupt index files.

Before running this script, don't forget to perform a backup of ~/.evolution directory.

After running the script, run evolution, and be patient while it re-creates all the mail indexes.

```


#!/bin/bash
export LANG=C
set -e
evolution --force-shutdown
tar -zcf dot_evolution_$$.tgz ~/.evolution/
for each in index data cmeta; do
 find ~/.evolution/mail/local -type f -iname "*.$each" | xargs rm
done
rm ~/.evolution/mail/local/folders.db


```

Let us know if it helps.

Jeremy

EXCELLENT!  I was getting the error on both inbox and sent and couldn't delete 1 gazillion things from Trash.  Worked 1st time out.

When can u start my private bash classes?  ;-)

Thanx much,
Skip

---

### Post by clflyer on 2010-02-01
> **jeremybar said:**
> I am using Evolution 2.24.3 with local mail fetching from gmail with POP3, and was faced with the same problem.

I found that the following script fixed things a bit by cleaning up old or corrupt index files.

Before running this script, don't forget to perform a backup of ~/.evolution directory.

After running the script, run evolution, and be patient while it re-creates all the mail indexes.

```


#!/bin/bash
export LANG=C
set -e
evolution --force-shutdown
tar -zcf dot_evolution_$$.tgz ~/.evolution/
for each in index data cmeta; do
 find ~/.evolution/mail/local -type f -iname "*.$each" | xargs rm
done
rm ~/.evolution/mail/local/folders.db


```

Let us know if it helps.

Jeremy

Jeremy,
this worked great with my system. All I had to do was change permissions to 777
Thanks,
Bill:D

---

### Post by rkevinbrown on 2010-02-02
Thank everyone.  Had same problem and renaming ~/.evolution/mail/local/folders.db worked perfectly.

---

### Post by fonsi2099 on 2010-02-10
Again thank everyone. I had same problem and renaming ~/.evolution/mail/local/folders.db worked perfectly for me!!!!

---

### Post by vigyani on 2010-02-12
> **damianpeterson said:**
> I found that simply renaming ~/.evolution/mail/local/folders.db fixed the same issue. I later deleted the newly renamed file as Evolution recreated this the next time I launched it.


This worked for me on Karmic Kola 9.10, as well.

---

### Post by r m h on 2010-02-13
Jeremy - 

Thanks for your script.  Can I make a suggestion to enhance it?

piping your find command to xargs works great until there is a file found that has embedded spaces in it.

For example if the find command returns
file name.index
then xargs rm tries to 
rm file
rm name.index

A fix for this condition would be to use the following syntax:
replace
find ~/.evolution/mail/local -type f -iname "*.$each" | xargs rm
with
find ~/.evolution/mail/local -type f -iname "*.$each" -exec rm {} \;

---

### Post by drpjkurian on 2010-03-05
Hi Jeremy
Thank you very much for your wonderful script, It solved our problem in Evolution mail

---

### Post by dschof on 2010-03-28
Had this problem in Karmic (temporarily solved by deleting files as other threads suggested) but then Lucid (Beta) was hanging when "sending and receiving" - this script "seems" to have solved that problem too.

Incidentally, would anyone know if I created the problem by copying across from one "home" partition to another, maybe?

Thanks for the help, David

---

### Post by opm595 on 2010-05-30
Champion Stuff! 

> #!/bin/bash
export LANG=C
set -e
evolution --force-shutdown
tar -zcf dot_evolution_$$.tgz ~/.evolution/
for each in index data cmeta; do
 find ~/.evolution/mail/local -type f -iname "*.$each" | xargs rm
done
rm ~/.evolution/mail/local/folders.db

Worked a treat - Thanks!

---

### Post by Phillip Spencer on 2010-06-19
> **damianpeterson said:**
> I found that simply renaming ~/.evolution/mail/local/folders.db fixed the same issue. I later deleted the newly renamed file as Evolution recreated this the next time I launched it.

Thanks! Worked a treat in Karmic and has made a huge difference to the size of Evolution file.
Cheers
Phillip

---

### Post by David_Melb on 2010-06-20
> **HyRax said:**
> Deleting that one file worked brilliantly for me on my Jaunty setup! When restarting Evolution there's a short delay as it rebuilds that file, and my expunging error was gone - could empty trash without any issue. Cheers!

HyRax Great solution. I am using 9.10  + Evolution 2.28.1. I had the problem of not being able to delete files in the in box and emptying the trash bin. Had the dreaded expunge error.  I also had a problem that every time I opened the email and did a send and receive the files would be duplicated again.   If I hit the delete key the messages would have the line through them but would not delete.  Error alarm send expunge arror.  I moved the folder.db to folder.db.old and restarted Evolution and it rebuilt the folder list and all working well.

Thanks

---

### Post by Swagman on 2010-08-15
Just renamed  folders.db in Lucid

Sorted.

Thanks.

---

### Post by Z06Gal on 2010-08-15
Guys, help me understand what you are saying.  I just installed Evolution and set it up last night.  I do not have a "deleted" folder but when I delete an email it goes directly to trash.  I do not seem to have a problem deleting trash at this point.  I am using Lucid.  I see the evolution folder in my home directory via checking show hidden files but I haven't done anything to it.  I am relatively new to linux but am learning so I want to make sure I understand.  If you are showing a deleted folder then I need to fix that.  Thanks for your patience with us newbies. 


Robin :KS

---

### Post by Swagman on 2010-08-15
By your description you are not suffering the "Error expunging folder" dilemma when you empty the trash,  therefore you don't have a problem.

If/when this happens to you then you can refer to this thread to help you out.

You have grasped the basic gist of what is going on by showing hidden folders. There is a sub folder that contains a **FILE** called folders.db

That's the **FILE** that should be renamed (BAKfolders.db) until you are sure everything is hunky dory. You can then delete that file.

Make sure you are **NOT** running Evolution when you do all  this though.

As I said.... You don't have an issue atm so......

**Enjoy**

:D

---

### Post by Z06Gal on 2010-08-15
> **Swagman said:**
> By your description you are not suffering the "Error expunging folder" dilemma when you empty the trash,  therefore you don't have a problem.

If/when this happens to you then you can refer to this thread to help you out.

You have grasped the basic gist of what is going on by showing hidden folders. There is a sub folder that contains a **FILE** called folders.db

That's the **FILE** that should be renamed (BAKfolders.db) until you are sure everything is hunky dory. You can then delete that file.

Make sure you are **NOT** running Evolution when you do all  this though.

As I said.... You don't have an issue atm so......

**Enjoy**

:D


Excellent.  Thank you. :D

---

### Post by sieward on 2010-12-25
Goto Edit-Preferences-Mail preferences and check "empty trash folders on exit" and close evolution.
Trash folder  is empty next time Evolution is opened

---

### Post by warfie on 2011-06-13
> **jeremybar said:**
> I am using Evolution 2.24.3 with local mail fetching from gmail with POP3, and was faced with the same problem.

I found that the following script fixed things a bit by cleaning up old or corrupt index files.

Before running this script, don't forget to perform a backup of ~/.evolution directory.

After running the script, run evolution, and be patient while it re-creates all the mail indexes.

```


#!/bin/bash
export LANG=C
set -e
evolution --force-shutdown
tar -zcf dot_evolution_$$.tgz ~/.evolution/
for each in index data cmeta; do
 find ~/.evolution/mail/local -type f -iname "*.$each" | xargs rm
done
rm ~/.evolution/mail/local/folders.db


```

Let us know if it helps.

Jeremy

That worked perfectly, thank you!

---

### Post by wmccarty on 2011-12-16
The procedure worked, sort of.

For those who have problems running the script because RM would error out saying that it could not find the directory or file..

In my directories in evolution there are spaces in many of the folder names

** a bit of caution should be exercised when rm is used to delete files

I ended up having to do the manual steps as implied by that script by doing the following
-Backup the settings by using the "Backup Settings" in evolution
-Run the kill evolution command
```
evolution --force-shutdown
```-Locate each type of file
```
locate *.cmeta
locate *.ibex.index*
```-paste all the results into a text file on the desktop or where-ever call it "test.sh"
ignore lines that are not in your "~/.evolution/mail/local" folder
-Insert the following in front of each line
```
rm -f "
```-Insert a close quote at the end of each line 
```
"
```You should now have a bunch of lines that look like
```
rm -f "/home/yourusername/.evolution/mail/local/Inbox.sbd/Folder Example.sbd/Hotmail.cmeta"
```-delete the folders.db in the local folder by
```
rm ~/.evolution/mail/local/folders.db
```-Then run your little manual rm script
```
sh ./test.sh
```-Restart Evolution

I still am not good with scripting so if anyone can rewrite the script to accommodate spaces in the directories then please have at it.

I can now use the evolution delete command and my folders are no longer all wonky!

---

### Post by jeremybar on 2011-12-16
> **wmccarty said:**
> The procedure worked, sort of.

For those who have problems running the script because RM would error out saying that it could not find the directory or file..

In my directories in evolution there are spaces in many of the folder names


Thank you for your reply, I have updated my script to support spaces in the name of the mailbox.  See my comment number 3.

---

