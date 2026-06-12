---
title: "Repositories"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Koba on 2005-10-13
Is there anyone who has a list of Extra Repositories for Breezy? the only ones i know of are for Hoarty, and i kinda want to get my apps and codecs :S

---

### Post by oldblue on 2005-10-13
backports isn't up yet, and the mplayer site is down.  You can get the w32 codecs from somewhere else though.
I'm assuming you don't know how to do some things in linux, so I apologize if this is redundant.
Run 'sudo gedit /ect/apt/sources.list'.  Add this to the top:
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main
Save the file.
Run 'sudo apt-get update'.  Then 'sudo apt-get install w32codecs libdvdcss2'.  Once installed rerun 'sudo gedit /ect/apt/sources.list' and remove the line that was added.  Run 'sudo apt-get update'.
Do NOT run 'apt-get upgrade' with the above repository, you can break stuff.

---

### Post by grsing on 2005-10-13
I think you mean etc, instead of ect.  Besides that, thanks.

---

### Post by N8MAN1068 on 2005-10-14
actually, it is 'etch'

---

### Post by grsing on 2005-10-14
Not the "etch," but "etc" instead of "ect" in /ect/apt/sources.list

---

