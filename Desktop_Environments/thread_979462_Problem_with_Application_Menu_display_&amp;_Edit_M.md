---
title: "Problem with Application Menu display &amp; Edit Menu"
date: 2008-11-12
forum: Desktop Environments
---

### Post by vinusweety on 2008-11-12
Dear all,

Being a newbie, sometimes crazy of doing some interesting stuffs on Ubuntu. Yesterday, after installing IE 6.0, found a way for adding IE 6.0 to Application Menu. 

Clicking on Edit Menu, I added IE to Internet Menu and to Programming Menu. Then, wen i right clicked on added Item.. There i found delete option. Guessing it will delete "IE 6.0" Menu Item. Proceeded that action. Now whole of Application Menu is gone. Edit Menu window is not opening. 

Can anyone please help me how to get back my Application Menu???? 8-[

---

### Post by ciscosurfer on 2008-11-12
If I understand you correctly, you can add the Applications menu back to your panel by right-clicking on empty space on any panel, selecting Add to Panel, scroll down and select either Main Menu or Menu Bar and then click Add then click Close.

---

### Post by vinusweety on 2008-11-12
> **ciscosurfer said:**
> If I understand you correctly, you can add the Applications menu back to your panel by right-clicking on empty space on any panel, selecting Add to Panel, scroll down and select either Main Menu or Menu Bar and then click Add then click Close.



Hi.. Thanks for your reply. My first experience of posting a question and getting reply very soon. Cool.. Getting more enthu on working with Ubuntu...

 I also tried this step. First i found out the empty Application menu path.. Here it goes

/home/"username"/.config/menus/applications.menu

and there was another copy this application menu in 
/etc/xdg/menus/applications.menu

Replaced this /etc/xdg/menus/applications.menu in that applications.menu in /home directory. Works fine.

---

### Post by aboud on 2008-12-05
where can i find the main menu file configuration ? 

i don't have this file, and even the folder menus.  

> 
/home/"username"/.config/menus/applications.menu

in fact 
```

find -iname *.menu* 

```
in my home folder return nothing. 


and 

```

/etc/xdg/menus/applications.menu

```
is not my menu, and changing it wont chang mine. 

________________________________________________________________
8.10 amd64

---

### Post by aboud on 2008-12-26
bump !

---

