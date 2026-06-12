---
title: "Rename /home/USERNAME"
date: 2007-03-29
forum: Desktop Environments
---

### Post by dkaddict on 2007-03-29
A quick question. Any replies are received with thanx.

All I want to know is...

my /home folder is currently on its own partition (hda1) and is called

'/home/dk

is it possible for me to change the name of this folder to...

/home/dkaddict

?

I am unsure about just changing it because I think it will render a lot of stuff unusable as a result of the change in the path to icons, apps, etc

Is there a safe way to do it?

thanx

dkaddict

---

### Post by ComplexNumber on 2007-03-29
manually changing the name will render a lot of stuff unusable. i would recommend that you do the following instead:
-create the username _and_ user group called dkaddict 
-add your newly created username to the 'admin' group. this is so that your new username can use sudo.
-go into failsafe terminal and copy(ie they must be copied. DO NOT move. this is so that you have a perfectly usable dk home directory that you can go back to if things get messed up) any documents and folders that you want to keep over to your newly created dkaddict home directory. once they are in the newly created home folder, they should take on the attributes of the new user automatically (ie they should be owned by username dkaddict  and user group dkaddict, except those that happen to be owned for root for whatever reason). i would personally leave most of the invisible dot folders (eg especially the 'system' folders such as .gconf, .gconfd, .gnome2, .metacity, .nautilus, etc) in your old username.  folders that belong to applications such as .mozilla that you want to keep the settings for will only be created anew the first time you run firefox in your new user directory. therefore, its ok to copy over .mozilla, .tomboy, etc before you have run them for the very first time in your newly created user directory.



**DO NOT **get rid of your old username for a while until you are entirely happy that everything is ok.

---

### Post by tho on 2007-03-29
Should be possible without any breakage if you simply symlink /home/dk to /home/dkaddict.

# ln -s /home/dk /home/dkaddict

If you want to change your username, make sure to change the permissions for your files in your home directory aswell.

# chown -R newuser:newgroup /home/dkaddict

---

### Post by ComplexNumber on 2007-03-29
> **tho said:**
> Should be possible without any breakage if you simply symlink /home/dk to /home/dkaddict.

$ man ln
but that would mean that everything in dkaddict home directory still has the username and usergroup dk. the only thing that would change would be the name of the directory. i don't think thats what he's hoping to do.

---

### Post by tho on 2007-03-29
> **ComplexNumber said:**
> but that would mean that everything in dkaddict home directory still has the username and usergroup dk. the only thing that would change would be the name of the directory. i don't think thats what he's hoping to do.

See my edit :)

---

### Post by ComplexNumber on 2007-03-29
don't forget the 'sudo' part before the ln and chown. ;). then there's the problem of the newly created username not being able to use sudo. and the problem of the new username and usergroup not being recognised anywhere. changing the username and user group like that isn't healthy.

---

### Post by tho on 2007-03-29
> **ComplexNumber said:**
> don't forget the 'sudo' part before the ln and chown. ;). then there's the problem of the newly created username not being able to use sudo. and the problem of the new username and usergroup not being recognised anywhere. changing the username and user group like that isn't healthy.

Well, I presumed that he had already added his new user and added himself to the relevant groups. Perhaps I should have mentioned that. ;)

Let's do it step-by-step:

1. Add a new user 'newuser' with primary group 'newgroup' (Using either 'adduser' from a terminal, or the graphical tool found in System -> Administration -> Users and groups?)

2. Put 'newuser' in the relevant groups (Using either 'gpasswd' from a terminal, or the graphical tool found in System -> Administration -> Users and groups?)

3. Remove the /home/newuser directory and make a symbolic link from /home/olduser to /home/newuser:
$ sudo rm -r /home/newuser
$ sudo ln -s /home/olduser /home/newuser

4. Change ownership of the files in /home/olduser to newuser:newgroup:
$ sudo chown -R newuser:newgroup /home/olduser

5. Change ownership of the symbolic link /home/newuser to newuser:newgroup:
$ sudo chown newuser:newgroup /home/newuser

I don't think using a symlink as a home directory would cause any breakage, but I can't be entirely sure.

I would like to add that I think adding the new user and moving over the bits and pieces you want to keep (changing ownership of the files as you go), is absolutely the prefered way to go.

---

### Post by dkaddict on 2007-03-30
Wow. I didn't think I would get so many replies.

Big thanx for them all.

I am going to have a go at doing it when I get home this evening.

I sort of knew that the  ~ .kde etc files would give me a problem in renaming my /home folder.

I will do it later as I said and post the results as soon as.

Again, many thanx for all of your replies and time

dkaddict

ps, would I be able to change the permissions in one hit? I mean doing, right click /home/dk> properties>permissions>change>apply to all sub-folders&files?

---

