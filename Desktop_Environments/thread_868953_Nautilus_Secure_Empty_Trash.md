---
title: "Nautilus Secure Empty Trash"
date: 2008-07-24
forum: Desktop Environments
---

### Post by MaddMatt on 2008-07-24
Different methods for securely deleting files through Nautilus have been discussed in the past.. Personally I prefer using srm through nautilus-actions, but individually shredding each file is rather inconvenient. Does anybody know of a way of enabling a 'secure empty trash' button or menu for Nautilus? This would enable you to put files in your trash normally, and then with one button, batch the shredding of all. Just a more convenient way of dealing with erasing files... but the trash:/// in Nautilus does not allow for nautilus-actions... Anyone know how to do these sorts of mods for the trash? 

Cheers, 
M

---

### Post by Potatoj316 on 2008-07-24
can shread operate recursivly on directories?  If it can then you could set up a script that does just that and then puts the trash directory back when its done.

---

### Post by MaddMatt on 2008-07-24
All of the shredding programs I know of have recursive modes - the problem is that the Nautilus trash, from what I understand, is a compilation of different .trash folders from around the operating system - not stored in a centralized place. I've tried shredding things in the past from the trash with a nautilus-script but no luck. Essentially it doesn't work because of the architecture of the trash system.

---

### Post by Potatoj316 on 2008-07-24
I think that nautilus's trash is just in /home/USER/.Trash, try deleting things and then look there.  If it is a combination of directories than you still can create a script to do this.  I think this would work but check the help/man page just to be sure (man shread or shread --help)
```
shread -r /home/USER/.Trash/
```
The other trash might be somewhere like /home/USER/.share/local/trash (i dont really know, im not on ubuntu at the moment)

---

### Post by MaddMatt on 2008-07-24
> **Potatoj316 said:**
> I think that nautilus's trash is just in /home/USER/.Trash, try deleting things and then look there.  If it is a combination of directories than you still can create a script to do this.  I think this would work but check the help/man page just to be sure (man shread or shread --help)
```
shread -r /home/USER/.Trash/
```
The other trash might be somewhere like /home/USER/.share/local/trash (i dont really know, im not on ubuntu at the moment)
well normally I do have a .Trash folder in my ~/ but I did just find one here: ~/.local/share/Trash/files, which does contain everything from my trash. Good job! I guess an easy nautilus-script could secure delete those files at any time... I'll whip one up and put it up here in a minute or two. There's probably a more elegant solution, though.

---

### Post by MaddMatt on 2008-08-30
Sorry I forgot to put this up for a while.

OK so here is a nautilus script that I coded to do do a very good job of securely deleting trash. It assumes that all of the trash can be found in ~/.local/share/Trash (which is usually the case). It also depends on the secure-delete package. Place the script in your ~/.gnome2/nautilus-scripts/ directory and don't forget to chmod +x it. 

Theoretically you could put this in your .profile and have it run at login. 

Let me know if anyone has improvements... 
Ideally I would want to:
[LIST]
[*]have it as an additional button in Nautilus, or even have Nautilus default to this action when emptying the trash
[*]estimate the progress instead of going back and forth
[/LIST]
Unfortunately, I don't know how to do those things. Cancel is supposed to 'auto-kill' the srm process - I think that because of the load that srm puts on your box it takes some for it to actually kill it... the process load doesn't go down for some time though, that's for sure. 


Here's the code:

```

#!/bin/bash
#created by matter - this script depends on the secure-delete package; 
#use this command to install it: 
#$ sudo apt-get install secure-delete
#This software comes with absolutely no warranty, so please use at your own risk. 

srm -r -v -z ~/.local/share/Trash | zenity --auto-close --auto-kill --progress --width 350 --pulsate --text "Securely Emptying the Trash - Please be patient." --title "Securely Erasing Files"

```

---

### Post by ehazlett on 2008-09-08
I created a simple Nautilus plugin to secure delete files...

