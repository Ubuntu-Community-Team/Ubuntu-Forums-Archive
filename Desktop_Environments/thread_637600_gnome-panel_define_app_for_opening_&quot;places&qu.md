---
title: "gnome-panel: define app for opening &quot;places&quot; locations"
date: 2007-12-11
forum: Desktop Environments
---

### Post by mtron on 2007-12-11
Hello fellow  Ubuntu'ers! 

I'm currently faced with an - for me - annoying problem. Out of curiosity i've installed the latest xfce release from scratch (including their file manager thunrar)

I' didn't stick with xfce so i removed all the stuff again. After a restart of the X Server i've logged in to gnome again and discovered that the Places menu Links don't work any more

The error is: 

> Could not open location 'file:///home/mtron/Documents'

Details: There was an error launching the default action command associated with this location.

so i suspect thunrar changed the  default action command somewhere in gconf, but to be honest i never really looked at this gconf-editor (raises horrible memories of the MS registry :( )

So i'm hoping a gnome hacker could save me some work and point me to the correct shema to chage all the open commands for the Places links from thunrar back to Nautilus

Best Regards
mtron

---

### Post by NilsE on 2007-12-11
One quick thing to check is to open Nautilus and right click on any folder, select properties, and check the open with option.  If there is nothing there you can add one.

---

### Post by mtron on 2007-12-11
i've tried this already (forgot to mention) but I can't change to nautilus which is in there. The checkbox won't move away from the already uninstalled thunrar (i've tried this as my normal system user as well as root)

---

### Post by mtron on 2007-12-12
bump  :confused:

---

### Post by deepbluepixel on 2007-12-12
dunno the real command to use but I always used the scripts on this [page ]("http://www.psychocats.net/ubuntu/nonautilusplease").

---

### Post by mtron on 2007-12-12
thanks for the tip, but i looked at the script, and it seems that the files it want's to modify don't even exist on dapper.

It seems that this is quite a complicated issue.

Anyone an idea where there might be a better place to ask?

---

### Post by mcduck on 2007-12-13
Open the gconf-editor, browse to desktop/gnome/applications/component_viewer and change the value of "exec" to "nautilus %s". That should solve the problem.

---

### Post by mtron on 2007-12-13
it's already set to this, but doesn't solve the problem. :(

---

### Post by mvdberg112 on 2008-02-08
Same problem as MTRON
But I was not so clever to remember what I have done! I do know that I installed Thunar at one point in time, and that is now not in the list; only Thunar-data 0.9.0.2 is installed, which is only documentation.
[QUOTE=mtron]
The error is: 
Quote:> 
Could not open location 'file:///home/mtron/Documents'

Details: There was an error launching the default action command associated with this location.
so i suspect thunrar changed the  default action command somewhere in gconf, but to be honest i never really looked at this gconf-editor (raises horrible memories of the MS registry :( )

So i'm hoping a gnome hacker could save me some work and point me to the correct shema to chage all the open commands for the Places links from thunrar back to Nautilus

Best Regards
mtron[/QUOTE]
I have tried the same as MTRON (i.e. > ... can't change to nautilus which is in there. The checkbox won't move away from the already uninstalled thunrar (i've tried this as my normal system user as well as root)
The precise steps are:
 Open a folder in Nautillus (for example with Places -> Computer); 
 browse to the folder that does not behave properly (in my case file:///home/myuser)
 Select File -> Properties -> Open With; here one should be able to add and remove items. It is possible to Add items, but they cannot be selected. Two items cannot be removed: 'Open Folder'  and 'Open Folder with Thunar', which is selected by the radio button. It is not possible to move the radio button and select any other option.

I have tried the script to restore to Nautiles from [http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)
But it did not help: an extra option did show up in 'Open with', but the action was not changed and could still not be changed.\
It seems:
(1) that this is a bug introduced by Thunar or a related/required library
(2) that Nautilus or GNome is not easily able to recover from the error. This is of course a fault of Nautilus or GNome - recovery should always be possible!

Question: Is there anywhere else where one can configure the default action? Say, default per group, per user, etc?

PS: seems to be reported here: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/35463](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/35463)

Thanks!

---

### Post by charonn0 on 2008-04-29
I had a similar issue, not the same, but similar. What I did was to make symlinks to the appropriate folders in my home folder.

---

### Post by maxter on 2008-05-23
i solved removing thunar, then reinstalling nautilus.
i killed then nautilus and gnome-panel

fixed

i'm only wondering at the cause of this problem....

---

