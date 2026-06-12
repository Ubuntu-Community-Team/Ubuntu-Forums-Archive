---
title: "Copy desktop environment to other users"
date: 2010-05-14
forum: Desktop Environments
---

### Post by nothingtoprove on 2010-05-14
Is there a way to copy a customised desktop environment to other users on the same PC?

That includes not only the theme but fonts, panel position and sizes and preferably DockbarX.

TIA

---

### Post by nothingtoprove on 2010-05-15
Daily bump.

---

### Post by nothingtoprove on 2010-05-18
Anyone?
Please.

---

### Post by portentum on 2010-05-18
This isn't the cleanest way to do what you want, I'm sure, and if someone else has a better idea they're welcome to suggest it. But seeing as no one has in days...

**Solution 1**:
```

cp -rf /home/<youruser> /home/<newuser>

```
You'll want to delete any personal files you don't want them to have that you've stored in your home folder from theirs, other likely candidates for deletion are the /home/<newuser>/.mozilla folder so that they don't have your firefox profile, and others like that. You'll have to pick through the hidden folders and see what you want to keep to yourself.

After you've done that, you chown the folders to them.
```

chown -R <newuser> /home/<newuser>

```
You may not have permission to run those commands, if so you'll need to sudo them.
Before running the chown command the user should exist, so create the user account if it does not.
The capital "R" in chown matters, some programs don't use the lowercase -r switch.
Be sure to try each command without sudo first, of course, why make a habit of using it when you don't have to?

Hope this helps, and as I said above, before anyone complains about this solution feel free to offer one up yourself.

edit:[SIZE="1"]If I seem a little defensive of this, well, I've seen people complain about some odd, rather safe commands.[/SIZE]

**edit2**:After posting I thought a little and realized it was also fairly simple via the GUI. Sorry, I'm very CLI-oriented. :P

**Solution 2:** 
Open a root nautilus window (gksu nautilus), open the /home folder, copy your user folder, paste it, rename the copy to the new username. 
Remove any personal files you don't want to share as mentioned above in solution 1. (ctrl+h should show hidden files in the nautilus window)
If they have a folder already you can rename theirs to use as a backup first. 
Right click their new folder, open the properties dialog box. 
Permissions tab, change ownership to their user (their user must exist at this point), making sure the apply permissions recursively box is checked. 
Apply. (or OK?)

I don't have nautilus myself, so the wording may not be precise, but the options should be there as far as I am aware.
Both methods do the same thing, the same way, so either would work equally well.
If my rushed explanation isn't clear enough I'd be happy to clarify any steps.

**edit3**: I'm getting tired of second-guessing myself. :P
Ok, I realized this may all be overkill as well, depending on how much you want to share.
You could also...

**Solution 3:**
Create new user account, copy only the custom configurations you want into their home folder.
To do this I would suggest making sure their user account exists, then copying any (hidden) configuration files/folders to their home folder.
Examples would be the /home/<youruser>/.gnome2 folder, /home/<youruser>/.config/xfce4, etc.
Permissions on each configuration folder copied would need to be changed (right click, properties, Permissions tab, change ownership to new user, apply recursively as stated above).
Again, to display hidden folders/files (the ones with . in front of them) you can press ctrl+h in nautilus. You may need to do this copying in a root nautilus window.

---

### Post by nothingtoprove on 2010-05-25
Many thanks.
I'll give it a try later today.
Some way to easily export custom preferences would be nice, but I'll see how I go with solution 2 as being a casual PC user, ie Windows and Mac background, solution 1 gives me brain-ache just looking at it.

---

### Post by nothingtoprove on 2010-06-10
Thanks for the reply, but this proved beyond my desktop user abilities.
You can't win 'em all.

---

### Post by AfrikaDietmar on 2010-06-11
This sounds interesting, i'm trying to do something similar.

I have to setup ubuntu on 4 computers, and on all these 4 computers i will need to create several users on each PC who also need to have that same desktop, all with the same desktop environment, that is same programs and settings, profiles. In this way, any user can work on any PC. 

Is there a way I could make like a prototype desktop that I save, and then on each computer, after i have installed ubuntu, i apply the prototype settings that i have created and then it would be the same like the prototype with settings and (even with the programs?...) ?

---

