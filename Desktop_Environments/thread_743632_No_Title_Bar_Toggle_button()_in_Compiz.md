---
title: "No Title Bar Toggle button(?) in Compiz"
date: 2008-04-02
forum: Desktop Environments
---

### Post by dangerousgoat on 2008-04-02
Hi, first post, essential linux noob,


I am having a little issue now and then, and because of the phrasing, having a hard time finding an answer.

My title bar is fine most of the time, but every so often i hit some combo of keys, and they disapear (the end result looking like the 'bug' that everyone is talking about, and one i had to fix earlier in my install).

Basically I think there is some hotkey that i dont know about, where it might be set etc that switching compiz over to this no-title-bar state.  I think it might have something to do with the mousepad and something else? but im not sure.

My current workaround is to log off and log back on, but its just one little annoyance i wouldn't mind fixing.

Thanks for your help


PS.  I am really enjoying Ubuntu running on my Dell XPS m1330, it really wows the ladies =D

---

### Post by dangerousgoat on 2008-04-20
still happens=\

---

### Post by chiefmanyrabbitguteat on 2008-04-21
I think that I had a similar problem with Emerald.  Logging off and back on is a pain, so I made a launcher.  You can either do it right on a panel (Right click on the panel, and click Add Item), or in the main menu (System - Preferences - Main Menu, click "New Item")  Name it something like "Compiz Reboot" and make the command ```
 compiz --replace 
```
When the bug happens, just launch your new menu, and it it will restart Compiz without having to reboot.

(If you use Emerald, use ```
emerald --replace 
``` instead.

It ain't perfect, but it beats logging off and back on again.

---

