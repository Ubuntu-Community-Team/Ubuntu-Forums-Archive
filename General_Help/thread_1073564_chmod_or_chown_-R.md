---
title: "chmod or chown? -R ?"
date: 2009-02-18
forum: General Help
---

### Post by melbs on 2009-02-18
I have posted before about this and thought it was solved but I'm still having problems. Here's the situation:

I am in the group moodle-admin and moodle-admin is the group for /usr/share/Moodle. root owns it. I/moodle-admin has the correct r/w/x permissions on Moodle but NOT the folders underneath.

I know my network person has to use -R but do they use chmod, chgrp, chown..or what? All I need is to have the moodle-admin have Read rights for the fodlers under /usr/share/Moodle.

sudo chmod +r -R /usr/share/Moodle ? sudo chgrp -R moodle-admin /usr/share/moodle ?

I know it's so simple but I'm not sure waht syntax to use.

---

### Post by melbs on 2009-02-18
Sorry, I think I need the write permission. I can currently view the files.

---

### Post by hyper_ch on 2009-02-18
but why would you need access to /usr/share/... ?

---

### Post by melbs on 2009-02-18
I need to have permissions to upload files, change files in the Moodle folder, AND the folders within Moodle. That is the path to moodle.

   [FONT=Arial]Sudo chmod g+w &#8211;R /usr/share/moodle or instead of g+w, 775?

Since the group is already moodle-admin for the folder and all folders under it..and I'm in that group...I believe I just need to change the group permissions.
[/FONT]

---

### Post by hyper_ch on 2009-02-18
that should work

but why do you need to upload files there? It's not a folder one normally should have write access to IMHO.

---

### Post by melbs on 2009-02-18
Sometime I need to change things in the .php files. Upload new themes, modules, plug-ins..lots of stuff...via ftp or terminal.

Also, is 775 a correct/safe setting..does that mean others can not execute or write..


One final question :) What exactly does the Execute permission entail?.. Thanks.

---

### Post by stchman on 2009-02-18
There is a reason that root owns everything on / besides ~/.

It is Linux security model.  I would not change permissions on root owned folders as you are opening security holes.  If you modify permission or ownership on root owned folders then a script can either modify or delete that folder without your knowledge.

If you need to copy files to that folder then use sudo command, that is the far safer way.  You can also start your favorite graphical ftp program via using the gksu command.

I am surprised there is not some ~/.Moodle folder in your home folder to contain settings.

Once again I do not recommend changing permission/ownership of root owned folders, especially system critical folders.

---

### Post by melbs on 2009-02-18
But I would be changing the group permission not the owner of the file..I will be using an FTP to transfer the files. How do I use "sudo" in that case?

When I ssh in Moodle is my home folder.

---

