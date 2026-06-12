---
title: "Root Permissions Changed"
date: 2009-04-26
forum: General Help
---

### Post by Super TWiT on 2009-04-26
I was doing a reinstall of ubuntu, and moved my home data back.  As rsync was my backup program, my permissions were skewed.  So, I changed the owner to me, and ran ```
sudo chmod 700 -c --preserve-root /home/data -R
``` now, my root permissions have others being able to create and delete files, but only on the root path, not folders/files or anything in them.  Any ideas to why this has happened.  I have done multiple installs with this occuring each time.  The only simlink I have in my home, is at this point a broken one to a program I haven't yet installed.

---

### Post by Super TWiT on 2009-04-27
Oh, I should have mentioned that I am running Ubuntu 8.04, that I can make new folders via nautilus and the command line, and that the changes to the root partition stay when I run off of a live cd.  I have tested my ram (38 passes I think) with memtest, and no errors were found.  I have checked my install cd for errors, and even burned another copy from another image.  I have noticed that this doesn't seem to happen when I chown my data from the livecd as a test.  Could it be an update is changing something?:confused:

---

### Post by matt the destroyer on 2009-04-27
First of all, if you specify the path, you do not need the --preserveroot flag.  In fact, I am not sure that it exists as it is not in the man page.

Also, I am not sure what the -c flag does, it also is not in the man page.

Secondly, when you say "root path", do you mean "/" or "/root" or some other directory?

Now, please let us know what you would like to be doing.  Do you want the information in this directory to be shared? Do you want it to be private to just one user?

If you want it to be private, do this:

sudo chown -R <user>:<group> /path/to/directory
sudo chmod -R 700 /path/to/directory

This will make the directory and its contents read/write to the user you select and unreadable to other users.  Please note that this is not best practice as it makes every file in the directory executable, which is a potential security problem.  The alternative is to set the permission for each file individually.

If you want to set this up as a shared folder, the second line should be 

sudo chmod -R 770 /path/to/directory

Then, every user that you add to <group> will be able to read/write to the directory and its contents.  Again, this should only be used in the case that you trust the other users as they will be able to run any file in the directory as an executable.

I hope this helps,
-matt

---

### Post by Super TWiT on 2009-04-27
Thanks for responding!  I just put the preserve-root flag in to make sure I was preserving it, seeing as how I had this problem before.  -c means list all changes made.  These two flags are shown when the --help flag is used.  I should add that the root partition was no where in the changed list.   What I meant by root was /.  I should have been more clear.

---

