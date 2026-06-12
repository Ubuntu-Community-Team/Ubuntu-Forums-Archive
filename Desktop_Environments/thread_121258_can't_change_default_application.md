---
title: "can't change default application"
date: 2006-01-24
forum: Desktop Environments
---

### Post by justin.tyler on 2006-01-24
I'm fairly new to kubuntu/Linux in general, which is evident by my having to reinstall it the other day. Anyway, now that I've reinstalled kubuntu 5.10, I can't change the default application to handle certain file types. For example, if I wanted XMMS to open an .mp3 file, I have to right click and go to "open with". I have tried going to properties and changing it that way, I have also tried using kcontrol. As soon as I click "apply" and close the window, if I reopen it it goes back to exactly how it was.

Any ideas?

---

### Post by Jucato on 2006-01-24
Have you tried this:

1. KControl > KDE Components > File Associations
2. Type "mp3" in the "Find filename pattern" (mine shows up as audio > x-mp3)
3. Change the "Application Preference Order",  putting XMMS at the top.

Alternatively, you could also go to Konqueror > Settings > Configure Konqueror > File Associations, and do the same thing.

Hope this helps

---

### Post by justin.tyler on 2006-01-26
I have already attempted this. As soon as I hit "apply", and close the window, if I reopen it, it's back to how it was.

---

### Post by Jucato on 2006-01-26
That's strange, since I just did it now and it worked. Are you doing it as a regular user or as root?

---

### Post by justin.tyler on 2006-01-26
I've tried it as regular and root.
I just retried it, and now if I open a root priviledged konqueror, it opens it in XMMS the program I want it to, but if I'm using a regular account, I still can't change it, and it still is opening mp3s in Totem.

---

### Post by Jucato on 2006-01-26
you should only change it as a regular user. user settings for user, root settings for root. But it's strange that it doesn't work... Sorry I can't be of more help... :(

---

### Post by justin.tyler on 2006-01-26
Anyone else have any ideas?

---

### Post by samotholt on 2006-01-26
I have exactly the same problem. I have also tried to find what files to change, and do it manually. No luck there either. Could probably not find the right files (it's a bit messy if you ask me). Everything works fine in gnome though.

---

### Post by Jucato on 2006-01-26
I forgot to ask, if you have upgraded to KDE 3.5? Maybe it's a 3.4 bug?

---

### Post by samotholt on 2006-01-26
kde 3.5 does the trick :-)

---

### Post by Jucato on 2006-01-26
oooh... should have asked that from the start. It would have saved justin.tyler a lot of frustration... assuming that he's not yet upgraded to 3.5. :D

---

### Post by justin.tyler on 2006-01-28
Didn't do the trick for me. :(
edit: nevermind. I fixed it by deleting the mp3 file association, then creating a new one.

---

### Post by Copter on 2006-02-21
[QUOTE=justin.tyler]I've tried it as regular and root.
I just retried it, and now if I open a root priviledged konqueror, it opens it in XMMS the program I want it to, but if I'm using a regular account, I still can't change it, and it still is opening mp3s in Totem.[/QUOTE]
hi!

i have exacly the same problem on kde 3.5 but with a plain text editor. i want to use kedit but everytime i change .txt association to it, kubuntu makes new entry in Kmenu with empty template called Editor or Text Editor. it hasnt got any program set to run. the same thing happens when using KControl (dont know also why there are just a few options in Controll Center in the same section).

i also tried deleting ~/.kde/share/mimelnk/text/plain.desktop but its good for nothing. any ideas?

copter :]

---

