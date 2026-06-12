---
title: "Is this procedure safe?"
date: 2009-01-06
forum: General Help
---

### Post by Jammanuser on 2009-01-06
Hey, is the procedure described on [this page]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") safe? :) I noticed that it mentions a "rm" command, which is reportedly dangerous. :guitar:

Thanks in advance! :)

-jam man

:guitar:

---

### Post by jerome1232 on 2009-01-06
I didn't go over it in detail but the rm command was just to remove a backup of /home once everything is function correctly. So yes it should be safe. Everything looks fine although I don't understand what the find command is doing exactly.

 But I would recommend psychocats guide for this, it's much more complete

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Elfy on 2009-01-06
The rm command can be dangerous if it's used unwisely. But it's also perfectly suitable to use for it's intended purpose.

In this instance it is being used to remove and old backed up folder - the old home.

I would bear in mind this bit just before the rm command

> everything works fine, you can delete the &#8220;/old_home&#8221; directory by using:

rm doesn't send to the trash bin - it just deletes so make sure that everything is working before you run it. There's no need to delete the file quickly and leaving it for a few days would be advisable.

---

### Post by jrusso2 on 2009-01-06
Sigh this was what I was afraid of people believing common commands like rm are not to be used and are dangerous.  What other distro would say this?

rm is fine you just need to use caution and check twice what you are going to remove.  You should always have back ups.

---

### Post by Elfy on 2009-01-06
> **jrusso2 said:**
> Sigh this was what I was afraid of people believing common commands like rm are not to be used and are dangerous.  What other distro would say this?

rm is fine you just need to use caution and check twice what you are going to remove.  You should always have back ups.

Yep - pretend to be a tailor - measure twice - cut once.

---

### Post by jerome1232 on 2009-01-06
> **jrusso2 said:**
> Sigh this was what I was afraid of people believing common commands like rm are not to be used and are dangerous.  What other distro would say this?

rm is fine you just need to use caution and check twice what you are going to remove.  You should always have back ups.

Well yeah rm is only "dangerous" in the hands of someone that doesn't know how to navigate in a command line, and that doesn't keep regular backups. 

Ubuntu does attract users that tend to fall into this category.

I think "sudo rm -rf /*" (please don't run that on your production system, it recursively delete's your entire file structure, this includes mounted disks) is what is actually referred to as a dangerous command in the beginner sticky, not the rm command itself.

---

### Post by Jammanuser on 2009-01-06
> **jerome1232 said:**
> I didn't go over it in detail but the rm command was just to remove a backup of /home once everything is function correctly. So yes it should be safe. Everything looks fine although I don't understand what the find command is doing exactly.

 But I would recommend psychocats guide for this, it's much more complete

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Thanks for the info and the link. :) I just may use that guide instead of the other one...though its nice to know that the other one is perfectly safe (if of course, i follow the directions...which i would)! ;)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-06
> **jerome1232 said:**
> 
I think "**sudo rm -rf /***" (please don't run that on your production system, it recursively delete's your entire file structure, this includes mounted disks) is what is actually referred to as a dangerous command in the beginner sticky, not the rm command itself.

How about this one? It begins with the very command (well...almost! just without the "*" sign at the end) that you just warned against! :)

```
sudo rm -rf /home_backup
```

Its in the very guide that you pointed me to! :popcorn:

-Jam man

:guitar:

---

### Post by adult swim on 2009-01-06
yes, again it is removing the home backup

---

### Post by Jammanuser on 2009-01-06
> **adult swim said:**
> yes, again it is removing the home backup

Thanks. :) But if it does the same thing, why would it be different than the other command, i.e. having the "-rf" instead of just the "-r"? ;)

-Jam man

:guitar:

---

### Post by adult swim on 2009-01-06
it is the file name.  in the first guide, your home back up was named old_home, but in the new guide you followed, the backup was named home_backup.
EDIT:  the difference between -r and -rf is that the second one will ignore nonexistent files,and never prompt you about it.  basically it is more thorough

---

### Post by Jammanuser on 2009-01-06
> **adult swim said:**
> it is the file name.  in the first guide, your home back up was named old_home, but in the new guide you followed, the backup was named home_backup.


Yes, i realize that. but in the other command, it was "-r", not "-rf". :) What is the difference between the two? do they do different things, or are they the same? and if they are the same, why have them different? ;)

-Jam man

:guitar:

---

