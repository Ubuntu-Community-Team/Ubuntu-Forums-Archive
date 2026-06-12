---
title: "HELP!  ohcrapohcrapohcrap..."
date: 2006-01-08
forum: General Help
---

### Post by avox on 2006-01-08
I was trying to change the permissions to all the files in my document folder at once.  This was what I typed;

'chmod -R 644 docs'

this is what it gave me:

'chmod: `docs': Permission denied'

I used sudo, cause I didn't know why it wouldn't let me do that to my own folder and files.

it gave me an a-ok, I thought (an open terminal prompt), and I browsed to the folder in Nautilus and...

every file and folder is listed as an 'unknown type' with 'unknown' permissions, no file size!!!!!!  NOTHING WILL EXECUTE/OPEN!!!   and it won't even 'cd' to it in a terminal!  I'm sure you can guess from the folder name, but there were more than a few important documents in there!!

Does anybody have a clue what happened/what I can do to restore the folder?  Is there a log somewhere to look through??  Please, I'm begging you guys here, you're my only hope...  *bows*  m(_ _)m

---

### Post by rubinstein on 2006-01-08
try sudo chmod -R 777 docs 
that should help

---

### Post by avox on 2006-01-08
worked like a charm!  THANK YOU.  oh god i was scared for a second there.  i can't believe i haven't created a backup of that folder yet...  so that i don't make the same mistake again, what in the world did i do wrong?

---

### Post by fct on 2006-01-08
A directory, apart from the "read" permission, must have an "execute" permission so that you can get into it. The 644 removed the execution privileges. 777 restored them (actually, it made that readable and writable to every user in the system too).

You might want to try 755 or 754. But I'm not sure they work, since I use the human notation ("chmod u+rwx file" for example).

---

### Post by Lord Illidan on 2006-01-08
Try running ```
man chmod
``` to give you more help about what chmod does. I also agree that the human readable format is better for us humanbeings.

Also, next time, please rename the title of your thread to something more descriptive like : Problem with Permissions.

---

### Post by lamego on 2006-01-08
And next time do not execute a command specially with sudo unless you know what you are doing...

---

### Post by avox on 2006-01-08
aaah, so directories need to be executed as well.  i figured that was only an application thing.

---

### Post by jbro on 2006-01-08
Doing 'chmod 644 ...' removed execute privileges from the directory. Now you might say, of course, why would I want to execute a directory? The answer is that for directories the execute privilege allows you to scan into a directory. Without this privilege you won't be able to get much information about the directory or its contents. Doing 'chmod 777 ...' restored this privilege and fixed things. 

Basically the three digits correspond to user, group, and world privileges. For each digit you can have a value that is any combination (summation) of 4, 2, and 1, where 4 = read privilege, 2 = write privilege, and 1 = execute privilege. So 'chmod 644' gives you (user) read and write privileges, your group read and write privileges and world read and write privileges (for a normal file.) For more information you might try 'man chmod' from a terminal window to get the whole story. It is a bit abstruse, but very informative.

Regards,
jbro

---

### Post by xxsiriusxburnxx on 2006-01-08
Another way I have found to gain permissions under Ubuntu for ANY file or folder under a single session is to go to system/sys tools/ disks, from here click on the partitions secting choose your root partition and choose browse, before getting into this app it will ask for the root password, from there when you browse you will have full read/write access to all files and folders

---

### Post by Soleil-Raid on 2006-01-08
[QUOTE=rubinstein]try sudo chmod -R 777 docs 
that should help[/QUOTE]

Ew. Don't use 777. You should use 700 unless you want everyone to be able read everything, in which case you should use 755.

777 would mean _anyone_ can WRITE to your documents. This is a bad thing. It's not really an issue on a single user system where you've got the only login to the system, but it's an horrible habit to get into.

---

### Post by spartas on 2006-01-08
[QUOTE=Soleil-Raid]Ew. Don't use 777. You should use 700 unless you want everyone to be able read everything, in which case you should use 755.

777 would mean _anyone_ can WRITE to your documents. This is a bad thing. It's not really an issue on a single user system where you've got the only login to the system, but it's an horrible habit to get into.[/QUOTE]

Optimually you should use 770 to give users in your group the same permissions as yourself.  This is useful for accounts that act as aliases to your own, because usually the folder's group is also your username as well.

---