[http://reconstructor.aperantis.com/index.php?option=com_remository&Itemid=33&func=select&id=18](http://reconstructor.aperantis.com/index.php?option=com_remository&Itemid=33&func=select&id=18)

evan

---

### Post by MaddMatt on 2008-09-08
Good show! I see this makes a right-click extension! Very nice touch. I'm not a good coder, so I wasn't quite sure how to go about doing this. 

I had a peak at the code, though, and I'm going to modify it on my system to use secure-delete (command = 'srm') instead of wipe, based on information from [another forum post]("http://ubuntuforums.org/showthread.php?t=868747").

> **cdenley said:**
> It looks like wipe uses patterns suggested by Peter Gutmann for most of the passes, which is probably a little better than using random data. I don't think it's necessary to make so many passes with modern hard drives, and the advantages from one tool to another are trivial. You might want to look at srm, which has recursive mode, can use zeros for the last pass, and does 27 passes with Peter Gutmann's special patterns. It also comes with other useful tools.
```

sudo apt-get install secure-delete
man srm

```
You might want to read other threads about the limitations of deleting individual files. The best way to destroy your data (without physically destroying your disk) is to use the "secure erase enhanced" function built into the firmware of modern hard drives. This will erase the entire disk, though. 

Hope you don't mind, but I prefer srm rather than wipe due to the zeroing option. As I said, I'm not much of a coder - more of a 'hack it together' type of guy, so I just modified your script it to:

```
Line 15: WIPE_CMD='srm -z -v -r'
```

Hope you don't mind!

Also, it seems that the code is supposed to provide pop-ups? This doesn't happen on my system (8.04) Any ideas? 

Furthermore, do you know how to put a button next to the 'empty trash' button while surfing trash:/// ? That I think would be the most useful, as users could continue to delete trash in a normal way, and then securely empty it when they are ready to, rather than each file individually. 

Thanks again for the code, let me know your thoughts on the changes. 
-M

---

### Post by ehazlett on 2008-09-19
i'm glad you like it!  

i don't think there should be any pop-ups - just a menu entry.  a friend of mine mentioned an idea of putting all "secure delete" options into a window similar to the file operations window (for long delete operations)

that's why it is open source - change whatever you like to fit your needs!

evan

---

### Post by binbash on 2008-09-20
> **Potatoj316 said:**
> I think that nautilus's trash is just in /home/USER/.Trash, try deleting things and then look there.  If it is a combination of directories than you still can create a script to do this.  I think this would work but check the help/man page just to be sure (man shread or shread --help)
```
shread -r /home/USER/.Trash/
```
The other trash might be somewhere like /home/USER/.share/local/trash (i dont really know, im not on ubuntu at the moment)

Shread is NOT secure a lot.The items can be recoverable.There was a thread about it on the forums

---

### Post by mahmater on 2008-12-15
hi madmatt! I'm interested in the change you brought upon the script because I ve always thought secure-delete package is more efficient. will you plz post it and tell me how can I use it.

many thanks

---

### Post by MaddMatt on 2009-01-04
> **mahmater said:**
> hi madmatt! I'm interested in the change you brought upon the script because I ve always thought secure-delete package is more efficient. will you plz post it and tell me how can I use it.

many thanks

Hi Mahmater

The easiest way to do this is to install the .deb that ehazlet posted, located here:

> **ehazlett said:**
> 
[http://reconstructor.aperantis.com/index.php?option=com_remository&Itemid=33&func=select&id=18](http://reconstructor.aperantis.com/index.php?option=com_remository&Itemid=33&func=select&id=18)


Then, edit the script with a command such as:
```
$ sudo gedit /usr/lib/nautilus/extensions-2.0/python/secure-delete.py
```

and make this change:

> **MaddMatt said:**
> 
```
Line 15: WIPE_CMD='srm -z -v -r'
```


If you want I can make a .deb, but I just think this is easier. Sorry for the delay!

Cheers, 
M

---

### Post by blueshiftoverwatch on 2009-03-08
> **ehazlett said:**
> I created a simple Nautilus plugin to secure delete files...

[http://reconstructor.aperantis.com/index.php?option=com_remository&Itemid=33&func=select&id=18](http://reconstructor.aperantis.com/index.php?option=com_remository&Itemid=33&func=select&id=18)

evan
Thanks for making that. But is there a way that I can modify that program so that it will only add the secure delete option to the File menu in Nautilus's menu bar instead of being available for any file when you right click on it? Or adding a "secure delete" button next to the "empty trash" button that's in the blue bar in the trash folder?

I don't like the idea of being able to permanently delete files by using the right click context menu. The possibility for me to right click on something and through carelessness accidentally delete it instead of selecting another option seems too high. Especially since it just goes right ahead and deletes the file without popping up with a window asking if your sure you want to permanently delete said files.

The Ubuntu devs should add some sort of secure delete option to the trash folder with their next release. Seems like something that would not only go a long way towards protecting the users security but also be fairly easy to implement. They already include Gnu Privacy Guard by default, why not something like this?

---

### Post by sehrgut on 2009-03-14
The author of the trash-cli package, Andrea Francia, is considering addition of this feature to his package. From there, it'd be a hop, skip, and a jump to calling `trash-empty --shred` from a Nautilus menu.

---

