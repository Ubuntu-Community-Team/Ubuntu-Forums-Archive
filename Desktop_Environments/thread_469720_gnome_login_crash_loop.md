---
title: "gnome login crash loop"
date: 2007-06-10
forum: Desktop Environments
---

### Post by kornelix on 2007-06-10
I installed 7.04 on a new PC and started to customize my desktop. Afterwards I was not able to log in: gnome crashed after flashing my desktop briefly and went back to the login screen. After a long process of testing the modifications one at a time, I came to this conclusion: If I resize the bottom panel from 32 to 40 pixels, gnome crashes. If I put it back at 32, all is OK again. 

The file I was changing between tests:
  ~/.gconf/apps/panel/toplevels/bottom_panel_screen0/%gconf.xml

The change I made was to the entry called "size".

Test procedure:
0. log in to normal account
1. using panel properties (right mouse menu), change the bottom panel size to 40.
2. log out and back in
3. gnome crashes and returns to login page
4. log in as root and edit the above file back to 32
5. log in to normal account
6. everything is now normal

daemon.log had the unhelpful message: 
  gdm_slave_xioerror_handler: Fatal X error - Restarting :0

I was not able to find anything else relevant among the tons of trash in the many log files.

Any comments before I file a bug report?

---

### Post by kornelix on 2007-07-23
I got no help from this forum, but I found more relevant information by doing a google search. I found several complaints about gnome crashing and returning to the login screen immediately after displaying the panel. 

The problem is best characterized as follows: If panel transparency is enabled and panel size is bigger than 32 then gnome crashes about 0.1 seconds after initializing the screen.

I have two PCs running Ubuntu 7.04, configured identically. One crashes, the other does not. So I turned off transparency on the crashing PC and now it runs OK, even with the big panel size. 

I hope this helps someone else.

---

### Post by MrHippocampus on 2007-07-23
Ive seen this problem come up a few times, definitely file a bug report as its affecting quite a few people

---

### Post by kornelix on 2007-07-26
Bug report filed, # 128482

---

### Post by Brightrock on 2007-07-27
I had the same problem.  Thanks for the fix!

BR

---

