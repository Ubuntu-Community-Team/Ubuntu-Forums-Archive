---
title: "Finding Trash in Nautilus &amp; Update Manager question"
date: 2008-07-11
forum: Desktop Environments
---

### Post by VargasTheBlind on 2008-07-11
I have a problem with some files from a read-only medium being moved to the trash, and now they can't be moved or deleted, and there are a LOT of files in there so changing the permission would be a major pain, plus even if I try to change the permission i get a "Operation not supported by backend" error...of course, I would just delete them from Nautilus or the terminal, but the problem is, I don't know how to find the trash folder in either!:lolflag:

My other question is, there's an update called libcairo2 in the update manager and in the description it says not to install it since it creates slowness issues...I didn't install it, but the stupid thing is I have a very nice black and white theme going with matching icons, and that orange burst is really screwing up my desktop look. Any suggestions on how to get around this?

Thanks,
Vargas

---

### Post by Ataris on 2008-07-11
I don't know about the second issue, but I've had the "deleting files without permission issue" many times. You have two ways to solve this. Open up a terminal and type either ```
sudo konqueror
``` if you have KDE or ```
sudo nautilus
``` if you have gnome. In the address bar type ```
trash:///
``` and then select all of the files there and right click on them, select delete, and they're gone forever. The key is simply opening up a file manager using "sudo" to make you the root user. Hope this works for you.

---

### Post by niyonk on 2008-07-11
> **VargasTheBlind said:**
> but the problem is, I don't know how to find the trash folder in either!:lolflag:

lol, or you could try ~/.local/share/Trash...I think :)

About the cairo lib file, just go on and install.
If it bring trouble, System restore is always there :rolleyes:  :lolflag:

---

### Post by sisco311 on 2008-07-11
[FONT=monospace]delete all files from the Trash:
[/FONT][FONT=monospace]
[/FONT]```
sudo rm -fr ~/.local/share/Trash/files/*
```

or open nautilus as root (in the Trash folder):
```
gksu nautilus ~/.local/share/Trash/files/
```

---

### Post by niyonk on 2008-07-11
> **sisco311 said:**
> [FONT=monospace]delete all files from the Trash:
[/FONT][FONT=monospace]
[/FONT]```
sudo rm -fr ~/.local/share/Trash/files/*
```


I have always wondered...why not Just delete the contents of Trash...what is in the info folder??
What you delete in the Trash, don't you also delete it's information. :confused:

BTW...you from Romania, Numa Numa YEAAAH :guitar:

---

### Post by VargasTheBlind on 2008-07-11
> **sisco311 said:**
> 
```
gksu nautilus ~/.local/share/Trash/files/
```

Worked like a charm, thank you!

And what is System Restore?

---

### Post by niyonk on 2008-07-11
> **VargasTheBlind said:**
> And what is System Restore?

Just a stupid joke about windoze :biggrin:

Cheers!

---

### Post by VargasTheBlind on 2008-07-11
> **niyonk said:**
> Just a stupid joke about windoze :biggrin:

Cheers!

Ah, flew right over my head :lolflag:

So you lost me, was the part about installing it a joke too?:confused:

---

### Post by sisco311 on 2008-07-11
> **niyonk said:**
> I have always wondered...why not Just delete the contents of Trash...what is in the info folder??
What you delete in the Trash, don't you also delete it's information. :confused:


You're right, it's safe to delete the content of the info folder.

> what is in the info folder??The restore informations.
For exemple the path from where the file was deleted.
(The restore option is not inplemented yet)
> BTW...you from Romania, Numa Numa YEAAAH :guitar:You confuse Romania with Moldova.:)

[http://en.wikipedia.org/wiki/O-Zone](http://en.wikipedia.org/wiki/O-Zone)

---

### Post by niyonk on 2008-07-11
> **VargasTheBlind said:**
> So you lost me, was the part about installing it a joke too?:confused:

The part about installing was:
Install the file, if it gives you problems like they mention then remove it and wait for a more stable version.
I think they mention it according to a number of people reporting having had problems with it.
You might not get the same problems :)

