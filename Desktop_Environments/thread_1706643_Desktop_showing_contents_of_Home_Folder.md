---
title: "Desktop showing contents of Home Folder"
date: 2011-03-14
forum: Desktop Environments
---

### Post by manishlogan on 2011-03-14
Today I uninstalled Zimbra desktop from my Ubuntu 10.04. After doing it, I am facing several problems due to changes in system configuration.

My Home Folder contents are shown on Desktop and if I delete them from Desktop, they are also deleted from the Home Folder. I don't understand why this is happening. Kindly help me.

Also, from the side pane in Explorer, the option of Home Folder is not present any more. When ever I go to Home Folder, on the side pane is shows that I am on desktop and the location bar shows that I am in Home Folder.

I need help as soon as possible. Thanks.

---

### Post by mcduck on 2011-03-14
Do you still have a "Desktop" directory inside your home? If not, create it.

Open gconf-editor, browse to *apps/nautilus/preferences*, and make sure "*desktop_is_home_dir*"-key is not enabled.

If that doesn't solve the problem, check the *~/.config/user-dirs.dirs* -file, and make sure it has the following entry in it:

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

---

### Post by morean51 on 2011-03-14
thank you for the info

---

### Post by Zevaka on 2011-03-14
i swear [ubuntu-tweak]("http://ubuntu-tweak.com/") has nice GUI for editing this thing (and many more, of course). 
you can choose contents of what folder should appear on desktop.

---

### Post by rvchari on 2011-03-14
> **mcduck said:**
> Do you still have a "Desktop" directory inside your home? If not, create it.

Open gconf-editor, browse to *apps/nautilus/preferences*, and make sure "*desktop_is_home_dir*"-key is not enabled.

If that doesn't solve the problem, check the *~/.config/user-dirs.dirs* -file, and make sure it has the following entry in it:

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

months back i had posted a thread related to the same problem. i tried everything but to check the .config folder. finally i deleted that user account and  created new ! (ofcourse after backing up everything from my home directory !

now if the problem pops up again, i ll note this down for double check !
thanks buddy...

---

### Post by Copper Bezel on 2011-03-14
Zevaka - Ubuntu Tweak is a good package and does include a lot of nice, more GUI ways of handling things, but it doesn't include everything. It's still good to know your way around gconf-editor. 

Of course, the ideal would be if Gnome shipped an actual, modern, GUI interface (something laid out like Ubuntu Tweak) to handle all of its obscure and needlessly hidden features, but, ah. = )

---

### Post by manishlogan on 2011-03-16
> **mcduck said:**
> Do you still have a "Desktop" directory inside your home? If not, create it.

Open gconf-editor, browse to *apps/nautilus/preferences*, and make sure "*desktop_is_home_dir*"-key is not enabled.

If that doesn't solve the problem, check the *~/.config/user-dirs.dirs* -file, and make sure it has the following entry in it:

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```
Well, I did both the things, but still the problem is not solved.

---

### Post by rvchari on 2011-03-16
when nothing works (may be some more details needed for the forum members to help on the exact problem) the easiest and fastest way to get out of this is 2 options.
a) it you dont wish to have a new user account, then go to gconf-editor > nautilus > preferences and uncheck the show desktop items box. your desktop will be clean.
b) create a new user, copy all the personal files and data from ur current home directory to the new user with sudo command.
give ownership of the files that are transfered to the new user.
log out and log in with new user account.
if everything is fine then simply userdel the old problematic account.

BEFORE YOU DO THIS, could u simply delete .gconf / .gconf2 and .nautilus .config .cache files from your home directory ? try doing this and logout and re log in.

---

### Post by Krytarik on 2011-03-16
Please, before you do anything harsh like this, check if the directory "Desktop" is an actual symlink to your home directory.
Enter in a terminal:
```
ls -al ~/Desktop
```

---

### Post by manishlogan on 2011-03-20
Well, when I rebooted my laptop, it worked. Thanks a ton.

---

### Post by r!ots on 2011-05-25
> **mcduck said:**
> If that doesn't solve the problem, check the *~/.config/user-dirs.dirs* -file, and make sure it has the following entry in it:

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

That solved the problem for me. Thank you!!

My desktop showed my home folder content the boot after cleaning my desktop up. Very strange, but luckily no harm was done, since the folder was empty.

---

### Post by r!ots on 2011-07-03
Since happening for the first time about a month ago, my Desktop folder gets deleted and shows the content of my home folder again and again. It happens randomly every few days.

To restore it, I have to edit the *~/.config/user-dirs.dirs*-file and change the line ```
XDG_DESKTOP_DIR="$HOME/"
``` to ```
XDG_DESKTOP_DIR="$HOME/Desktop"
```And I need to recreate the Desktop folder as well.

It seems as if the *~/.config/user-dirs.dirs*-file gets overridden with some default file. The other directory-entries I made in the file are reverted as well.

Does anyone know why this is happening and how I can stop it? Am I the only one, experiencing this problem?

I'm thinking about reporting it as a bug, but I don't really know where. Could you point me to the right place?? What do you think, would be some useful information to add to the bug report? Since I can't reproduce the problem intentionally, I'm a bit lost on how to proceed.

---

### Post by Krytarik on 2011-07-03
r!ots, try placing the file "/etc/X11/Xsession.d/60xdg-user-dirs-update" somewhere else, to prevent "xdg-user-dirs-update" from being run at the start of an X session. This is part of the package "xdg-user-dirs". So, if this works, file a bug report here, there is also a similar report filed already:
[https://bugs.launchpad.net/ubuntu/+source/xdg-user-dirs](https://bugs.launchpad.net/ubuntu/+source/xdg-user-dirs)

You need to know that there is another package involved, "xdg-user-dirs-gtk", which has the item "User folders update" in "Startup Applications". This is meant to ensure that your Bookmarks are updated if the user directories are changed. Bug reports against this package are here:
[https://bugs.launchpad.net/ubuntu/+source/xdg-user-dirs-gtk](https://bugs.launchpad.net/ubuntu/+source/xdg-user-dirs-gtk)

Greetings.

---

### Post by r!ots on 2011-07-06
Hi Krytarik,

thanks for your reply. By now, I think it doesn't have anything to do with the "xdg-user-dirs"-package or file.

I noticed that my Desktop folder gets deleted randomly. For example it vanished, when I closed Firefox. So it makes sense, that my user directories get updated on the next boot, since I don't have a Desktop folder anymore.

I will start a new thread concerning this, since this one is marked as solved and my problem doesn't seem to have much in common with the original one.

Thanks for your fast reply, anyway.

Greetings.

---

