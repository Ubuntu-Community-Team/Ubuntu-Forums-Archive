---
title: "Moving mail folders in Thunderbird"
date: 2005-09-04
forum: Desktop Environments
---

### Post by Quirky on 2005-09-04
I have Thunderbird set up with filters to move mail to different places (e.g. job offers to one folder, mailing list items to another). I have about 7 or 8 folders, and decided to add a subfolder and move the less-read folders into that. So I added a new folder called 'semi-spam' into which I moved my job offers folder by dragging and dropping - all went well, TB informs me that it will update my filters.

I then tried moving another folder 'shopping' (containing special offers from websites I shop at regularly) into the semi-spam folder. Nothing happens. The folder just stays where it is. Nothing I do lets me move the second folder. I restart Thunderbird and wtf? I now have 2 shopping folders! One in semi-spam and one in the original position. The 'new' folder in the sub folder is just a copy. The filters still point at the original folder. Has anyone else experinced this odd behaviour? I think it's a bug that only seems to let you move 1 folder after starting Thunderbird before things go tits up, perhaps gnome d'n'd is getting it in a muddle, but I don't want to file a bug report in case it's 'nominal behaviour'. Ubuntu 5.04 Hoary, Thunderbird version 1.0.6 (20050727) by the way.

---

### Post by essexman on 2005-09-04
[QUOTE=Quirky]I have Thunderbird set up with filters to move mail to different places (e.g. job offers to one folder, mailing list items to another). I have about 7 or 8 folders, and decided to add a subfolder and move the less-read folders into that. So I added a new folder called 'semi-spam' into which I moved my job offers folder by dragging and dropping - all went well, TB informs me that it will update my filters.

I then tried moving another folder 'shopping' (containing special offers from websites I shop at regularly) into the semi-spam folder. Nothing happens. The folder just stays where it is. Nothing I do lets me move the second folder. I restart Thunderbird and wtf? I now have 2 shopping folders! One in semi-spam and one in the original position. The 'new' folder in the sub folder is just a copy. The filters still point at the original folder. Has anyone else experinced this odd behaviour? I think it's a bug that only seems to let you move 1 folder after starting Thunderbird before things go tits up, perhaps gnome d'n'd is getting it in a muddle, but I don't want to file a bug report in case it's 'nominal behaviour'. Ubuntu 5.04 Hoary, Thunderbird version 1.0.6 (20050727) by the way.[/QUOTE]

I can't get the problem to repeat on my system.  It may be permissions. try: ```
sudo chown -R username:username /home/path to thunderbird mail folder/*
```. 
 The other thing that might work is reposting with something like: > Moving folders within Thunderbird Local folders wich may catch the eye of someone who has had the same problem.  I see that a few people have looked at this post, and not replied.

---

### Post by Quirky on 2005-09-04
No, it isn't a problem with permissions. It actually works occasionally. Most of the time it just makes a copy of the folder in the sub folder. Perhaps I should be clearer in the steps:

1. create inbox->folder1
2. create inbox->subfolder
3. drag inbox->folder1 to inbox->subfolder

Expected result: folder1 is now inside subfolder with any filters updated. 
Actual result: "nothing" happens. Restarting TB shows a copy of folder1 in subfolder, the original folder1 is still a peer of subfolder.

Worse is that this only happens occasionally. Sometimes the folder is moved as expected.

---

