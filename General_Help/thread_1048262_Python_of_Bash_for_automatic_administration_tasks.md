---
title: "Python of Bash for automatic administration tasks"
date: 2009-01-23
forum: General Help
---

### Post by e24ohm on 2009-01-23
Python of Bash for automatic administration tasks
What should I use or learn to perform automatic administration task on my desktop version? I am coming from an environment that uses .bat files, so I am not sure what do use for my Linux automation of administration tasks?

What are the benefits of each (Python vs. Bash)? What will I need to learn if I go each route?

First project: I want to make a script that I run that will automatically mount a NFS share on my desktop. 

One other question – would it be best practice if I always mount my shares, and folders in the /mnt location?

---

### Post by sp0nge on 2009-01-23
This is a questions I've been struggling with myself recently...

Python is awesome. I <3 it and use it whenever I can. However, bash is sweet too and very very flexible and powerful. The truth is you can accomplish the same thing with either (for administrative tasks). Python can also extend into OOP which is super sexy and very useful. I'm really new to bash so it may be able as well!? 

That is a bit off topic though... The reason my answer to your question (opinion really) is that you should use bash. Reason being, it is almost always available and powerful enough to accomplish anything you may need/want. I highly recommend the O'reilly book "Learning the bash shell", not that there aren't an abundance of resources online.

The thing I've discovered on my endless quest to know it all is that using the right tool for the right job makes life much easier once you identify when to use what tools and why.

I hope this helps.

---

### Post by stephan0h on 2009-01-23
bash is the screwdriver.
python is the full-fledged toolbox.
depends on the task what you need.

---

### Post by e24ohm on 2009-01-23
> **sp0nge said:**
> This is a questions I've been struggling with myself recently...

Python is awesome. I <3 it and use it whenever I can. However, bash is sweet too and very very flexible and powerful. The truth is you can accomplish the same thing with either (for administrative tasks). Python can also extend into OOP which is super sexy and very useful. I'm really new to bash so it may be able as well!? 

That is a bit off topic though... The reason my answer to your question (opinion really) is that you should use bash. Reason being, it is almost always available and powerful enough to accomplish anything you may need/want. I highly recommend the O'reilly book "Learning the bash shell", not that there aren't an abundance of resources online.

The thing I've discovered on my endless quest to know it all is that using the right tool for the right job makes life much easier once you identify when to use what tools and why.

I hope this helps.hey mate, this realy helps, and since i am very new to both, i think i am going to try to learn both...

thanks...cheers!!!

---

### Post by e24ohm on 2009-01-23
> **stephan0h said:**
> bash is the screwdriver.
python is the full-fledged toolbox.
depends on the task what you need.so just to make a script to mount a folder from my nfs server i would most likley use BASH for this?

thanks...
E

---

### Post by Sorivenul on 2009-01-23
I suggest reading the Sticky threads in the Programming Talk subforum:
[Read Before Posting: Forum FAQ's, how to learn to program, and Linux programming]("http://ubuntuforums.org/showthread.php?t=1006666")
[Programming Tools and References]("http://ubuntuforums.org/showthread.php?t=1006662")

You can also ask for help with both BASH and Python there if you need to.

Good luck!

EDIT: As for a script to mount something from your NFS server, I would think BASH would be fine. Python may be overkill... ;)

---

### Post by Slim Odds on 2009-01-23
Not to start a language war here, but I've used Python before and like it a lot, but I much prefer Ruby for things that are more complex than bash can handle.

bash is great for simple stuff. Just don't try to push it too far.

---

