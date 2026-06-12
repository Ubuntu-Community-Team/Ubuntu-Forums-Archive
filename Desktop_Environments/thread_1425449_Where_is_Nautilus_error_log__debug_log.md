---
title: "Where is Nautilus error log / debug log ?"
date: 2010-03-09
forum: Desktop Environments
---

### Post by sdaau on 2010-03-09
Hi all, 

I've been looking for this for a while, but cannot find an answer: Where are error or debug logs from Nautilus kept? Is there such a log file at all? 

My problem: recently, right-clicking on a text file, and choosing 'Open with "Text Editor"', starts the notification icon, but no editor is started. And I would like to know why (i.e. what is actually being called, and how it fails). Thus, the first thing I want to do is look at some log file for some errors - except I don't know which log file to look at :) 

Hope I can get some help on this..

Cheers!

---

### Post by hhh on 2010-03-09
I don't *think* there is a nautilus-specific error log, so I would look at the /var/log/messages file. More error log info is here...
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

You should also right-click the file, choose "Properties>Open with" and make sure it's set to gedit. Also, do other text files open? Could the file be corrupt, or not a text file at all?

---

### Post by sdaau on 2010-03-09
Hi hhh, 

Thanks for responding! 

> **hhh said:**
> I don't *think* there is a nautilus-specific error log, so I would look at the /var/log/messages file. More error log info is here...
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)


Good to know that - and shame there isn't a Nautilus specific file :) I was also trying to see if there are some command line options/switches that would make nautilus run in single thread and spit messages out to stderr, but couldn't find anything like that either. 


> **hhh said:**
> 
You should also right-click the file, choose "Properties>Open with" and make sure it's set to gedit. Also, do other text files open? Could the file be corrupt, or not a text file at all?

Nah, I was actually trying to replace gedit with Scite by default, and some symlinks got missing in the process - I discovered more less by accident that it was a broken symlink problem, which is why it would have been nice to have a debug log. And /var/log/messages spit absolutely nothing here. (btw, I posted about those steps as comment on [Matthew's Technology Blog: Making Scite the default editor in GNOME (Ubuntu)]("http://matthewstechnologyblog.blogspot.com/2007/05/making-scite-default-editor-in-gnome.html"))

Thanks again, 
Cheers!

---

### Post by hhh on 2010-03-09
np, peace.

---

