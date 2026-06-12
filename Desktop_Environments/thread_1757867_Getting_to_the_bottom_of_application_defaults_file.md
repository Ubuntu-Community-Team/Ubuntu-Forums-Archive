---
title: "Getting to the bottom of application defaults file associations"
date: 2011-05-13
forum: Desktop Environments
---

### Post by buchs on 2011-05-13
On Ubuntu 11.04, I have a need to use gnome-open from another application to open files in assigned applications. I think I understand how mime types are given in /usr/share/mime. I understand how default application associations are done in /usr/share/gnome/applications/defaults.list. I understand how update-desktop-database is used to maintain defaults.list. I know how to specify file associations (open with) from Nautilus. I understand how ~/.local/share/applications and ~/.local/share/mime override the system settings. I get all that. 

What I don't understand is why the command **gnome-open** or double-clicking a file in nautilus, for certain file types (e.g. PDF), generates an error message: 
  > Could not display "<whatever file>". The location is not a folder.

The occurrences of application/pdf in the different applicable files all point to evince as the associated application.

By the way, mimeopen does work. What is the relationship between mimeopen and gnome-open? Manual pages for these commands are not helpful in understanding their operation.

In addition, I might throw in one other question. In the various .desktop files, I see that some application commands are enclosed in single quotes, but never the file name identifier, %f. If dealing with file/directory names with spaces in them, it would seem that quoting the '%f' would be important. Am, I wrong?

I spent quite a few hours researching this topic but have not found any answers. Can anyone here help?

---

### Post by buchs on 2011-05-20
[COLOR="Blue"][FONT="Arial"]Replying to my own posting, I will share what I discovered which is more information but still not all I desire. 

I found that some entries in my .local/share/applications/mimeapps.list file were very general entries, that were hijacking more specific entries like PDF. Some general entries were of the form x-scheme-handler/file=nautilus. 

I am not sure if the various file association handlers like gnome-open, mimeopen and exo-open (new one for me!) process these mime associations in the order they occur and take the first one that includes the file type you are giving. It would seem that was the case. Somehow the more general handler for type *file* was overriding the type for *PDF*. 

Removing these general entries from that file caused gnome-open to begin to work once again. However, it remained that nautilus and my Chrome browser had trouble opening certain files, like PDF. After reading some other forum posts and websites regarding the exact error message, I found that the xfce desktop components and specifically exo-utils package may have problems in the 11.04 Ubuntu release. A _work-around_ is to uninstall exo-utils. I would still like to get to the bottom of how all these different open functions work - what is reading which files and the rules they are using. Also, what maintains the files?

_References_
[LIST]
[*][1]("http://ubuntuforums.org/showthread.php?p=10830485#post10830485")
[*][2]("http://ubuntuforums.org/showthread.php?t=1669414&highlight=gnome-open")
[*][bug 743859]("https://bugs.launchpad.net/ubuntu/+source/xdg-utils/+bug/743859")
[/LIST]

[/FONT][/COLOR]

---

### Post by Copper Bezel on 2011-05-20
I can't help with this directly, but I've had similar problems with mimetype associations - for instance, installing KDE changed associations in some very unexpected ways under Gnome. Most things go to xdg-open (another to add to the list?) first, which identifies the DE and should jump straight over to gnome-open, but since some apps (say, Nautilus) read the mimetype and others (*most* others from what I've seen) read the extension and then guess at the mimetype according to a shared list of extension globs, and since mimetype associations themselves seem to be perfectly contained within each DE as appropriate except for all the times that they're not, it gets a little unpredictable. = P

It would be neat if someone had a chart for this. = )

---

### Post by davilima6 on 2011-05-27
SOLVED! Uninstalling exo-utils did it! THANK YOU!! I was missing 'go' (gnome-open) too much. :popcorn:

---

### Post by fresneda on 2012-05-05
@buchs: Spot on! thanks!

---

### Post by mutex023 on 2012-05-06
> **buchs said:**
>  In the various .desktop files, I see that some application commands are enclosed in single quotes, but never the file name identifier, %f. If dealing with file/directory names with spaces in them, it would seem that quoting the '%f' would be important. Am, I wrong?

I spent quite a few hours researching this topic but have not found any answers. Can anyone here help?
If a file/directory has spaces in its name, it must be enclosed in quotes. %f is not required

---

