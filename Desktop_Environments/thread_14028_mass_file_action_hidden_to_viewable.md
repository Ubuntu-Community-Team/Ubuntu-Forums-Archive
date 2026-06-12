---
title: "mass file action: hidden to viewable"
date: 2005-02-04
forum: Desktop Environments
---

### Post by machiner on 2005-02-04
Can I change all of the (recursive) hidden files in a directory to be viewable?

Sorry if there was a thread earlier .. I've got 999 things going on and kids!

THanks

---

### Post by valadil on 2005-02-04
You can but that would be a very bad idea.  What makes a file hidden is its name.  Files that begin with periods don't get shown by default in ls or a file manager.

Usually whats in those files is config information for various programs.  The programs know to look to those files in particular for their settings.  If .gnome/ suddenly becomes gnome/ then your window manager won't be able to find its configurations.

What would be a better idea is to view hidden files by default.  I'm not sure where that option is in nautilus (try checkign gconf-editor) but if you run ls -a isntead of ls it will show you all files.  You can set ls to always show hidden files with an alias:
alias ls='ls -a'

---

### Post by Yukonjack on 2005-02-04
When you are in nautilus file browser click on edit preferences-->view, click the check box view hidden files and backup files.

---

### Post by machiner on 2005-02-04
I'm actually looking for some file utility to mass rename all the . (hidden) files in a directory.

I've tried on or 2 today - no luck.

I want to recursively rename files in a folder from hidden to visible.

---

### Post by Yukonjack on 2005-02-04
Oh I see what you mean, I'll keep me eye open in case I come across something.

---

### Post by valadil on 2005-02-05
Here's something to try, but don't say I didn't warn ya:
 for i in `ls -a` ; do mv $i `echo $i | sed -e 's/^.//' ` ; done

Keep in mind that this doesn't do anything for files with a space in their name and it certainly isn't recursive.  For one line its not bad though :-P

---

### Post by machiner on 2005-02-05
Thanks -V. I tried something like that already - moving all .files to a spot...yech!

Evolution will recognize mbox files deposited into its mail/local folder.

Example: I have a zillion accounts and folders in my /mail folder (for kmail)  but as we all know, when you "send page"  from firefox, nothing is filled into any fields in kmail - only evoultion works well here.  Same for other mailto: actions.

So - I want to copy all of my /mail directory folders (& files - which are accounts) into my evolution folder.  Of course, copy/paste works well...but evolution won't see the mail folders when it opens up....because they are hidden.

See?


SO - instead of taking 3 hours to rename every single file I was hoping for a batch renamer to do the job (recursively) for me.

I know it's dooable.  SO - how?

grazzi

---

