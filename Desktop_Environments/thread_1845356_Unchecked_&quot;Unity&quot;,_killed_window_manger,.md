---
title: "Unchecked &quot;Unity&quot;, killed window manger, can't do anything!"
date: 2011-09-16
forum: Desktop Environments
---

### Post by BanderSnoot on 2011-09-16
Please help, I have just totally hosed my Ubuntu 11.04 setup.

I had been using Unity

I went into Compiz thinking I would try to change the Window behavior.

I decided I would try not using Unity, so I unchecked the box.

Yeah, Unity is gone, and so is 100% of desktop.  No icons, no launcher, no menus, nothing!  After I login, I can't even start a terminal session.

I had to revert back to a Windows partition to get here!

Please, any guidance appreciated.

---

### Post by wildmanne39 on 2011-09-16
Hi, here is what you need to do.

You can reset unity or compiz or both by doing the following.

Open a terminal by hitting ctrl+alt+t or alt+f2, if one of those key combination does not open the terminal try ctrl+alt+f1 thru f6. Then type this command in terminal to reset unity. 
```
Unity --reset
``` Use these commands to reset all the settings in compiz.
```
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
``` 
let unity reset run for about 3 minutes then restart your computer and do not worry about the errors.
Thank you

---

### Post by Blasphemist on 2011-09-16
I'll pass on this link from one of the forum users, wildmane39. At the end of the post it describes how to do the reset you need. Then, if you go through the post it describes how to set up the cube but also how to modify some other settings in ccsm. It is just good experience.

---

### Post by BanderSnoot on 2011-09-16
Thanks very much.  Ctrl-Alt-T + "unity --reset worked."

---

### Post by wildmanne39 on 2011-09-16
Hi, that is great and you can click on the link for setting up the cube and effects in my signature if you want to change any other settings in compiz, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by Blasphemist on 2011-09-16
> **wildmanne39 said:**
> Hi, here is what you need to do.

You can reset unity or compiz or both by doing the following.

Open a terminal by hitting ctrl+alt+t or alt+f2, if one of those key combination does not open the terminal try ctrl+alt+f1 thru f6. Then type this command in terminal to reset unity. 
```
Unity --reset
``` Use these commands to reset all the settings in compiz.
```
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
``` 
let unity reset run for about 3 minutes then restart your computer and do not worry about the errors.
Thank you
Here I was trying to pass on your site, while you were answering yourself, and somehow forgetting to paste in the link. Jeez!

---

### Post by wildmanne39 on 2011-09-16
Hi Blasphemist, you are doing a great job keep up the good work.

---

