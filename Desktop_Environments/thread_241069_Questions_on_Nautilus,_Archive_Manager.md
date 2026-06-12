---
title: "Questions on Nautilus, Archive Manager"
date: 2006-08-21
forum: Desktop Environments
---

### Post by straypackets on 2006-08-21
Two questions on opening archives and the filemanager:

1. When I click on the icon of an archived file, I want it to default to creating a folder with the same name as the archive and then extract the archive into that folder. What happens now is that Archive Manager launches. If I select its "extract" option it unpacks the archive and strews the files all over the Desktop.  If I select "open", it simply launches another instance of itself.  Not helpful.  How can I get the behavior I want?


2.  I want to move a folder into a directory owned by root.  Can I do that with Nautilus?  How?

---

### Post by BitTorrentBuddha on 2006-08-21
For question number one you can make a script to automatically run tar on selected files when you right click them and go into the submenu 'Scripts.'

0. This will only work if:
     You are using GNOME (Ubuntu)
     You are extracting a **tarball** in a directory you have write access to (ie ~/, /tmp/, etc.)

1. You can do this with .nautilus-scripts, first run this command, creating the file. ```
gedit ~/.gnome2/nautilus-scripts/Extract\ Tarball
```

2. Copy this into the file. ```
#!/bin/bash

tar -xzf NAUTILUS_SCRIPT_SELECTED_URIS
```

3. Make the script executable giving the owner executable rights and group and other read rights. ```
chmod 755 ~/.gnome2/nautilus-scripts/Extract\ Tarball
```

For the second question, there is a way, but it's difficult. You'd either have to run nautilus as root: ```
sudo nautilus
``` Or You'd have to make another script to launch a root nautilus. Again This only works if you're using GNOME (Ubuntu). (Credit to Arnieboy for the script)

1. Make the script ```
gedit ~/.gnome2/nautilus-scripts/Nautilus\ As\ Root
```

2. Copy this into the file and save it. ```
#!/bin/bash

# Opens a nautilus window as root.

foo=`gksudo -u root -k -m "Enter your password for nautilus root access" /bin/echo "Invalid Password"`
sudo nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI
```

3. Make it executable just as above. ```
chmod 755 ~/.gnome2/nautilus-scripts/Nautilus\ As\ Root
```

4. Then cut/copy a file/folder in regular Nautilus, run the 'Nautilus As Root' script and paste it where you see fit.

---

### Post by straypackets on 2006-08-21
Thanks. 

That seems to defeat the purpose of the GUI.  I can easily do this at the command line; I've been doing it for years.  I don't think I should have to resort to writing scripts to convince Nautilus to open an archive in a sensible fashion. (If you've archived a directory, what's more logical than wishing to recreate that directory when you unarchive it?)

What I've described is the default behavior in OS X.  And when you try to do something that requires root's password, the GUI pops up a request asking for it.

Am I right to think that the answer to both my questions is "No"?

---

### Post by BitTorrentBuddha on 2006-08-21
If you're not a fan of nautilus-scripts perhaps give [Nautilus Actions](http://www.grumz.net/index.php?q=taxonomy/term/2/9&PHPSESSID=7d76dce7a4931b778f7d014c4ad5af97) a look. And I whole-heartedly agree with the functionality that you're looking for, it's definitely something that should be added to Nautilus.

---

### Post by wagerrard on 2006-08-21
Thanks for the pointer. I was bouncing between OS X and Ubuntu today, trying to duplicate  on Ubuntu some work I'd done on the Mac. It was frustrating using Nautilus, there was so much it wouldn't let me do.  Quicker and easier to move files around at the command line, which is a telling statement.

---

