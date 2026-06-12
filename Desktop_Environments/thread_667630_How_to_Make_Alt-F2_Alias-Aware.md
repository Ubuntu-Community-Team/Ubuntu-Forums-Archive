---
title: "How to Make Alt-F2 Alias-Aware"
date: 2008-01-14
forum: Desktop Environments
---

### Post by jjsonp on 2008-01-14
In trying to make some Alt-F2 shortcut commands (as discussed in [this thread]("http://ubuntuforums.org/showthread.php?t=667342")) it became apparent that adding aliases to .bashrc (or via .bash_aliases) worked fine in the terminal, but did not work when called from Alt-F2. [One comment]("http://ubuntuforums.org/showpost.php?p=4135424&postcount=27") mentioned perhaps Alt-F2 uses some shell besides bash but I have no idea.

Anyone know how to tweak things so that Alt-F2 will interpret aliases? Thanks.

---

### Post by fwojciec on 2008-01-16
Well, that would be a hackish way of going about it, but you could always create tiny little scripts instead of aliases, name them appropriately, make them executable, and put them in one of the directories included in $PATH (/usr/local/bin for example)

Here is an example:

write a script in your preferred text editor:
> #!/bin/bash
gnome-terminal -x htop

save the file (as, for example "sysinfo" in your home directory) 
make it executable: chmod +x ~/sysinfo
move it to /usr/local/bin:  sudo mv ~/sysinfo /usr/local/bin
voila -- you can run it using Alt-F2 + sysinfo

For this particular script to work you'd need to have "htop" installed of course, but you get the general idea...

---

### Post by jjsonp on 2008-01-17
Thanks; that is exactly what I wound up doing.

The alias method (had it worked) seemed simpler in that I'd just be modifying a single text file, but actually I think this way is more intuitive to manage.

Also I've discovered that when I want to create a new 'launchword' script, I can just (gksudo) browse to the folder I've stored them in, copy an existing one, edit the command and choose a name, and that's it...the copy already has executable permissions.

---

### Post by fwojciec on 2008-01-17
you can make a nice little launchword with "gksudo nautilus [/path/to/launchword/directory]" (I think that's how nautilus works, I don't have it installed so I can't check) in it to make the process even more simple :D
or you could make a "template" launchword and make a launchword that would open it in a text editor (also using gksudo) and then just use "save as" to create new launchwords...

linux/bash is great like this, you can customize how your system works to a great extent using scripts.

---

### Post by jjsonp on 2008-01-17
Ah, great idea! That will definitely take me to the next level for automating this.

I don't know if you are forced to use Windows, but I use it at work and this excellent free tool [SlickRun]("http://www.bayden.com/SlickRun/") performs all of the functions we are discussing in a very simple and intuitive way. I've grown addicted to it on Windows so I'm trying to reproduce the enormous assistance it provides. Almost there!

---

### Post by fwojciec on 2008-01-17
Luckily I don't really have the need to use Windows anymore -- I still have it installed on one of the partitions though... somewhere...

You might want to check this app for linux -- [http://www.bazon.net/mishoo/gmrun.epl]("http://www.bazon.net/mishoo/gmrun.epl")
It should be in the repos -- I used to use it in openbox and it's minimalistic and very configurable, it also works with web pages, has tab completion of commands and history, and can open specified files in the terminal for you.  You might like it more than the default gnome alt-F2 behavior -- you'd need to figure out how to bind it to a key combination though... Gnome should have the ability to configure it somehow.

---

