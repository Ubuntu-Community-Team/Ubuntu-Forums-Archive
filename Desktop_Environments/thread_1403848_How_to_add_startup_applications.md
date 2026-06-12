---
title: "How to add startup applications"
date: 2010-02-10
forum: Desktop Environments
---

### Post by temporos on 2010-02-10
I think this is a gnome question, so I used that prefix.  If it's really just an Ubuntu Netbook Remix issue, then let me know and I'll change it.  Note that I'm still a "beginner" with Linux.

I'd like to add my installed chat client (Empathy) to the startup applications list using the control panel System > Startup Applications.  When I click "Add," however, I don't know where to look for Empathy.  I've searched through most of the folders, but I can't find any applications, and I'm not even sure what a linux app *looks* like...  Any help would be appreciated.

Maybe this belongs in the "Absolute Beginner Talk" forum.  LOL

I'm rockin' the netbook remix v9.10.  It's fully-updated.

---

### Post by mats! on 2010-02-10
Hello temporos, 

Usually empathy is located in /usr/bin/empathy. That's the path you should have to add in Startup Applications.

A quick tip, if you want to locate any application, you can open up a terminal, and use: whereis <program>

Hope this helps

---

### Post by sisco311 on 2010-02-10
You don't have to specify the full path to the binary. Just type *empathy* in the command field.

---

### Post by temporos on 2010-02-18
This worked.  Thanks.  :)

---

