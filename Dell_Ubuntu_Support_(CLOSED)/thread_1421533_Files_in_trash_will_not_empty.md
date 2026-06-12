---
title: "Files in trash will not empty"
date: 2010-03-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RutRow on 2010-03-04
I have some files I put in the trash, that will not go away. It is an entire folder that is several gigs of data. If I open the trash and click delete from trash I get the error Permission Denied. I am logged on as the administrator. 
 
How can I get the files to go away?

---

### Post by RutRow on 2010-03-04
When I try to change the permissions of the files to read & write it says 
 
"Operation not supported by backend"
 
This is on my Dell Inspiron Mini 10 running Ubuntu 8.04

---

### Post by Arndtwe on 2010-03-04
[Let me Google that for you]("http://lmgtfy.com/?q=empty+trash+override+permission+ubuntu") <-- link

More specifically: [THIS]("http://ubuntuforums.org/showthread.php?t=994480")

---

### Post by RutRow on 2010-03-04
Thank you. :p
 
Knowing just how to phrase the search is the trick.
 
"empty trash override permission ubuntu" is logical, I just did not think to phrase it that way. I figured it was something easy.

---

### Post by RutRow on 2010-03-04
Sill no luck.
 
Please remember I am new to Ubuntu. I have only been using it for a week. I have used computer for decades, but Ubuntu 8.04 is new to me.
 
I ran terminal and pasted in:
 
sudo chown -R $USER:$USER ~/.local/share/Trash
 
It asked for my password and I entered it. I exited terminal and emptied the trash. The files are still there and will not go away. :(
 
What am I doing wrong?

---

### Post by RutRow on 2010-03-04
OK I found the answer.

[http://ubuntuforums.org/showthread.php?t=817075](http://ubuntuforums.org/showthread.php?t=817075)

This did the trick. 

Thanks all

---

### Post by Arndtwe on 2010-03-04
Glad you found the answer! I'll give you a hint: I never send things to the trash bin. I went into nautilus settings and added a "delete" option. This will completely by-pass the trash bin and just delete things.

---

