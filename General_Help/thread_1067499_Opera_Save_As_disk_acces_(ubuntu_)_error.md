---
title: "Opera Save As disk acces (ubuntu ?) error"
date: 2009-02-11
forum: General Help
---

### Post by sirkubax on 2009-02-11
Hello, 
I'm not sure is it good place for this post, so if i put this in a wrong thread please correct me.

I have been searching for this error lot, but it is hard to find something...
I have following problem while using opera, and i suspect ubuntu "file manager"/"disk acces" to make a trouble.

When i'm using opera, and i want to save file on disk (image, movie, torrent, txt, etc. ...) I'm choosing "Save image as/ Save linked context as/ etc.." and then appears window to chose where i would like to save downloaded file (like "file manager") [picture 11.png]. And here is problem. Sometimes happen, that this window will not fully load. It just appear, but nothing is inside, or appear, but only "tree view of system disks/places" is loaded, but certain catalog/folder like Desktop or Home does not appear (i can not see the files inside this folder). In this moments mouse pointer is in "wait mode". I see in opera status bar, that file is being downloaded, but i can not chose place to save file, so after download finish, file is "lost". I can not move between tabs while "save as window hang up"(in this instance of opera), but if i have more than one opera windows open, i can still use second opera instance without any troubles.
Sometimes it happen that "file manager" window will load fully after few minutes (tree view and folder view displays it's content), and i can save file and use opera, but usually i have to kill opera process and start it again.
This save fail happens about 1/20 item saves.

Sometimes, even though &#8220;file manager&#8221; windows load ok, I can not  press save or cancel or &#8220;x&#8221; button,  and opera seems to be dead (only one instance of opera) [picture 12.png and 13.png]

I think that there is some problem with disk access in ubuntu, but i have no idea how to measure that. Can you tell me if there is some tool to track this error and debug it?

It is hard to find similar case in internet, but possible that  no-one knows how to describe this error (or is to lazy). Meaby i'm looking in wrong direction, but i have this problem for a long time, and if i remember well, it was also in 8.04 and with opera 9.52. 
My friend have the same trouble on his ubuntu 8.10, but he rarely save items to disk, so for him it is margin problem.
My other friend, who use Debian (will check with one later) had this error today, thats made me to write this post, because i believe it is not a single case.


In this moment i'm not looking for an answer what is wrong, but rather for a tip, how to log this error for further analysis. Or how to describe this in proper way, to make it "a bugs.launchpad.net post" possible to find for other users. 


My system
Ubuntu 8.10 (and 8.04 also if i remember well)
Opera 9.63

---

### Post by Menthu_Rae on 2009-05-09
Edit: I beleive I have found the cause of the bug, at least for me... sent this to Opera team:

> Just to follow up this bug, I have found what is causing the issue...

If you have samba shares mounted... and then shutdown the mount source (e.g. server)... then follow the actions specified in my bug report - then Opera "calls" (is this the right word?) smb_init... however, it waits for the timeout (I presume)...

It is interesting to note that Firefox does *not* exhibit this behaviour, even though it's on the same system and thus would be "effected" by the samba mount source having been shut down...

Could you please fix this somehow? It's annoying that firefox "works fine" but opera hangs/waits for a timeout when the samba share source is shutdown/disconnected...


--------- old post below ---------

I also have this problem, it's a royal pain in the ****... I suggest anyone who has this issue submit a bug report to the Opera team. :)

---

### Post by ellgor on 2009-05-09
Hi,

Not a fix but a tip, in (the Opera toolbar) >tools>preferences the box that appears chooose downloads, near the bottom is the location of the download folder (as specified by yourself) downloads all go to there and you can sort things out afterwards, hope this helps.

Regards, Ellgor.

---

