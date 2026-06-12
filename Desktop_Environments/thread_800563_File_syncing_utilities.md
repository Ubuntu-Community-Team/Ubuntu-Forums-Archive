---
title: "File syncing utilities"
date: 2008-05-19
forum: Desktop Environments
---

### Post by jtibau on 2008-05-19
I'm looking for a file syncing utility to use (don't mind if it is cli/gui). I own a nokia n800 so I'm carrying around my important files in an 8GB SDHC card and also have a backup in my laptop...
One big problem is that I usually modify things in the laptop as well... So you wouldn't really call it a backup, right? I can't just erase everything in the laptop and replace it with the current contents of my SDHC card, and I certainly don't trust myself to remember each change I do in either...
So, does anyone know any easy/automatic file syncing utilities??? I'm interested in pretty much anything...

---

### Post by sdennie on 2008-05-20
I don't know of any simple ways to keep versions of files in sync across machines without using some sort of source control management (though, I admit that I didn't look very hard).  If no one can give you a simpler method, you may want to look for a tutorial on how to setup subversion server on your main machine.

---

### Post by jtibau on 2008-05-20
ah yes, I expected this... I have looked around but haven't found many tools either.
I can't speak for all of the tools, but I have a little experience with CVS. CVS is probably not the way to go to solve this problem because:
- You have to tell the server about EACH file you want it to keep track of.
- Moving folders is a pain
- It's 6am, I can't think anymore just yet :)
Anyway, I don't know much about SVN, bzr, git. But it seems to me that it would be rather complicated to use one of these tools...

---

### Post by sdennie on 2008-05-20
Syncing files across multiple machines is a very hard problem.  It's less hard if all the files are text files (and REALLY hard if they aren't).  Depending on how you edit files, something like subversion or CVS might be overkill or annoying enough that it's not worth it.  You could probably write a script that informs you of new files, modified files, deleted files, etc. and prompts you what you'd like to do about that when the two machines connect.  There may be an elegant solution on Ubuntu but, I'm not aware of it.

(Though you aren't in Quito, I'd also like to inform you that San Lorenzo is going to destroy that feeble Ecuadorean team on Thursday in the Copa)

---

### Post by dccrens on 2008-05-20
Suggest looking at "rsync". It will do wonders. Search rsync in these forums (there are many examples.)

---

### Post by galileon on 2008-05-20
rsync, unison-gtk, conduit, take your pick!

---

### Post by jtibau on 2008-05-20
> **vor said:**
> 
(Though you aren't in Quito, I'd also like to inform you that San Lorenzo is going to destroy that feeble Ecuadorean team on Thursday in the Copa)
haha, I don't follow soccer, sorry...

---

### Post by jtibau on 2008-05-20
> **galileon said:**
> rsync, unison-gtk, conduit, take your pick!

I haven't used rsync, and I had heard about unison... I will take a look at them and report if I can.

---

### Post by jtibau on 2008-05-22
> **vor said:**
> (Though you aren't in Quito, I'd also like to inform you that San Lorenzo is going to destroy that feeble Ecuadorean team on Thursday in the Copa)

I just couldn't let this go!!! I just watched the match and San Lorenzo sucked so bad...

---

### Post by sdennie on 2008-05-22
> **jtibau said:**
> I just couldn't let this go!!! I just watched the match and San Lorenzo sucked so bad...

My shame knows no bounds.  I blame it on the altitude.  Reasonable people don't live that high.  ;)

Saludos

---