### Post by adult swim on 2009-01-06
> **Jammanuser said:**
> Yes, i realize that. but in the other command, it was "-r", not "-rf". :) What is the difference between the two? do they do different things, or are they the same? and if they are the same, why have them different? ;)

-Jam man

:guitar:

you edited on me! :D
i did the same :P

---

### Post by Jammanuser on 2009-01-06
> **adult swim said:**
> 
EDIT:  the difference between -r and -rf is that the second one will force the [COLOR="Red"]removal of nonexistent files[/COLOR] and never prompt you about it.  basically it is more thorough

Ahh...thanks! :) Appreciate it. :D But how can you remove something that doesn't exist? ;)

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-06
> **adult swim said:**
> you edited on me! :D
i did the same :P

Yeah...so? :lol:

-Jam man

:guitar:

---

### Post by adult swim on 2009-01-06
you know i totally screwed that up!  it should be ignore nonexistent files.  as to how that occurs, youll have to wait for a filesystem guru to show up.

---

### Post by Jammanuser on 2009-01-06
> **adult swim said:**
> you know i totally screwed that up!  it should be [COLOR="Red"]ignore nonexistent[/COLOR] files.  as to how that occurs, youll have to wait for a filesystem guru to show up.

Interesting. :?: But as before, why would there be a need to "ignore" **nonexistant** files? :) since they don't exist, i would think they would be already ignored! ;-)

Hahaha! :lol:

-Jam man

:guitar:

---

### Post by theozzlives on 2009-01-06
f=force, like the old DOS deltree command, Microsoft got rid of it cause it was so dangerous```
deltree /y c:\*.*
```would wipe your whole drive.

---

### Post by stchman on 2009-01-06
> **Jammanuser said:**
> Hey, is the procedure described on [this page]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") safe? :) I noticed that it mentions a "rm" command, which is reportedly dangerous. :guitar:

Thanks in advance! :)

-jam man

:guitar:

If you want to put your /home somewhere else you can do it through System--->Administration--->Users

There will be an option to put that users home in a different area.

---

### Post by Jammanuser on 2009-01-06
> **theozzlives said:**
> f=force, like the old DOS deltree command, Microsoft got rid of it cause it was so dangerous```
deltree /y c:\*.*
```would wipe your whole drive.

Thanks. So what's its basically doing then is **forcing** removal of the home backup? hmm...:-k

BTW, you may have a virus on your computer, because when i got an email about your message, i received a warning message multiple times i tried to open up the email, saying it contained a virus (i have AVG)...and so i deleted it, without opening it, and came here the normal way. ;) You may want to run a scan, to make sure you don't pass any viruses, via notification email, onto anyone else. :)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by jocko on 2009-01-06
> **Jammanuser said:**
> Thanks. :) But if it does the same thing, why would it be different than the other command, i.e. having the "-rf" instead of just the "-r"? ;)

-Jam man

:guitar:

