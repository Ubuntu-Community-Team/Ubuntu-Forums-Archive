---
title: "To run firefox I have to sudo"
date: 2005-12-15
forum: General Help
---

### Post by Granduke on 2005-12-15
In the terminal I have to 'sudo firefox' to get it to run.  I imagine I have to change the permission on the program to run it from User.  If this is the solution- how would I accomplish this?

---

### Post by paulvandenberg on 2005-12-15
Did you run it as sudo the first time? If you, root got to be the owner of personal mozilla profile folder. I would try deleting your .mozilla folder and then running as a normal user. If my hunch is correct, you will need to sudo to delete your .mozilla folder. Midnight Commander comes in handy for this kind of stuff. If you don't have it, do 'apt-get install mc'. Then 'sudo mc' to delete your .mozilla folder. This is the easy way to delete folders with root authority. Make sure you delete .mozilla in your home folder, not root's (if it exists).

---

### Post by aysiu on 2005-12-15
Try this: ```
sudo chown -R granduke:granduke ~/.mozilla
firefox
``` If that doesn't work, try: ```
sudo mv ~/.mozilla ~/.mozilla_backup
firefox
```

---

### Post by Granduke on 2005-12-15
Thanks aysiu,
                    Your first suggestion did the trick.
I really appreciate your help.  I was about to give up on Linux a week ago but your assistance and that from others keep me on course.

---

### Post by aysiu on 2005-12-15
Awesome. Glad it worked out. Help others, too, if/when you can.

---