---

### Post by VargasTheBlind on 2008-07-11
> **niyonk said:**
> The part about installing was:
Install the file, if it gives you problems like they mention then remove it and wait for a more stable version.
I think they mention it according to a number of people reporting having had problems with it.
You might not get the same problems :)

What about if I just install it and then immediately remove it? Will that remove it from the updates list too? I've been poring over the bug report page for that specific update, and opinions are very divided on whether it's a true bug or not.

---

### Post by niyonk on 2008-07-11
> **sisco311 said:**
> 
You confuse Romania with Moldova.:)

[http://en.wikipedia.org/wiki/O-Zone](http://en.wikipedia.org/wiki/O-Zone)

I don't know how to read maps and I am awful in history ;) lol

About the system restore, I think it would be very useless...unless it would only be for "system files"
Besides, we don't have registry to mess around with \\:D/

Cheers!

---

### Post by niyonk on 2008-07-11
> **VargasTheBlind said:**
> What about if I just install it and then immediately remove it? Will that remove it from the updates list too? I've been poring over the bug report page for that specific update, and opinions are very divided on whether it's a true bug or not.


Oh..sorry, I ddn't get your Q right. I did not know you wanted you wanted to remove it from the updates....
I think there is a way...:-k

If only I could remember where I saw it, somewhere in these very forums :confused:
I'll google the forums for ya :p


::EDIT: found em'. It seems the solution is to go to 'synaptics package manager' and click on the package and "Lock Version" somewhere in the menu.
try [this]("http://ubuntuforums.org/showthread.php?t=703671"), [this]("http://ubuntuforums.org/showthread.php?t=704904") for exact answers.

---

### Post by VargasTheBlind on 2008-07-11
I installed it, and I do indeed have slowness issues, especially in Gmail as the bug states...and I don't know how to revert bag to libcairo2 v1.6.0-ubuntu1 since 1.6.0-ubuntu2 replaced it, anyway I can get it through the terminal?

---

### Post by niyonk on 2008-07-11
I think you can try the "Lock version" method I posted.

Maybe it will skip the latest version and install the previous one.
But you do have to remove it COMPLETELY from synaptics package manager.

Like I said, wait for a more stable version :tongue:
It won't be long before some bugs are squashed :wink:

---

### Post by VargasTheBlind on 2008-07-11
Nevermind, I installed it, noticed slowness in Gmail, downgraded through Package>Force Version but realised that the slowness in Gmail isn't dependent on that version, so I just reinstalled it so I don't have the orange burst in the panel. Now all that's left is to wait for a solution to the scroll and Gmail problem in FF. Thank you for helping, marking as solved.

---

### Post by VargasTheBlind on 2008-07-11
**** **** **** I removed libcairo completely as per your suggestion and now everything is gone! openoffice, the terminal is gone, the advanced menu, EVERYTHING!

---

### Post by VargasTheBlind on 2008-07-11
No home folder, no directories PERIOD, there´s NOTHING there!

---

### Post by VargasTheBlind on 2008-07-11
**** **** **** I´m writing this from another PC, PLEASE tell me there´s SOME way to revert the changes!

---

### Post by niyonk on 2008-07-11
What?? NOOOOOOOOOOO!! :shock:

sorry, DAMN! am so stupid...i meant "mark for complete removal (including configuration files)" option in the package manager. :(

Tell me what you have left...

you could try sudo apt-get install -f to repair broken packages...

Sorry, again I ddnt explain the remove completely fully.
:cry:

and I thought your post #16 solved your Question, so I did not really bother.
What command did you run anyway?? Take a look at  [http://ubuntuforums.org/announcement.php?a=54]("http://ubuntuforums.org/announcement.php?a=54")
And what tutorial/procedures did you follow to remove it.
If you run any of those commands, you are pretty much scr*wed :(

---

