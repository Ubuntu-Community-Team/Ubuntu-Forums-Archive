---
title: "best place to practice and learn terminal commands?"
date: 2009-02-04
forum: General Help
---

### Post by tednumber8 on 2009-02-04
I wish to go somewhere to practice and learn terminal commands

Is there any good places you know of?

Also would I need a VM inside ubuntu so as not to mess up any settings.

I await a response excited about learning the terminal

---

### Post by kerry_s on 2009-02-04
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

the normal terminal uses bash, but there are many kind of command types, dash,zsh,etc...

you need to be more descriptive.

---

### Post by mb_webguy on 2009-02-04
Feel free to practice on your own system.  To be on the safe side, you might want to create a new user account for this, so you don't risk accidentally altering your settings on your regular account.  Just follow a few basic guidelines, and you shouldn't be in any risk of doing anything disastrous to your system:

1)  Don't use run any command as root (using sudo, gksu, gksudo, or kdesu) unless you're *absolutely sure* what you're doing.  The commands that can do serious harm to your system (e.g. fdisk) generally require you to run them as root.  Any command that isn't run as root can only affect files and folders owned by your user account, or which the user otherwise has permission to alter.

2)  Be careful with the "rm" command.  Unlike desktop file managers, there is no Trash or Recycle Bin where you can recover accidentally deleted files.  If you delete a file with "rm", it's gone forever.  Be even more careful with "rm" when using the "-R" option, since this will delete files and folders recursively.  And never, *ever* run the "rm" command as root using the "-R" option unless you're absolutely, positively sure you know exactly what you're doing.

3)  Always make backups of files before you edit them.  Just use the "cp" command to copy the file with something like ".backup" appended to the end of the filename.  You may even want to add the date to the end of the filename in case you edit the file multiple times.  The gedit editor will automatically make a backup of a file (with a "~" appended to the filename), but don't rely on that, since it will only save the most recent previous version of the file.

4)  There is no four.

---

### Post by Sorivenul on 2009-02-04
[http://linuxcommand.org](http://linuxcommand.org) is another great site.

Also, look at the [community guide to BASH scripting]("https://help.ubuntu.com/community/Beginners/BashScripting"), and the [Education Focus Group Resources]("https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Education/Resources") page for *all* your needs.

See also:
[Using the Terminal]("https://help.ubuntu.com/community/UsingTheTerminal?highlight=(\bCategoryCommandLine\b)")
[Command Line HowTo]("https://help.ubuntu.com/community/CommandlineHowto?highlight=(\bCategoryCommandLine\b)")
[Advanced Command Line HowTo]("https://help.ubuntu.com/community/AdvancedCommandlineHowto?highlight=(\bCategoryCommandLine\b)")

Two more good things to know:
```
man
```
and 
```
apropos
```
"apropos" will tell you manpages you have available on a subject, i.e.:
```
apropos networking
```
From there, "man" will give you specific information about a particular subject, i.e.:
```
man ifconfig
```

---

### Post by fragos on 2009-02-04
I recommend you learn CLI by displaying infoprmation in the terminal and making changes in the GUI. When you're sure you understand a particular command you can start using it for changes. Don't ever enter a command unless you're sure what it does. CLI and trial and error don't mix well.

Given the differences between distributions distrobution agnostic guides are less helpful and can get you in trouble. The book I highly recommend is "Ubuntu Linux Toolbox". It teachs commands by explaining how to accomplish tasks. Some tasks require multiple commands and perhaps a preset configuration file. This book deals with that. Beware of CLI help in forums as it may come from what works on a different version of Ubuntu or perhaps a totally different distrobution.

---

