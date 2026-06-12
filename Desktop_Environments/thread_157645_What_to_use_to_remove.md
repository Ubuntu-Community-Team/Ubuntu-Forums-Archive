---
title: "What to use to remove"
date: 2006-04-09
forum: Desktop Environments
---

### Post by phil66 on 2006-04-09
left over files from removed package.

I have 25 files left over from an attempt to install avg7-linux

I have tried using apt-get,rmdir,rm -r and none of these are finding the files.

Files are found using find files and folder.

I cannot remove from that location as I get access denied.

I open file from found and try to delete but nothing happens.
[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)
Your help needed Please

Ray

---

### Post by stanthecaddy22 on 2006-04-09
you could try dpkg,

possibly using 'dpkg -r --purge [packagename]'

---

### Post by Ramses de Norre on 2006-04-09
The acces denied errors are most likely caused because the files are owned by root. You'll need to use sudo to remove them. And you should use sudo apt-get remove --purge file_name or sudo dpkg -r --purge file_name to remove them completely.

---

### Post by ice60 on 2006-04-09
another really good program is called GtkOrphan, it's in Synaptic. once it's installed you'll find it at System>Administration>Remove Orphaned Packages.

[img]http://img469.imageshack.us/img469/9616/gtkorphan0rl.png[/img]

there's also this HowTo, it mentions deborphan, but i prefer GtkOrphan. just keep on running it until there are no more orphaned libraries. :cool: 
[http://www.ubuntuforums.org/showthread.php?t=140920&highlight=deborphan](http://www.ubuntuforums.org/showthread.php?t=140920&highlight=deborphan)

there's also a program called FSLint, in Synaptic, which help remove alot of rubbish. just be very careful about removing Duplicates unless you are 100% certain you know what you are doing.

[img]http://img425.imageshack.us/img425/4052/screenshotfslint2wl.png[/img]

---

### Post by phil66 on 2006-04-10
[QUOTE=stanthecaddy22]you could try dpkg,

possibly using 'dpkg -r --purge [packagename]'[/QUOTE]

Tried this and got error return "conflicting action --purge and --remove"

Remove -r and run got error" package not installed"

Thanks for the help

---

### Post by phil66 on 2006-04-10
[QUOTE=Ramses de Norre]The acces denied errors are most likely caused because the files are owned by root. You'll need to use sudo to remove them. And you should use sudo apt-get remove --purge file_name or sudo dpkg -r --purge file_name to remove them completely.[/QUOTE]

Running all commands as root the apt-get you suggested returns error
"--purge file_avg7 is not installed"
dpkg command returns" couldn't find package"

These errors are what I have gotten on anything I try
Thanks for the help

---

### Post by phil66 on 2006-04-10
[QUOTE=ice60]another really good program is called GtkOrphan, it's in Synaptic. once it's installed you'll find it at System>Administration>Remove Orphaned Packages.

[img]http://img469.imageshack.us/img469/9616/gtkorphan0rl.png[/img]

there's also this HowTo, it mentions deborphan, but i prefer GtkOrphan. just keep on running it until there are no more orphaned libraries. :cool: 
[http://www.ubuntuforums.org/showthread.php?t=140920&highlight=deborphan](http://www.ubuntuforums.org/showthread.php?t=140920&highlight=deborphan)

there's also a program called FSLint, in Synaptic, which help remove alot of rubbish. just be very careful about removing Duplicates unless you are 100% certain you know what you are doing.

[img]http://img425.imageshack.us/img425/4052/screenshotfslint2wl.png[/img][/QUOTE]

I have all the repositories from /etc/apt/sources.list updated yet I must be missing one as gtkorphan or fslint are not in the synpatic manager.

Deborphan was available in synpathic so I installed and also set up a filter for orphans so as I could see what they wanted to delete before actually deleting.

The only entries in the deborphan area of synpatic manager were some gstreamer and a couple of lib. There were not any files that I have been trying to delete.

Do I need to download gtkorphan and the dependencies files from Debian website.
Will this show me more files than deborphan has showed.

Thanks for the help

---

