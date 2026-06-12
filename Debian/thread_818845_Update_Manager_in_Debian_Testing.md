---
title: "Update Manager in Debian Testing?"
date: 2008-06-04
forum: Debian
---

### Post by hockeyfighter09 on 2008-06-04
I am wondering if there is a way to get update manager installed in Debian Testing.  I check for it in my current repos and its not there. Any suggestions?

---

### Post by kerry_s on 2008-06-04
do you have all the repos turned on (contrib, non-free) it shows in mine, i'm using etch/lenny(stable/testing)

```
deb http://ftp.debian.org/debian/ stable main contrib non-free  
deb http://ftp.debian.org/debian/ testing main contrib non-free 

deb http://security.debian.org/ stable/updates main contrib non-free 
deb http://security.debian.org/ testing/updates main contrib non-free 


```

---

### Post by hockeyfighter09 on 2008-06-04
```

# deb cdrom:[Debian GNU/Linux testing _Lenny_ - Official Snapshot i386 CD Binary-1 20080602-11:13]/ lenny main 

# deb cdrom:[Debian GNU/Linux testing _Lenny_ - Official Snapshot i386 CD Binary-1 20080602-11:13]/ lenny main  

deb http://security.debian.org/ testing/updates main 
deb-src http://security.debian.org/ testing/updates main 
deb ftp://ftp.debian.org/debian/ testing main contrib non-free 

```

That is whats on my /etc/apt/sources.list I think I need to add one more repo because I only have three and you have four.  Also is it ok if I were to remove those cdrom snapshot things off my sources.list?  I want to just stick with testing because its a rolling release.

---

### Post by K.Mandla on 2008-06-04
Moved to Debian subforum.

---

### Post by kerry_s on 2008-06-04
> **hockeyfighter09 said:**
> ```

# deb cdrom:[Debian GNU/Linux testing _Lenny_ - Official Snapshot i386 CD Binary-1 20080602-11:13]/ lenny main 

# deb cdrom:[Debian GNU/Linux testing _Lenny_ - Official Snapshot i386 CD Binary-1 20080602-11:13]/ lenny main  

deb http://security.debian.org/ testing/updates main 
deb-src http://security.debian.org/ testing/updates main 
deb ftp://ftp.debian.org/debian/ testing main contrib non-free 

```

That is whats on my /etc/apt/sources.list I think I need to add one more repo because I only have three and you have four.  Also is it ok if I were to remove those cdrom snapshot things off my sources.list?  I want to just stick with testing because its a rolling release.

yes, you can remove it, you can also # out the deb-src if you don't plan on building anything.

i have 4 because i'm using the etch kernel on my install, so i keep the etch repo for updates.


for yours you need to:
```
deb [http://security.debian.org/](http://security.debian.org/) testing/updates main 
to
deb [http://security.debian.org/](http://security.debian.org/) testing/updates main contrib non-free
```

you can add my testing 1's if you want.
you also might want to add the multimedia repo:

```
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) testing main
```

it has things you might want, like acrobat reader, flash, etc...

---

### Post by hockeyfighter09 on 2008-06-04
> **kerry_s said:**
> yes, you can remove it, you can also # out the deb-src if you don't plan on building anything.

i have 4 because i'm using the etch kernel on my install, so i keep the etch repo for updates.


for yours you need to:
```
deb [http://security.debian.org/](http://security.debian.org/) testing/updates main 
to
deb [http://security.debian.org/](http://security.debian.org/) testing/updates main contrib non-free
```

you can add my testing 1's if you want.
you also might want to add the multimedia repo:

```
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) testing main
```

it has things you might want, like acrobat reader, flash, etc...

Alright, thanks alot for your help. Ill see if I can smooth everything out by myself.:)

---

### Post by kerry_s on 2008-06-04
forgot to tell you the key for the mutimedia repo is in that repo, you just apt-get it or install it with synaptic if you prefer the gui.

---

### Post by hockeyfighter09 on 2008-06-04
[HTML]
deb http://security.debian.org/ testing/updates main contrib non-free

deb ftp://ftp.debian.org/debian/ testing main contrib non-free

deb http://www.debian-multimedia.org testing main[/HTML]

Thats what my sources.list looks like now.  Is there anything else I need to add, did I do everything correctly?

---

### Post by hockeyfighter09 on 2008-06-04
Ok, I got the repos put in then I did a apt-get update and also insalled the multimedia key like you said, but I still dont have update manager in the repos.  Is there anymore I am missing?:confused:

---

### Post by kerry_s on 2008-06-04
> **hockeyfighter09 said:**
> Ok, I got the repos put in then I did a apt-get update and also insalled the multimedia key like you said, but I still dont have update manager in the repos.  Is there anymore I am missing?:confused:

mybag, i just looked at in synaptic and it's in stable, so you need to add etch/stable.

---

### Post by hockeyfighter09 on 2008-06-04
> **kerry_s said:**
> mybag, i just looked at in synaptic and it's in stable, so you need to add etch/stable.
Which stable repo would I need to add?  Is it one of the ones you posted earlier.  Also how would this effect me from getting the newer packages in testing if I added a stable repo?

---

### Post by kerry_s on 2008-06-05
> **hockeyfighter09 said:**
> Which stable repo would I need to add?  Is it one of the ones you posted earlier.  Also how would this effect me from getting the newer packages in testing if I added a stable repo?

yeah just add mine. no difference apt-get/synaptic will always install the highest version, which is usually lenny/testing. the etch/stable stuff will only be used when there is no testing/lenny option.

---

### Post by hockeyfighter09 on 2008-06-05
> **kerry_s said:**
> yeah just add mine. no difference apt-get/synaptic will always install the highest version, which is usually lenny/testing. the etch/stable stuff will only be used when there is no testing/lenny option.

Ok, Last question to make sure :) If I use the exact repos you posted earlier will that be basicially the same as running a pure testing version of debian so it will always be rolling release?  Thanks so much for your help!

---

### Post by hockeyfighter09 on 2008-06-05
Nevermind I think I know what youre saying in your post. Just took awhile to click for me.:)

---

### Post by kerry_s on 2008-06-05
> **hockeyfighter09 said:**
> Nevermind I think I know what youre saying in your post. Just took awhile to click for me.:)

:lolflag: don't worry the more you use it the easier it gets. debian is solid as a rock. it just takes time to get familiar.

---

### Post by hockeyfighter09 on 2008-06-05
Alright I added the two stable repos you provided earlier and got the update manager and notifier installed, now everything is running smooth as silk!  I think I am falling in love!:lolflag:

---

### Post by notwen on 2008-06-05
> **hockeyfighter09 said:**
> I think I am falling in love!:lolflag:

Debian isn't a bad distro to fall in love w/.  It won't break you heart, it shouldn't break too much of anything as a matter of fact.  I've been using Debian stable for years as a file server and I've had zero problems.  =]

---

### Post by kerry_s on 2008-06-05
> **hockeyfighter09 said:**
> Alright I added the two stable repos you provided earlier and got the update manager and notifier installed, now everything is running smooth as silk!  I think I am falling in love!:lolflag:

hey, i saw her first, she's my beloved deb. :lolflag:

oh god notwen, you to, she must be cheaten on me. :(

---

