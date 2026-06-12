---
title: "Beowulf Cluster"
date: 2009-05-21
forum: Education &amp; Science
---

### Post by Hans4 on 2009-05-21
Hey Ubuntu Users!

I was recently given a challenge by my Adv. Networking teacher to create a Beowulf Cluster and after using Ubuntu (Since about version 8. something, i forget) I immediately thought of Ubuntu as the perfect OS for running a cluster computer. 

I was wondering if you guys(or girls) had any ideas on which version to use, or if you have recently created a cluster computer and have any tips.

Thank You!

Hans4

---

### Post by mag_dex on 2009-05-23
Hey,

I've been thinking about starting a cluster. 

How have you done it? Can you give any useful links? extra info etc.

I'd be really grateful :)


M.

---

### Post by Hans4 on 2009-05-23
Hey M.
 
No, I have not created any clusters but have been researching how to create one for about a year now. (Using Google, and all that good stuff) And i have found next to nothing explaining how to actually create one, or which OS to use. 
 
I figured that I would find an OS and then just build from there, and thats why i am here; to see if anyone knows of a form of Ubuntu that could run a cluster computer.
 
 
Hans

---

### Post by hubie on 2009-05-23
As I write this reply, your post is sitting right under a [monster thread]("http://ubuntuforums.org/showthread.php?t=1030849") regarding clustering.  I think if you go through those 22 or so pages, you'll get a good idea what you'll need to do.

---

### Post by Hans4 on 2009-05-24
Howdy to anyone still reading my thread considering the thread mine is sitting under.
 
I have just realised that there is no way for me to set up a Cluster Computer to do what i want. I wish it were possible right now but it just isnt to have a head of a cluster automatically split threads to various cores and etc. by itself. I'll tell that to my Networking Teacher and if he has a problem... well :P
 
So maybe i will come back in a couple of years and see it its possible then
 
Hans4

---

### Post by ajt on 2009-05-24
> **Hans4 said:**
> Howdy to anyone still reading my thread considering the thread mine is sitting under.
 
I have just realised that there is no way for me to set up a Cluster Computer to do what i want. I wish it were possible right now but it just isnt to have a head of a cluster automatically split threads to various cores and etc. by itself. I'll tell that to my Networking Teacher and if he has a problem... well :P
 
So maybe i will come back in a couple of years and see it its possible then
 

Hello, Hans4.

Don't give up yet!

There's a lot of people talking about things like this over on our 'easy' Ubuntu clustering thread:

  [http://ubuntuforums.org/showthread.php?t=1030849](http://ubuntuforums.org/showthread.php?t=1030849)

I suggest that you have a look at MPI (Message Passing Interface). You can install this very easily as LAM (Local Area Multicomputer) under Ubuntu:

```

  sudo aptitude install lam-dev lam-mpidoc

```

You can use LAM on a single node with multiple CPU's, and it will run part of the task on each CPU. This is not a Beowulf, of course, but it is quite easy to start running MPI programs on more than one computer once you've got the idea of what MPI is all about - Why not join in the 'easy' Ubuntu clustering thread and tell us how you get on trying out LAM?

Bye,

  Tony.

---

