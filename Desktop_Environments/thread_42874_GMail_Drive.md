---
title: "GMail Drive"
date: 2005-06-19
forum: Desktop Environments
---

### Post by acascianelli on 2005-06-19
For Windows there is a program to mount GMail and use it as a storage system.  Is there anything available like this that I could use inside Ubuntu Hoary with Gnome?

---

### Post by skoal on 2005-06-19
Whoa! I didn't realize there was such a thing.  I need a place to stash all my old junk I've been lugging around in my CD backup collection.  Great idea, and surely there's something like this for Linux...

\\//_

---

### Post by gil-galad on 2005-06-19
Looking around on google, I found out that it came out for linux first.  I have no idea how to install this ([http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html)) , but it looks awesome.

Edit:  Actually, its in the hoary repositories!  **apt-get install gmailfs**

---

### Post by acascianelli on 2005-06-19
[http://www.viksoe.dk/code/gmail.htm](http://www.viksoe.dk/code/gmail.htm)

Here's the windows version.

---

### Post by rwabel on 2005-06-20
indeed there is a version in ubuntu. But the problem is while mounting gmail. I get the following message
 ```
fusermount: old style mounting not supported
``` 

any chance to let it mount or change the way to mount?

I've used the suggested one from the homepage
 ```
 mount -t gmailfs /usr/local/bin/gmailfs.py /path/of/mount/point -o username=gmailuser, password=gmailpass, fsname=zOlRRa 
```

---

### Post by Sionide on 2005-06-20
Ohh, very good! I had been wondering about this, I have a few files stashed away in my Gmail account :)

---

### Post by cutOff on 2005-06-20
[QUOTE=rwabel]indeed there is a version in ubuntu. But the problem is while mounting gmail. I get the following message
 ```
fusermount: old style mounting not supported
``` 

any chance to let it mount or change the way to mount?

I've used the suggested one from the homepage
 ```
 mount -t gmailfs /usr/local/bin/gmailfs.py /path/of/mount/point -o username=gmailuser, password=gmailpass, fsname=zOlRRa 
```[/QUOTE]
It didn't work here. Can you explain please how to achieve it?

Thanks

---

### Post by luca_linux on 2005-06-20
Really useful!

---

### Post by rwabel on 2005-06-20
[QUOTE=cutOff]It didn't work here. Can you explain please how to achieve it?

Thanks[/QUOTE]
 well it didn't work for me. But to get to my error message you need to mount it as stated on the homepage.
you have to remove the space after the coma, sorry forgot to mention that and the path of gmailfs.py is also different when you install via apt

 ```
 mount -t gmailfs /usr/share/gmail/gmailfs.py /path/of/mount/point -o username=gmailuser,password=gmailpass,fsname=zOlRRa
```

I hope I could help out, but we still have the problem with fusermount

---

### Post by cutOff on 2005-06-20
I have just read this [here](http://ubuntuforums.org/archive/index.php/t-21385.html) (last post)

>  i had to to main problem as i really think is python when ever you look in synaptic on the depnedencies of gmailfs you will notice python2.4 sorry to tell you i read a full document in linux-magazine in the issue 55 know-how on gmailfs and it says that gmails fs do not work with python 2.4 it says 2.3 and hoary by default has pythin 2.4 installed ,if you want to work with gmaifs you could download the tar ballz and compile them manually with the kernel issue and it will work fine ,beside that to remove all python 2.4 related and reinstall 2.3 ,it is a long procedure and i am ready to discuss it if any one interested ,gmailfs from scratch ,manually compiled ,but guys personnaly i could wait a fix for that instead of messing off my kernel and my lovely ubuntu

---

### Post by rwabel on 2005-06-20
what a pity!
maybe there is another gmail program around.

---

