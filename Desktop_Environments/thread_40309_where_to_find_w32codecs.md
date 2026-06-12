---
title: "where to find w32codecs"
date: 2005-06-08
forum: Desktop Environments
---

### Post by banditti on 2005-06-08
I have enabled universe and I can't find w32codecs anywhere.  I have tried several of the new user scripts and if I go into backports, it causes my video to blank out.  I am not sure what package does it, but I don't want to mess with it anymore.  So, if someone can help me find w32codecs, I would appreciate it.


Thanks,

---

### Post by arunsub on 2005-06-08
Try this.
[http://www.mplayerhq.hu/homepage/design7/codecs.html](http://www.mplayerhq.hu/homepage/design7/codecs.html)

---

### Post by banditti on 2005-06-08
so MPlayer essential works for xine too?

---

### Post by arunsub on 2005-06-08
I think so. I think that's what i did. Give it a try. Sorry if i'm wrong.

---

### Post by drummer on 2005-06-08
[QUOTE=banditti]I have enabled universe and I can't find w32codecs anywhere.  I have tried several of the new user scripts and if I go into backports, it causes my video to blank out.  I am not sure what package does it, but I don't want to mess with it anymore.  So, if someone can help me find w32codecs, I would appreciate it.


Thanks,[/QUOTE]
 w32codecs are also in the marillat repositories.
Add to your /etc/apt/sources.list 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

---

### Post by banditti on 2005-06-10
where do I put the files once I have them?

---

### Post by drummer on 2005-06-10
[QUOTE=banditti]where do I put the files once I have them?[/QUOTE]
 hmm.. I've just seen that the codecs and other packages are in the backports repository and have been told to use that instead of marillat as debian sarge has just been released.

to add backports repos -- [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
and to install codecs -- [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

you can use the backports instead of marillat so remove the marillat entry in /etc/apt/sources.list .. I'm sorry for my previous post, I didn't realise all that's needed is in backports.

Also, you don't need to download the package files yourself.. use apt-get and it does everything for you. Follow the instructions on ubuntuguide.org - links above - text in the black boxes is to be entered in a terminal window, one line at a time, for more info read the general notes at the top of the Ubuntu Guide page. It's an invaluable resource for configuring/tweaking Ubuntu.

I hope that's clearer.

---

