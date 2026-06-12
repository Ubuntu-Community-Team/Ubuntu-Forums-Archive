---
title: "Padlocks?"
date: 2009-02-25
forum: General Help
---

### Post by Prince1 on 2009-02-25
Hi.
 
I've just recently been having problems with my Web book laptop. Everytime I try to click or go to something it doesn't letg me, it comes up just blank. Also everything has padlocks on them? My daughter was playing with the laptop and done something to it and I'm not sure how to resolve it, can you guys sort it or let me know what's up with it? Thank you.

---

### Post by heindsight on 2009-02-25
sounds like file permissions were changed - a padlock emblem on a file usually means you have permission to read but not write it (a little box with an x emblem means you can't read the file).

If it's only files in your home directory that are affected, you can simply reset the permissions to some sane values using chmod in a terminal (or by right clicking the file, clicking properties and going to the permissions tab). see the manual:
```
man chmod
```

If other files (eg under /etc or /usr) are affected then you may have more serious problems (is there any chance your daughter could have had root access?).

---

### Post by scouser73 on 2009-02-25
> **Prince1 said:**
> Hi.
 
I've just recently been having problems with my Web book laptop. Everytime I try to click or go to something it doesn't letg me, it comes up just blank. Also everything has padlocks on them? My daughter was playing with the laptop and done something to it and I'm not sure how to resolve it, can you guys sort it or let me know what's up with it? Thank you.

You will need to open Terminal, go to **Accessories** and scroll to **Terminal**, Terminal will then open, then paste the command > gksudo nautilus Enter your password, and make your way to the files/folders that have the padlock on them. Place your cursor over the files/folders, and **Right Click** and scroll to **Properties**, and then click the **Permissions** tab. In the **Owner** drop-down menu find your name and select it and then go to the **Group** drop-down tab and do the same again, then click **Apply Permissions to Enclosed Files** and click **Close**, then come out of Nautilus, and also out of Terminal. You will now have access to the files/folders.

---

### Post by heindsight on 2009-02-25
> **scouser73 said:**
> You will need to open Terminal, go to **Accessories** and scroll to **Terminal**, Terminal will then open, then paste the command  Enter your password, and make your way to the files/folders that have the padlock on them. Place your cursor over the files/folders, and **Right Click** and scroll to **Properties**, and then click the **Permissions** tab. In the **Owner** drop-down menu find your name and select it and then go to the **Group** drop-down tab and do the same again, then click **Apply Permissions to Enclosed Files** and click **Close**, then come out of Nautilus, and also out of Terminal. You will now have access to the files/folders.

If only files in the home directory are affected, you shouldn't need root privileges to fix things (unless file ownerships have been changed).

Files outside your home directory should generally not belong to your user, so don't just haphazardly change ownership and permissions of files outside your home dir.

---

### Post by Prince1 on 2009-02-25
When I click on Terminal it comes up blank. Just a white box with nothing in it named 'Terminal' ?

---

### Post by heindsight on 2009-02-25
It's a bit difficult to know how to fix this without knowing exactly which files are affected.

What happens if you click on Places>Home Folder?
If that opens a file browser window showing your home directory, then you can change permissions of files in your home directory to whatever seems sensible to you (all the files in your home dir should belong to you and your personal group (the group with the same name as your username).

If the file browser opens, but you can't see the contents of your home directory, then try clicking the up button on the toolbar, you should then be able to see the contents of the /home directory, then go to the properties of your home directory, make sure it's owned by you and your group and set the "Folder Access" permissions so that the owner (you) can create and delete files, the group and others can access files (the "File Access" permissions should all be set to ---). Also make sure the Execute box is checked. Then close the Properties dialog, double click your home directory and then try to change the file permissions in there.

If you can't get the file browser working or you can't manage to set the permissions of your home dir, then try pressing Ctrl+Alt+F1, log in there and do:
```
ls -la ~
```
and post the output here.

---

### Post by Prince1 on 2009-02-26
No, nothing at all I click on responds, it's all just a white box, nothing at all in it. Is there anyway I can do a system restore?

---

### Post by heindsight on 2009-02-26
Does Ctrl+Alt+F1 not work either?

In that case, you could try to reboot into recovery mode (press Esc at the Grub prompt and choose recovery mode). You'll end up in a root shell, from where you can try to find out what changed, do an
```
ls -la /home/username
```
Unless your daughter had root access, she could not have done much more damage than changing permissions in your home directory, so you should only need to fix things in there (well of course she might also have deleted files, but at least the damage will be restricted to your home directory). In the worst case, if she did really serious damage to your home directory, you may have to recreate it, but then you'll be OK.

On the other hand, if your daughter had root access, there's no knowing what files she may have deleted or changed anywhere on the system, in which case you're probably best off reinstalling.

---

### Post by Prince1 on 2009-02-26
When I presser ctrl + alt + f1 the whole screen just went black, and nothing else happened.

---

### Post by heindsight on 2009-02-26
Try rebooting into recovery mode then

---

### Post by Prince1 on 2009-02-26
How exactly do I do that?

---

### Post by heindsight on 2009-02-26
Reboot the machine, when GRUB starts up, press Esc to get a menu, in that menu you'll see an option to boot Ubuntu in recovery mode, select that option and press Return to boot into recovery mode.

I haven't needed to do this in quite a while, but I believe you'll end up at a menu giving you various options, one of the options should be to start a root shell.

---

