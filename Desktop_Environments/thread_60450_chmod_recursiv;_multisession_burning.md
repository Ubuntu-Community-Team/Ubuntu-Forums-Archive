---
title: "chmod recursiv; multisession burning"
date: 2005-08-27
forum: Desktop Environments
---

### Post by mat69 on 2005-08-27
First of all I want to thank you all for Ubuntu!
Second thing is that I came across a few things which need improvement imho.

One of that is that there should be an option to recursively change the rights of some folders. I mean it should be like Win XP or KDE. You select a folder press the right mouse button go to options change the rights and now select the option to change the rights for subfolders and the files in those folders too. Just a simple checkbox.
Another thing is that gnome-burn should support multisessions. Imagine someone burning backups of his important files. Some documents with around 20 mb. It would be a waste of money and resources to utilize a disk for each backup you do. Normally you would create mulitsessions. Just adding a folder named by the date of the backup each time you create one.

So please add those features.
I know some people (including me for the second suggestion, but I couldn't find the thread ;) ) have asked for them before, but anyway can you point me to the right direction where these suggestions will be recognised?
Thank you in advance.

Matthias

---

### Post by professor_chaos on 2005-08-27
[QUOTE=mat69]First of all I want to thank you all for Ubuntu!
Second thing is that I came across a few things which need improvement imho.

One of that is that there should be an option to recursively change the rights of some folders. I mean it should be like Win XP or KDE. You select a folder press the right mouse button go to options change the rights and now select the option to change the rights for subfolders and the files in those folders too. Just a simple checkbox.[/QUOTE]

You can do this from the command line. ```
 chmod -R 777 
```

> 
Another thing is that gnome-burn should support multisessions. Imagine someone burning backups of his important files. Some documents with around 20 mb. It would be a waste of money and resources to utilize a disk for each backup you do. Normally you would create mulitsessions. Just adding a folder named by the date of the backup each time you create one.

Although I haven't tried it. K3B has this option.
I aggree though, that it would be nice for the nautilus burner to do this, but for me it's only important for some app to preform the function I need. K3b fits the bill.

---

### Post by mat69 on 2005-08-27
[QUOTE=][/QUOTE]
 Sorry that I did not make my point clear.
I know that you can use chmod -R and gnomebaker or K3B but why SHOULD I need the console, why should I need additional burning apps especiallly K3b which makes problems started by a normal user (.ICEauthority - file --> I know how to fix it). That's not great for a newbie.
Gnome should be enhanced. I don't think - not experienced in any way - that those features will be so hard to implement.

---

### Post by doclivingston on 2005-08-27
[QUOTE=mat69]One of that is that there should be an option to recursively change the rights of some folders. I mean it should be like Win XP or KDE. You select a folder press the right mouse button go to options change the rights and now select the option to change the rights for subfolders and the files in those folders too. Just a simple checkbox.[/QUOTE]

There was a bug filed for this against nautilus several years ago. From reading the large number of comments on the bug, it appears that no-one can agree on the exact semantic that it should have, or what the UI should be.

If you want a simple checkbox, should it apply those exact permissions to the files or just the ones you changed
 * If the former, consider that directories should normally have the execute permission and files shouldn't (except when you don't want it that way).
 * For the latter, figure out a UI that a) is easy to understand, and b) doesn't make the dialog several times larges with hundred of options.

Basically should it work like "chmod -R 777", or "chmod -R a+w"?


Setting permissions recursively isn't something the "average user" will want to do, and there are several different groups of "power users" who want it to do slightly different things. Basically it's not going to be implements until people agree on how it should work, and no-one can agree.

---

### Post by mat69 on 2005-08-28
Sorry but I can't agree with you here.
The only time I needed to set permissions recursively was chmod -R u+rxw. If you copy the data of a CD (or a USB stick) you often don't have the permission to write. But changing the permissions at once with the tools shipped by Gnome (not considering the newbie hostile console --> how should a newbie find the command chmod, chown ....?) is not possible. Please don't tell me that copying data from removable devices is a task an average user doesn't want to do.
So at all those people came to the conclusion that it is better not to ship this option because SOME peole could be distracted while most users of Win XP (by default) and KDE use this option successfully?

So please add the checkbox "Apply settings to all subdirectories and their contents".
I know in some cases it will be usefull to change the rights just for folders (read only) and for files (rw) seperatly but for this you could add the advice that there is the console command chmod (=link to a special help-file with examples like "find . -type f -print0 | xargs -0 chmod 644") [maybe you should add chown too but there I'm not sure] and the change-right-tool (not existing yet, but why not or am I blind?).

I hope you see the advantage of this idea: Now you are left alone. You do not know that there is a way to change the rights of subdirectories and their files all at once. You do not know that you have almost endlessly possibilities to change the rights to use those tools for YOUR needs. You will get the impression that some tasks are really time consuming in Linux (Ubuntu to be exact but the impression will stick to Linux too) while they aren't! You keep people in the dark!


PS.: With you I don't mean you. ;) I'm from Austria here we have different words for you (you alone) and you (more people).

---

### Post by doclivingston on 2005-08-28
I agree that "chmod -R u+rw" is normally what you want it to do; but a "apply these permissions to the contents of this directory" won't do that, it'd do a "chmod -R 755". When you are using checkboxes to change the permissions, there is no easy way to tell it you want "u+rw" rather than "755" - which is the issue that is stopping this being done.

The biggest problem with it doing a "chmod -R 755" is that it will add execute permissions to files, which you almost certainly don't want to do. Windows doesn't suffer from this problem because it's simple permissions don't have an "execute" permission, and ACLs behave differently (sidenote: Eiciel work well for dealing with ACLs). I haven't tried changine file permissions in KDE before, so I'm not sure how well that works.

---

### Post by mat69 on 2005-08-28
Imo it is not working very well in KDE but at least it is there.
But you could split the command in two commands. At first it only changes the directories and then the files (-x).

Overall the impression remains that the properties dialog is nearly useless for changing rights.

---

### Post by mat69 on 2005-09-02
Can someone post the link of nautilus-burner- and chmod-recursive-issue at bugzilla please, so that I can post my arguments and ideas there as well?
Thanks in advance.

---

### Post by doclivingston on 2005-09-02
[http://bugzilla.gnome.org/show_bug.cgi?id=44767](http://bugzilla.gnome.org/show_bug.cgi?id=44767) is the recursive chmod bug, I'm not sure about the cd burning one.

---

