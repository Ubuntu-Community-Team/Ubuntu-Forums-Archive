---
title: "Pasting into a folder i don't have permissions for"
date: 2005-04-09
forum: Desktop Environments
---

### Post by Giawa on 2005-04-09
I want to copy and past into a locked folder that I don't have permissions for. How can I copy it? I am the main user, I want to log in as root so I have these privledges. How could I do this? Or can I copy it using root terminal and paste it into my folder? I'm soooo confuzzled!

Giawa

---

### Post by edubarr on 2005-04-09
You can do this using the terminal. Just type 'sudo cp file-to-be-copied /full/path/to/folder/'. Another way would be to just change the permissions of the folder using chmod, but since the folder is locked, there must be a reason for this and this second option is not recomended unless you know what you are doing.

I really don't have a clue how to do it using nautilus, though... probably running 'sudo nautilus' will give you access to a root-priviledged nautilus.

---

### Post by Giawa on 2005-04-09
Awesome, sudo nautilus worked perfectly!  O:) thanks!

Giawa

---

