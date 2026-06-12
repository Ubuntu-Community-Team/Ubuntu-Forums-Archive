---
title: "Noob question about txt editors"
date: 2009-05-19
forum: General Help
---

### Post by GnubbyaBush on 2009-05-19
Hi all I'm new to ubuntu, and I'm trying to set up an ftp server. I've run into problems on step one haha. When I try to edit my proftpd.conf file using the syntax "sudo gedit /ect/proftpd.conf" and i get a blank window. I've tried vi and vim, and still blank. When I go to synaptic manager it says proftpd is installed. Can anyone enlighten me here, i'm assuming it's something simple, thanks.

---

### Post by Titan8990 on 2009-05-19
the path is /etc/ not /ect/. Try tab completion.

---

### Post by Moe The Cat on 2009-05-19
I don't know if you've made the typo just in your post above, but it should be /etc, not /ect.

Edit: Titan beat me to it ...

---

### Post by GnubbyaBush on 2009-05-19
wow that was sad thanks, i'll be back with more dumb questions, although hopefully a little better than this one

---

### Post by asmoore82 on 2009-05-19
> **GnubbyaBush said:**
> wow that was sad thanks, i'll be back with more dumb questions, although hopefully a little better than this one

/etc = Editable Text Configuration

there's a method to the madness :KS

---

### Post by lisati on 2009-05-19
> **GnubbyaBush said:**
> wow that was sad thanks, i'll be back with more dumb questions, although hopefully a little better than this one

Sometimes it's dumber NOT to ask. Sometimes the answer will come to you as you figure out how to ask your so-called "dumb" question. And there's always the possibility that someone else might read the ensuing discussion and be helped by it.

Keep on smiling!

---

### Post by AlexsAntidote on 2009-05-19
> **GnubbyaBush said:**
> Hi all I'm new to ubuntu, and I'm trying to set up an ftp server. I've run into problems on step one haha. When I try to edit my proftpd.conf file using the syntax "sudo gedit /ect/proftpd.conf" and i get a blank window. I've tried vi and vim, and still blank. When I go to synaptic manager it says proftpd is installed. Can anyone enlighten me here, i'm assuming it's something simple, thanks.

As someone else already mentioned, it is /etc/ not /ect/ but perhaps that was simply a typo in your post and you actually entered /etc/ in your terminal... If that is the case...

Try:
```
sudo gedit /etc/proftpd/proftpd.conf
```

I think that should work for you.

The reason why you are getting a blank file is because you are telling gedit to open a file that does not exist, so it creates a new file by the name you gave. The reason why the file does not exist is because you are looking for it in the wrong folder.

---

### Post by AlexsAntidote on 2009-05-19
> **lisati said:**
> **Sometimes it's dumber NOT to ask.** Sometimes the answer will come to you as you figure out how to ask your so-called "dumb" question. And there's always the possibility that someone else might read the ensuing discussion and be helped by it.

Keep on smiling!

I completely agree.

---

### Post by evermooingcow on 2009-05-20
The strategy I picked up for surviving CLI is to spam the tab key. It auto completes unless there are multiple possibilities in which case it will list all of the possibilities.

Its much harder to make typos using auto complete

---

### Post by GnubbyaBush on 2009-05-20
thanks for all the help guys, this forum is surprisingly really responsive. sudo gedit /etc/proftpd/proftpd.conf worked. Its funny cause i tried this earlier but i must have used ect instead of etc, thanks again

---

### Post by StooJ on 2009-05-20
Just a quick note:

You should really be using gksudo, not sudo when opening GUI programmes like gedit. Keep sudo for command-line stuff only.

---

