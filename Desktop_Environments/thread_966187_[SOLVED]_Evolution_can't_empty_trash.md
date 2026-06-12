---
title: "[SOLVED] Evolution can't empty trash"
date: 2008-11-01
forum: Desktop Environments
---

### Post by erlguta on 2008-11-01
Since i am in intrepid i notice that i can't empty the trash..
I have 10 messages and if i click empty trash nothing happens.
I tried too to set empty when evolution closes, but nothing again.
What can i do?

Thank you.

---

### Post by craig564 on 2008-11-01
> **erlguta said:**
> Since i am in intrepid i notice that i can't empty the trash..
I have 10 messages and if i click empty trash nothing happens.
I tried too to set empty when evolution closes, but nothing again.
What can i do?

Thank you.

I had this same problem and here is how I fixed it. 
Close Evolution and open your file browser. 
Go to /home/put-your-ubuntu-login-name-here/.evolution/mail/local
There are 2 files (Junk.cmeta and Trash.cmeta). 
I deleted the Trash.cmeta file and opened Evolution again.
When you reopen Evolution, it creates a new Trash.cmeta file.
I deleted some more messages and was now able to empty the trash.
Craig

---

### Post by deniswal on 2008-11-02
I have the same problem:

After migrating to Intrepid Ibex the backend storage of evolution changed.

I now am not able to empty the Trash folder.

This is not solved by your procedure.

Denis

---

### Post by DChamp on 2008-11-13
Same problem here. Since updating, the trash will not empty in any way.

Tried the fix above, did not fix the problem.
Any help would be appreciated.

---

### Post by DChamp on 2008-11-13
Found the answer here:

[http://ubuntuforums.org/showthread.php?t=974536](http://ubuntuforums.org/showthread.php?t=974536)

---

### Post by TheRingmaster on 2008-11-17
I have a similar problem, I have evolution set to empty trash on exit and yet it does not. I have to right click on the trash folder to the left and manually empty the trash. 

I've yet to see a real answer to the problem.

---

### Post by erlguta on 2008-11-18
> **DChamp said:**
> Found the answer here:

[http://ubuntuforums.org/showthread.php?t=974536](http://ubuntuforums.org/showthread.php?t=974536)

Thank you it solved my problem.

---

### Post by wutti on 2008-11-21
I have tried all the methods listed above but it crashes when I empty trash. There are no debug messages other than "segmentation fault"....

I can not clean out my trash!

---

### Post by nrayever on 2010-08-21
> **craig564 said:**
> I had this same problem and here is how I fixed it. 
Close Evolution and open your file browser. 
Go to /home/put-your-ubuntu-login-name-here/.evolution/mail/local
There are 2 files (Junk.cmeta and Trash.cmeta). 
I deleted the Trash.cmeta file and opened Evolution again.
When you reopen Evolution, it creates a new Trash.cmeta file.
I deleted some more messages and was now able to empty the trash.
Craig

Thanks Craig, great way to solve this issue. Hope doesn't happend to me again.

Regards, nrayever.

---

### Post by gsnoorky on 2011-08-12
Evolution has changed and these cmeta files appear not to exist any longer. ("folders.db" is the only file which appears). I get this message, now: "Error while expunging folder '.#evolution/trash'.... I had to use "root terminal" to see the "local" folder--nautilus doesn't seem  to cut it. Recklessly, I deleted folders.db--nothing happened. I'm considering uninstalling evolution, then reinstalling....

This problem often pops up, stupidly, in this otherwise intelligent program. Why not delete the trash folder, then immediately afterwards recreate a new folder? What's so hard about that? When I desire to delete the trash, I'm committed and accept any consequences. (Really, I'm OK with deleting inbox messages directly.) It seems that the developers believe that the trash is worth "synchronizing"--I don't get it....:confused: 

Thanks! Already, we need a new solution....

---

### Post by Arthur King on 2011-08-29
The solution proposed by Divine Amoeba
[URL="http://ubuntuforums.org/showthread.php?t=974536"]
still works in Lucid, but you need to repeat it every time you want to empty the trash.

---

### Post by frogotronic on 2011-12-14
> **craig564 said:**
> I had this same problem and here is how I fixed it. 
Close Evolution and open your file browser. 
Go to /home/put-your-ubuntu-login-name-here/.evolution/mail/local
There are 2 files (Junk.cmeta and Trash.cmeta). 
I deleted the Trash.cmeta file and opened Evolution again.
When you reopen Evolution, it creates a new Trash.cmeta file.
I deleted some more messages and was now able to empty the trash.
Craig

This worked for me on Maverick Meerkat.

- CH   :popcorn:

---

