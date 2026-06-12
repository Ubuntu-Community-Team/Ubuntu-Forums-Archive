---
title: "Installing Warsow, Tremulous"
date: 2006-07-16
forum: Gaming &amp; Leisure
---

### Post by Cure777 on 2006-07-16
Forgive me, but I am a Linux n00b. How do I install the warsow_0.12-english.run file? When I double-click on it, it either does nothing, or just tries to open it in text editor, which gives me an error about it being a binary file. ](*,) I had the same trouble with Tremulous yesterday...

---

### Post by PPower on 2006-07-16
> **Cure777 said:**
> Forgive me, but I am a Linux n00b. How do I install the warsow_0.12-english.run file? When I double-click on it, it either does nothing, or just tries to open it in text editor, which gives me an error about it being a binary file. ](*,) I had the same trouble with Tremulous yesterday...

May I introduce you to my good friend, the console. You need to install it from a terminal.

---

### Post by Cure777 on 2006-07-16
> **PPower said:**
> May I introduce you to my good friend, the console. You need to install it from a terminal.
I figured as much, but how would I go about doing that?

---

### Post by Cure777 on 2006-07-16
No one seems to feel like replying...

---

### Post by christhemonkey on 2006-07-16
You need to change to the directory it was downloaded to:
```
cd /path/to/directory/ 
```
Replacing path to directory with actual path.
If its on your desktop:
```
cd ~/Desktop 
```

And then you need to make it executable:
```
sudo chmod +x warsow_12-english.run 
```

And then run it:
```
sudo sh ./warsow_12-english.run 
```

Something like that anyways!

---

### Post by Kabal on 2006-07-16
Try this Thread :)

[http://www.ubuntuforums.org/showthread.php?p=1237785](http://www.ubuntuforums.org/showthread.php?p=1237785)

Read it trough and it might help :)

---

### Post by Cure777 on 2006-07-16
Thank you very much, this worked.

---

### Post by PPower on 2006-07-17
Whoops! I was going to but i forgot. Sorry!

---

