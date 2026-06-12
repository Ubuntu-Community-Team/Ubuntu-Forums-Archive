---
title: "Error message with Pidgin"
date: 2009-05-24
forum: General Help
---

### Post by Mashuteichou on 2009-05-24
This is for a friend, not me.  (They don't understand Linux yet, but recently started using it regardless.)

Basically, she did something that made Pidgin freak out and not work.  It would start loading, but nothing would happen after the initial loading was over.  Open it 2 times, same thing yet 2 would be running in the background.  

I had her open terminal and type in pidgin.  Nothing happen.  Sudo pidgin - generated an error message, but the pidgin loaded like it was the first time it had ever loaded.  As in, she had to redo all her email and password stuff.  

Heres the error:

 GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to execute dbus-launch to autolaunch D-Bus session) 

I am not an expert on Linux by any means.  So this error message is like Japanese to me, I can understand some of the words, but in context with the words I don't know, I have no idea whats being said.  

It sounds like something happened when the system failed, causing an error that messed up pidgin.  But, I have no idea.  

thanks for the help.

---

### Post by kerry_s on 2009-05-24
you should not sudo any program that is run as a normal user, you have just screwed up the permissions of that program. sudo is for command line programs, use gksudo or gksu for gui programs, but there are certain programs that never need to run as root, webbrowser and im would be on that list. :lolflag:

open your folder and try and delete the folder " .purple ", you might have to press ctrl+h to show the hidden files. you might even have to use "gksudo nautilus" if it's already owned by root.

---

### Post by Mashuteichou on 2009-05-24
Im confused though.  It works now normally.  Do I still have to have her delete it?

---

### Post by kerry_s on 2009-05-24
> **Mashuteichou said:**
> Im confused though.  It works now normally.  Do I still have to have her delete it?

if it's running as root, your opening the system up to attack. it should not be running as root.

---

### Post by Vadi on 2009-05-24
Yes, delete .purple and don't prefix 'sudo' to anything unless it actually requires it. Pidgin doesn't, it's best to run it as a normal user.

---

