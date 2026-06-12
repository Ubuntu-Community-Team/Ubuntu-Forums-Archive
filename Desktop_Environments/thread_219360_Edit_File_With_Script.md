---
title: "Edit File With Script"
date: 2006-07-19
forum: Desktop Environments
---

### Post by opticyclic on 2006-07-19
I am using Kommander to made installing KDM Themes easy.

This basically involves 2 steps:
Copying the directory that was downloaded from KDE-Look to /usr/share/apps/kdm/themes
Editing /etc/kde3/kdm/kdmrc so that the correct Theme is chosen.

My problem is that I don't know how to do find/replace with scripts.
This is mostly BASH scripts.

At the moment my script looks like this
```
@# see if we are running as root and throw dialog if not
@if(@exec(whoami) != "root") then
        @switch(
        @Message.warning(In order to run this you must run as root, Requires root, Open as root, Run anyway))
        @# handle dialog ouput
        @case(1)
        @exec(kdesu kmdr-executor @global(_KDDIR)/@global(_NAME))
        @dcop(@dcopid, MainApplication-Interface, "quit()")
        @case(2)
        @#nothing to do
        @end
@endif		

echo "
Copying directory to /usr/share/apps/kdm/themes.
"
sudo cp -r "@FileSelector1.text" "/usr/share/apps/kdm/themes/"
echo "
Setting as default in /etc/kde3/kdm/kdmrc
"

```

---

### Post by slider on 2006-07-20
You can drop the sudo since you are ensuring that the script is run as root.

Find and replace using sed

```
sed s/find/replace/g inputfile > outputfile 
```

Using perl

```
perl -pi.bak -e 's/find/replace/g' inputfile 
```

Perl does the find and replace in place and creates a backup file. Sed will work if you don't have access to perl.

On edit: you can also do it with shell builtins.

[http://www.arachnoid.com/linux/shell_programming.html](http://www.arachnoid.com/linux/shell_programming.html)****

---

