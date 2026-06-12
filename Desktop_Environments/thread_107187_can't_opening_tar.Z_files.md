---
title: "can't opening tar.Z files"
date: 2005-12-22
forum: Desktop Environments
---

### Post by greenkey on 2005-12-22
Hi all,
I'm having a problem with an archive.

The file has the "tar.Z" extension, File Roller 2.12.1 says: [INDENT]**Could not open "aaaaa.tar.Z"**
Archive type not supported[/INDENT]
What commands can I try to open it from bash?
How can I open it from GNOME?

Thanks

---

### Post by Susana on 2005-12-22
[QUOTE=greenkey]Hi all,
I'm having a problem with an archive.

The file has the "tar.Z" extension, File Roller 2.12.1 says: [INDENT]**Could not open "aaaaa.tar.Z"**
Archive type not supported[/INDENT]
What commands can I try to open it from bash?
How can I open it from GNOME?

Thanks[/QUOTE]

uncompress aaaaa.tar.Z
tar -xvf aaaaa.tar

---

### Post by greenkey on 2005-12-23
Thanks, it works!!! :KS 

... but I wanna know if there is a graphical Interface for doing it... :confused:

---

### Post by schilcha on 2005-12-23
[QUOTE=greenkey]... but I wanna know if there is a graphical Interface for doing it... :confused:[/QUOTE]

Try File Roller (it's the default application configured on the ubuntu desktop).

BTW, to do the above in one line, use tar Zxvf aaaa.tar.Z

---

### Post by kaamos on 2005-12-23
[QUOTE=greenkey]The file has the "tar.Z" extension, File Roller 2.12.1 says: [INDENT]**Could not open "aaaaa.tar.Z"**
Archive type not supported[/INDENT]
[/QUOTE]
[quote=schilcha]
Try File Roller (it's the default application configured on the ubuntu desktop).
[/quote]
Err.. Did I miss something?

---

### Post by schilcha on 2005-12-23
[QUOTE=kaamos]Err.. Did I miss something?[/QUOTE]
Wow, that's magic ;)

Honestly, shame on me (I hate it when people don't read previous posts carefully)! Afterall, no information was being conveyed...

Anyways, 
   MERRY CHRISTMAS to all of you!

---

### Post by kaamos on 2005-12-23
And to you! :)

---

### Post by schilcha on 2005-12-23
Finally, I'll give it one more try:

Greenkey, how did you install compress/uncompress? 

On my installation these utils were missing. Trying to open the .tar.Z file with File Roller resulted in the error you reported. I installed the ncompress package via synaptic. Now I have compress/uncompress and File Roller can handle tar.Z-files.

---

### Post by greenkey on 2006-01-02
back from holidays...

[QUOTE=schilcha]Finally, I'll give it one more try:

Greenkey, how did you install compress/uncompress?[/QUOTE] 
Don't know... 
when you told me to try I tried and it worked... whitout installing anything... :???: 

[QUOTE=schilcha]
On my installation these utils were missing. Trying to open the .tar.Z file with File Roller resulted in the error you reported. I installed the ncompress package via synaptic. Now I have compress/uncompress and File Roller can handle tar.Z-files.[/QUOTE]
Now I've just installed "ncompress" via Synaptic and... it definitely works with File Roller!!! :D 

Just for the next time, how did you find it? Searching "compress" on Synaptic?

Thanks.

---

