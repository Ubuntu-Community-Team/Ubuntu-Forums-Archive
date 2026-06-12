---
title: "Nautilus default permissions"
date: 2005-12-20
forum: Desktop Environments
---

### Post by invalid on 2005-12-20
Hi,
 
How would it be possible to change the default permissions given to a file created from within nautilus? They always seem to end up with 600, while I would like them to be 644. I know I can change them afterhand, but it would be more convenient to make changes to the default value.

Cheers

---

### Post by briancurtin on 2005-12-20
im wondering this as well, because everything i just copied off of a data DVD i have has 600 permissions, and thats not at all what i want, so now i have to go into folders and change everything again.

---

### Post by Madpilot on 2005-12-20
If you've got a whole load of stuff to change permissions of, you might want to start a Terminal & do it on the command line...

chmod is the command you want - "man chmod" gets you the manual file. There's a -R option to make it recursive, so you can change an entire directory w/ subdirectories & files with one command.

AFAIK Nautilus has no way to change an entire tree at once.

---

### Post by invalid on 2005-12-20
[QUOTE=Madpilot]If you've got a whole load of stuff to change permissions of, you might want to start a Terminal & do it on the command line...

chmod is the command you want - "man chmod" gets you the manual file. There's a -R option to make it recursive, so you can change an entire directory w/ subdirectories & files with one command.

AFAIK Nautilus has no way to change an entire tree at once.[/QUOTE]
Thanks for your suggestion, but not helping the question posed. I am aware of how to operate chmod in a command line, as I do 99% of my activity there. Maybe this will help some others who are not familiar though.

I am not worried about recursive calling in Nautilus, rather, just the creation defaults of a single file. Surely there has to be a setting somewhere that allows the change of the value.

---

### Post by cwaldbieser on 2005-12-20
[QUOTE=invalid]Thanks for your suggestion, but not helping the question posed. I am aware of how to operate chmod in a command line, as I do 99% of my activity there. Maybe this will help some others who are not familiar though.

I am not worried about recursive calling in Nautilus, rather, just the creation defaults of a single file. Surely there has to be a setting somewhere that allows the change of the value.[/QUOTE]
I remember a thread about this a long time ago.  The basic problem is that Nautilus does not respect your umask setting.  I searched and found this bug entry, which may be relevant:
[http://bugzilla.gnome.org/show_bug.cgi?id=317664]("http://bugzilla.gnome.org/show_bug.cgi?id=317664")

---

### Post by huphtur on 2005-12-20
I encountered same problem, so I installed [this script]("http://sourceforge.net/mailarchive/message.php?msg_id=2415558"), which help out a lot until the bug is fixed.

---

