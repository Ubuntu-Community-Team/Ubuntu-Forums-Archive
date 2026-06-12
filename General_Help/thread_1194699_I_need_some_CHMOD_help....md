---
title: "I need some CHMOD help..."
date: 2009-06-22
forum: General Help
---

### Post by AoSteve on 2009-06-22
Somehow, someway...  My 17 year old brother who "thinks" he knows all with Linux had been trying to figure out CHMod in the command line.   I've looked at it and can't exactly figure out what to do here.

I have no write permissions in the /home folder, nor it's subfolders.   

What all CHMod commands will I have to run to restore the normal setup for the user allowances on this system?   I'll take this as a good opportunity to learn a bit more about CHMod.  The only one I'm at all familiar with is "chmod 777" for web servers and allowing FTP clients to read and write in specific directories..

---

### Post by ad_267 on 2009-06-22
Instead of using 777 etc you can also use symbolic mode. This means you use options like a+r for "add read permission for all users" or u+w to "add write permission for the user who ownes the file". You can also use - (minus) to remove permissions.

The -R (recursive) option is useful, this applies the permissions to all subdirectories. One thing to make sure you don't do is remove the execute permission from directories.

Another useful command is chown. You can use "chown -R $USER:$USER directory" to recursively set the owner and group of all files in a directory to your user.

Have a look at the man page (man chmod) for more information.

To fix your problem you should probably do:
```
sudo chown -R $USER:$USER $HOME
sudo chmod -R u+w $HOME
sudo chmod -R u+r $HOME
```

---

### Post by bjk03 on 2009-06-22
Try ```
sudo chmod -R /home/*yourusername* 644
```

That is assuming you own it.

---

### Post by mikewu on 2009-06-23
Please don't run sudo chmod -R /home/user 644

Directories must have the execute bit set inorder to perform any actions(ex. ls). The above command will deny access to all of your folders until you reset the permissions. (Also the 644 has to go before /home/user)

You shouldn't have write access to /home or other users. 

As to reseting permissions, assuming you haven't changed the permissions before

```
find /home/user -type d -exec chmod 755 {} +
find /home/user -type f -exec chmod u+rw,g=r,o=r {} +
```

The first sets permissions for directories, which need the execute bit and rw, while the second adds permissions for files.

The permissions might be incorrect for shell scripts, pipes and possibility other files. I would strongly recommend going through your home directory and ensuring you can access your files/folders.

---

### Post by AoSteve on 2009-06-23
I can access them all just fine, it has full reading rights, but it can't write to any files.  A good example is like the .conkyrc file in it.  It cannot be saved with gedit unless it's ran in a terminal like : sudo gedit .conkyrc

Also, it won't save the display settings.   No errors on boot or anything, just noticeable when trying to save a file or whatnot.

---

### Post by AoSteve on 2009-06-23
Here's an odd one...  Those commands simply respond like this :

```

[FONT=monospace]chmod: changing permissions of `/home/steve/.conkyrc~': Operation not permitted
chmod: changing permissions of `/home/steve/.conkyrc': Operation not permitted
chmod: changing permissions of `/home/steve/Desktop/Random Stuff/conky.conforig': Operation not permitted

```

Conky isn't running on the system..  I just wonder why it's doing that...   LOL
[/FONT]

---

### Post by ad_267 on 2009-06-23
That could be because those files aren't owned by you. You can do "ls -l ~/.conkyrc" to find out what's going on. If you're not the owner you can run "sudo chown -R $USER:$USER $HOME" first then run the commands again.

---

### Post by AoSteve on 2009-06-23
Well, I think that's right.   I changed those over, it looks like the rest is working correctly.   He must have done something to his conky scripts and not been able to save and started to CHMod the place LOL!    He's pretty much the only one that uses this system so he can't blame meh wifer! :)

Thanks for your help guys!

---

