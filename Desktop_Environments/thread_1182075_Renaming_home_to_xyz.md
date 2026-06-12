---
title: "Renaming /home to /xyz"
date: 2009-06-08
forum: Desktop Environments
---

### Post by garg on 2009-06-08
Hello,

Is there any way to rename /home to something else like /xyz on an existing machine? For example, if I had an existing home directory, I'd like it to exist in /xyz/my_home_dir. I'd also like all future accounts to be made in /xyz by default.

Is this doable?

---

### Post by whoop on 2009-06-08
pardon me for asking, but, why would you want to do that? 

I stumbled on this post because I recently changed my /home to /home_old, but at the same time I created a /home raid1.

---

### Post by s3MA00RRNY on 2009-06-08
Almost every linux distro has a "home" folder. I would assume that this means many programs are not designed for this folder to be named differently. I would not attempt it. It will probably confuse things.

---

### Post by garg on 2009-06-08
A person who I am helping out told me that his previous setup had his home files in /xyz/blabla and wants to keep it like that on his new ubuntu setup. 

Maybe I should just make a symlink from /xyz -> /home ?

---

### Post by lykwydchykyn on 2009-06-08
> **garg said:**
> A person who I am helping out told me that his previous setup had his home files in /xyz/blabla and wants to keep it like that on his new ubuntu setup. 

Maybe I should just make a symlink from /xyz -> /home ?

That'd be the quick and easy (and safe) approach.  Theoretically you can just change the path to a user's home in /etc/passwd and it shouldn't matter where their home dir is (as long as they can read/write to it).  I wouldn't be too confident that some poorly designed software wouldn't break by making the assumption that /home exists.

Making it default would be another can of worms altogether.  Probably would involve some major hacking on the graphical tools, at least.

---

### Post by unkilbeeg on 2009-06-08
I doubt that it would be a problem.  If a package is so poorly written that it doesn't look at $HOME and uses a hard coded /home, then you're better off not having it installed.


It's pretty easy to do.

```
sudo mv /home /xyz
useradd -D -b /xyz
```

then replace all instances of home in /etc/passwd

```
sudo vim /etc/passwd

:s/home/xyz/
:wq
```

---

