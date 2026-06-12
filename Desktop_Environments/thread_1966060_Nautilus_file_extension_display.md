---
title: "Nautilus file extension display"
date: 2012-04-26
forum: Desktop Environments
---

### Post by VanillaMozilla on 2012-04-26
I noticed that Nautilus (Places) under Oneiric does not seem to display file extensions!  There is a verbose description of the file type, but I couldn't find a way to display the extension (the part of the file name after the dot).

Please tell me I missed something.  This is an essential part of the file name.

---

### Post by papibe on 2012-04-26
Hi VanillaMozilla.

Do you refer to hidden files? The ones that start with a dot?

Or regular extensions like .txt .sh, etc?

Regards.

---

### Post by VanillaMozilla on 2012-04-26
No.  There are no hidden files here that I've noticed.

Ohmygosh, I see I'm getting the same problem in Natty, with Nautilus 3.32.2.1.  Look at /usr/share/applications, then look at the same directory with a ls command in the terminal.  The Nautilus display is very different from the actual list of files.  What the heck is going on?

---

### Post by mc4man on 2012-04-26
The .desktops in /usr/share/applications have an actual file name & a 'display' name that's determined by the Name= line in the .desktop

Ex. "Home Folder" is this if you were to open in a text editor, see screen
Actual name is nautilus-home.desktop, Name= is Home Folder

This is the way .desktops are.

---

### Post by VanillaMozilla on 2012-04-27
I see.  Is there any way for the *File* Manager to display the actual *file* name?  And are there any other cases in which Nautilus does not display the file name?

---

### Post by VanillaMozilla on 2012-04-27
OK, I get it.  It's trying to be helpful by displaying the file contents in place of the file name.  Given the choice, I would opt for consistency instead.

For anyone reading this and wanting an answer, you can view the file names with a Web browser or file picker, but your options for managing the files (e.g., deleting, renaming) are limited.

Thanks, your reply is appreciated, mc4man, even if the irregularity is not.

---

### Post by mc4man on 2012-04-27
It's not really an irregularity, it's how it works & should work
Never really tried to understand the exact 'how it's done' but you can see the results if you take a closer look

If you create a valid .desktop anywhere in your Home dir. it will show actual file name & can't be executed by d. left clicking on unless it's then marked as executable

However any .desktop that's created, installed  or placed in /usr/share/ or /usr/local/share/ or any directory within them will automatically show the Icon=, Name= & can be executed by any user from d. left click even though the .desktop isn't  set as executable
(as long as it remains  in /usr/share/.. or /usr/local/share/..

.desktops in any other location will show as <whatever>.desktop unless explicitly set as executable

---

### Post by VanillaMozilla on 2012-04-27
Right.  A special rule for every case.  (I wonder how many others there are.)  The really annoying thing is that's by design.  No wonder our computers are too damned complicated.

---

### Post by Krytarik on 2012-04-28
> **VanillaMozilla said:**
> OK, I get it.  It's trying to be helpful by displaying the file contents in place of the file name.  Given the choice, I would opt for consistency instead.
Do you know how your "consistency" would actually look like?: Desktop icons displayed with their actual file names, that thing with the .desktop appended, and with some generic icon instead of those fancy ones. :P In case you don't know, Nautilus is also handling the desktop, if you have icons enabled there.

Regards.

---

### Post by VanillaMozilla on 2012-04-28
KDE gets it right.  Icons *and* file names.

I'm looking at it right now.  It's actually kind of pretty too.  Hmm....

Thanks for your help, though.  I really do appreciate it.

---