The "f" in "-rf" just means "force". It forces the rm program to continue even if some files or folders can not be removed.
The most [COLOR=Red]dangerous[/COLOR] part of the command is the actual path you tell it to remove.
If you just use a path to a file/folder you know is [COLOR=SeaGreen]safe[/COLOR] to remove (such as [COLOR=SeaGreen]/home_backup[/COLOR]), nothing bad will happen.
If you type [COLOR=Red]/[/COLOR] or [COLOR=Red]/*[/COLOR] the command will try to remove your entire file system.
This can also happen if you accidentally type a space in the path; [COLOR=Red]/ home_backup[/COLOR] means the entire file system ([COLOR=Red]/[/COLOR]) and [COLOR=SeaGreen]home_backup[/COLOR], [COLOR=Red]/home backup[/COLOR] means [COLOR=Red]/home[/COLOR] and [COLOR=SeaGreen]backup[/COLOR] and so on...

So just make sure you understand what the command will do before you hit "enter", and you'll be safe. And never log in as root or use sudo unless you really need to...

---

### Post by Jammanuser on 2009-01-06
> **stchman said:**
> If you want to put your /home somewhere else you can do it through System--->Administration--->Users

There will be an option to put that users home in a different area.

Hey, thanks! :D I'll try that. Maybe i don't have to do it with the command line after all...:)

Much appreciation. :popcorn:

-Jam man

:guitar:

EDIT: Could i put it on a different **partition** though, using that method?

---

### Post by Jammanuser on 2009-01-06
> **jocko said:**
> The "f" in "-rf" just means "force". It forces the rm program to continue even if some files or folders can not be removed.
The most [COLOR=Red]dangerous[/COLOR] part of the command is the actual path you tell it to remove.
If you just use a path to a file/folder you know is [COLOR=SeaGreen]safe[/COLOR] to remove (such as [COLOR=SeaGreen]/home_backup[/COLOR]), nothing bad will happen.
If you type [COLOR=Red]/[/COLOR] or [COLOR=Red]/*[/COLOR] the command will try to remove your entire file system.
This can also happen if you accidentally type a space in the path; [COLOR=Red]/ home_backup[/COLOR] means the entire file system ([COLOR=Red]/[/COLOR]) and [COLOR=SeaGreen]home_backup[/COLOR], [COLOR=Red]/home backup[/COLOR] means [COLOR=Red]/home[/COLOR] and [COLOR=SeaGreen]backup[/COLOR] and so on...

So just make sure you understand what the command will do before you hit "enter", and you'll be safe. And never log in as root or use sudo unless you really need to...

Ahh...thanks for the clarification! :D But while we're at it...:) What does the "-r" mean then? :lol:

-Jam man

:guitar:

---

### Post by donkyhotay on 2009-01-06
The 'r' stands for recursive. It means it will delete all folders located within the folder you are trying to delete.

---

### Post by Jammanuser on 2009-01-06
> **donkyhotay said:**
> The 'r' stands for recursive. It means it will delete all folders located within the folder you are trying to delete.

Great! :D I really didn't expect to get this many answers! Thanks to you all! :p :D :) :P

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by jocko on 2009-01-06
> **Jammanuser said:**
> Ahh...thanks for the clarification! :D But while we're at it...:) What does the "-r" mean then? :lol:

-Jam man

:guitar:

"r" means "recursive", basically it tells rm to remove all files, folders and subfolders in the path.

So "rm file" will just remove files named "file", but stop with an error if it encounters a folder named "file", if the file "file" is read-only it would ask for confirmation before it is deleted and if there is no file named "file" it would stop with an error.

"rm -f file" would do the same thing, but would not stop with an error if there were no file named "file", and it would delete read-only files without asking for your confirmation (assuming you have permission to delete it). It would still stop if it found a folder named "file".

"rm -r file" would remove any file and folder named "file", including all files and subfolders in the folder "file". It would stop and ask for confirmation for read-only files, and stop with an error if it can't find any file or folder named "file".

"rm -rf" do the same as "rm -r", but never stops and asks for confirmations, and never stops with errors for missing files, so it will just continue until it has removed everything that matches your criteria (path and filename).

---

### Post by Slim Odds on 2009-01-06
"man rm" might be helpful

---

### Post by Jammanuser on 2009-01-06
> **jocko said:**
> "r" means "recursive", basically it tells rm to remove all files, folders and subfolders in the path.

So "rm file" will just remove files named "file", but stop with an error if it encounters a folder named "file", if the file "file" is read-only it would ask for confirmation before it is deleted and if there is no file named "file" it would stop with an error.

"rm -f file" would do the same thing, but would not stop with an error if there were no file named "file", and it would delete read-only files without asking for your confirmation (assuming you have permission to delete it). It would still stop if it found a folder named "file".

"rm -r file" would remove any file and folder named "file", including all files and subfolders in the folder "file". It would stop and ask for confirmation for read-only files, and stop with an error if it can't find any file or folder named "file".

"rm -rf" do the same as "rm -r", but never stops and asks for confirmations, and never stops with errors for missing files, so it will just continue until it has removed everything that matches your criteria (path and filename).

Ahh..ok! :) Thanks! :D I got it now. :popcorn: Thanks for the explanation. :)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-06
> **Slim Odds said:**
> "man rm" might be helpful

Good idea. :) I will keep that in mind...even though i think the others just explained the command well enough, and if i ran that, i would find out basically the same thing. Thanks. :D

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-06
> **stchman said:**
> If you want to put your /home somewhere else you can do it through System--->Administration--->Users


Thanks. :) That looks like it may work. :D However, if i wanted to put my /home folder on a different **partition** (which i do), how would i do this? could i just simply put "sda6" or whatever device string it is simply before the /home/*username* in the target path? would that work? also, since my MBR 4 primary partition limit is filled up, would that make a difference? or can it read partitions **outside** of the MBR?

Looking forward to your reply...

-Jam man

:guitar:

---

