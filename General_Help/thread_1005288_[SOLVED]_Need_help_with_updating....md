---
title: "[SOLVED] Need help with updating..."
date: 2008-12-08
forum: General Help
---

### Post by Jacob Collstrup on 2008-12-08
Heya,

I tried to update gimp according to a guide I found, but it didn't work. Now every time I need to update I can only do a partial update on my system, the error is not limited to gimp. I get this message AFTER the partial update:

[IMG]http://i202.photobucket.com/albums/aa224/JacobCollstrup/Screenshot-2.png[/IMG]

I hope someone can help me figure out how to correct this.

Jacob

---

### Post by howefield on 2008-12-08
I had this a while ago but can't exactly remember the fix, have you tried loading up synaptic package manager and choosing fix broken packages from the edit menu ?

---

### Post by Jacob Collstrup on 2008-12-08
I just tried that, and it didn't work even though it said 'successfully fixed broken dependencies' or something like that. The Error message is exactly the same.

It seems I need to tell Ubuntu that these packages are ok...but I don't know how to do that.

Jacob

---

### Post by howefield on 2008-12-08
How about going into System Menu > Software Sources, and unchecking any repositories that you have added, then type in terminal

```
 sudo apt-get update
```

Does that sort it ?

---

### Post by Jacob Collstrup on 2008-12-08
I tried removing the repository and then run the update manager again. That worked!! :p:p Thanks for the help!!

Jacob

---

