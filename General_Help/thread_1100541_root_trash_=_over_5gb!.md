---
title: "root trash = over 5gb!"
date: 2009-03-19
forum: General Help
---

### Post by sdowney717 on 2009-03-19
The only way I could even see it was to enable root graphical login


what do you normally do to delete this trash?

---

### Post by squee on 2009-03-19
in CLI

sudo nautilus

enter password and navigate to where the trash bin is. (IIRC /.local/share/Trash   Thats where it is on my home folder. presume its the same for root but i have no folder there so cant be sure.)

---

### Post by sdowney717 on 2009-03-19
interesting thing was, I could not delete this trash using gksu nautilus.
I could not even see this trash

I finally logged in as root, then I could see it. I could not simply empty all the trash at once. The first folder showed up with no name, perhaps that is why.

---

### Post by squee on 2009-03-19
just to check, did you see if there were hidden folders in the /.local ?

---

### Post by sdowney717 on 2009-03-19
the .local folder is hidden, the subfolders are not

What bothers me is why there was 5gb stuck in the root account trash.
Is this normal? Or was it just me?

---

### Post by Rallg on 2009-03-19
Here is how I deal with this issue:

1. Create a new text document, "empty-root-trash.sh" and put this text into it:

#!/bin/sh
sudo rm -rf /root/.local/share/Trash/

CAUTION: *sudo rm* is a powerful and dangerous command that deletes files or folders without further safeguard. You should never use it unless you understand the action. In this case, it deletes anything found in the root Trash folder.

2. Save the above document. Move it to the /usr/local/bin directory. If you need permission to do that, go to Terminal and open the file manager (in Ubuntu it is nautilus) with root permissions:

gksudo nautilus

then move the file. Once the file has been moved, if necessary change its permissions so that you, the user, can read and write, and everyone else can read only. Also check the box to allow execution as program.

3. Go to System > Preferences > Main Menu. In a likely place (such as Applications > System Tools) create a new item. Its type is Application in Terminal, name whatever you like (I use "Empty Root Trash") command "/usr/local/bin/empty-root-trash.sh" and if you like, give it a distinctive icon.

4. When you wish to empty the root trash, just choose from the menu. It will usually ask you for the password.

5. Sometimes, if you trash files while as root, they will accumulate in root trash, but not be emptied when you (as user) empty your own trash. The above shell script makes it easy to empty root trash without calling the file manager as root each time you need to do it.

---

### Post by partsdale on 2009-03-19
nice...

---

### Post by sdowney717 on 2009-03-19
yes thanks

---

### Post by chriskin on 2009-03-19
> **Rallg said:**
> Here is how I deal with this issue:

1. Create a new text document, "empty-root-trash.sh" and put this text into it:

#!/bin/sh
sudo rm -rf /root/.local/share/Trash/

CAUTION: *sudo rm* is a powerful and dangerous command that deletes files or folders without further safeguard. You should never use it unless you understand the action. In this case, it deletes anything found in the root Trash folder.

2. Save the above document. Move it to the /usr/local/bin directory. If you need permission to do that, go to Terminal and open the file manager (in Ubuntu it is nautilus) with root permissions:

gksudo nautilus

then move the file. Once the file has been moved, if necessary change its permissions so that you, the user, can read and write, and everyone else can read only. Also check the box to allow execution as program.

3. Go to System > Preferences > Main Menu. In a likely place (such as Applications > System Tools) create a new item. Its type is Application in Terminal, name whatever you like (I use "Empty Root Trash") command "/usr/local/bin/empty-root-trash.sh" and if you like, give it a distinctive icon.

4. When you wish to empty the root trash, just choose from the menu. It will usually ask you for the password.

5. Sometimes, if you trash files while as root, they will accumulate in root trash, but not be emptied when you (as user) empty your own trash. The above shell script makes it easy to empty root trash without calling the file manager as root each time you need to do it.

helped me too, i would give you a "thanks" if the option was still alive :)

:popcorn:

---

### Post by Therion on 2009-03-19
You could also use QuickStart.  The House Cleaning option empties root trash if you like.

[http://www.howtoforge.com/quickstart-the-swiss-army-knife-for-ubuntu-8.04-desktop](http://www.howtoforge.com/quickstart-the-swiss-army-knife-for-ubuntu-8.04-desktop)

---

### Post by Yashiro on 2009-03-19
Or Bleachbit.

---

