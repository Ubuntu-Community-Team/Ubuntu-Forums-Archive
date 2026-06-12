---
title: "Just Curious"
date: 2009-04-26
forum: General Help
---

### Post by lnajt on 2009-04-26
So, when I go into Gparted it says my primary partition has about 8.5 gb's of free space but the estimate that shows up towards the bottom of a file browser says about its 3.7 gb.

I'd like to know whats using those 4.5 gb's. Can I reclaim them?

Thanks

---

### Post by AlexsAntidote on 2009-04-26
could you post a screenshot?

---

### Post by lnajt on 2009-04-26
viola

---

### Post by AlexsAntidote on 2009-04-26
You know... I just checked my system and I seem to have a very similar situation. GParted shows I have 25.11 GB unused, while the file browser 23.6 GB "Free Space".

I'm not sure exactly what the cause is (I'm still fairly new to the inner workings of Ubuntu), but I'd imagine it is likely one of two things:

Either GParted and Nautilus use different algorithms or subprograms (or whatever) to calculate the available unused/free space,
Or the calculations differ because one is referring to the amount of space on disk while the other is referring to a different measurement (I hate to do this, but unfortunately I've used Windows for the largest portion of my life... in Windows if you check the properties of a file it will show you two different sizes, one is the "size on disk" and the other is the "file size", though I'm not sure what the precise difference is.)

Good question though.

---

### Post by lnajt on 2009-04-27
Thanks. I spoke to my CS teacher, and he thinks its probably exactly that - it's not taking into account the space lost when a cluster goes only partially filled. Or Something like that.

---

### Post by AlexsAntidote on 2009-04-27
You're welcome, and what your professor said is pretty much along the lines of what I was thinking... That sounds about right... :)

---

