---
title: "nautilus problem with files"
date: 2006-06-03
forum: Desktop Environments
---

### Post by double0seven on 2006-06-03
hi, when i try to open a file in nautilus it mostly tells me that it is a security problem and that it is a for example a mpeg file but the fileending shows that it is a mpg file. is there a way to tell nautilus that those 2 files are the same and that i dont always have to chose "open with other app"?

I'm sorry my gnome is in german, perhabs those things have different names in english.

mfg

---

### Post by double0seven on 2006-06-03
when i use nautilus as root, i dont have this problem. perhabs this helps :S

---

### Post by Corvillus on 2006-06-03
It could be a permissions issue...do you have ownership of the file? Right click it and go to Properties - Permissions, and you should be listed as the owner. If that's not the problem, it's probably a MIME type conflict, which occurs often when moving files from a certain other OS that doesn't support MIME types and relies completely on file extensions to determine the format of a file.

---

### Post by double0seven on 2006-06-03
i own the file and i made it readable and wirtable and executable for all users, i just moved all my movie files from my free-bsd server to my ubuntu workstation, oldertimes before i updated my ubuntu (i already had dapper i just did a apt-get dist-upgrade) 3 days ago it worked

---

### Post by Corvillus on 2006-06-03
Weird...I guess you could try this...but it doesn't really sound too much like like a MIME problem so I'm not sure it would work. [http://www.ubuntuforums.org/showthread.php?t=81936](http://www.ubuntuforums.org/showthread.php?t=81936)

---

### Post by double0seven on 2006-06-03
still having the problem this didnt work, especially i think it is strange because it works as root.
i pasted the dialog it gives me : (its german i'm sorry) [http://www.ubuntuusers.de/paste/1362/](http://www.ubuntuusers.de/paste/1362/)

in english this would be something like : > The filename "*.mpg" indicates that this file is of type "mpg-document". The contents of the file indicate that the file is of type "MPEG-Video". If you open this file, the file might present a security risk to your system.[.....]

---

### Post by double0seven on 2006-06-03
it can preview the files (i mean then there is instead of an icon a picture of the movie) but it cant open them whitout displaying the message, strange

---

### Post by double0seven on 2006-06-03
solved it :D if someone has the same problem: i had a wrong entry in /.local/share/mime/globs

---

### Post by Corvillus on 2006-06-03
Yeah, I hate how Nautilus is with MIME types. It's happy to complain when the MIME type doesn't match, but gives you no easy way to change it to the one you want. I should probably file a usability bug for that in GNOME or something. :P

---

