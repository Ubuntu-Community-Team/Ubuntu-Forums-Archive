---
title: "how to save a file on the desktop of &quot;all users&quot;"
date: 2006-12-06
forum: Desktop Environments
---

### Post by armandocroce on 2006-12-06
Hello,
I would appreciate any help on the subject.
I am using Ubuntu 6.10 with the default gnome desktop installation.

More or less I need the equivalent of the "All user" folder of MS Windows.
Specifically the common "Desktop" folder where items saved there are visible to all the users of the computer.

I am sorry to annoy but I searched a lot without success.

Thank you,
armando

---

### Post by CatKiller on 2006-12-06
If you make a directory called Desktop in /etc/skel, anything that you put in there will be put on the Desktop of any **new** users. I don't know how to do the same for **existing** users, or even if it is possible automatically.

---

### Post by aysiu on 2006-12-06
Well, there are two questions here, really:

1. How do you create a shared folder all users can read and modify?

2. How do you get all users to have the same desktop folder?

In answer to #1, you should check out this thread:
[Permissions on a shared directory](http://www.ubuntuforums.org/showthread.php?p=832721#post832721)

It's a bit old, so I'm not sure if a simpler solution now exists two versions later (that solution was for Breezy Badger).

For #2, I would suspect symlinking would be your best option. Create a new folder called *shared*: ```
sudo mkdir /shared
``` Then link each users desktop to that folder: ```
sudo rm -r /home/*firstuser*/Desktop
sudo ln -s /shared /home/*firstuser*/Desktop
sudo rm -r /home/*seconduser*/Desktop
sudo ln -s /shared /home/*seconduser*/Desktop
sudo rm -r /home/*thirduser*/Desktop
sudo ln -s /shared /home/*thirduser*/Desktop
``` If you have more than three or four users, you may want to create some kind of shell script to do this for you.

---

