---
title: "Please explain why users can navigate to other users home folders?"
date: 2008-01-20
forum: Desktop Environments
---

### Post by Ted_Smith on 2008-01-20
Why, oh why, do users have read access to other users home folders by default? I've read stacks of similar threads complaing about it, but no-one seems to be able to EXPLAIN to me the thinking behind this idea? Surely the idea of a 'home folder' is for that persons data to be kept private, unless they decide otherwise? I appreciate read access is not as severe as write access, but if I am writing an OpenOffice document with a list of surprise guests for my wife's birthday party, I don't want her being able to log in, navigate to my home folder, and read it!! 

I realise that I can log in as Admin, right click on the home folder, go to permissions, and uncheck all the options for "Others". But that's really not the point. 

Other threads relating to this : 

[http://ubuntuforums.org/showthread.php?t=327174](http://ubuntuforums.org/showthread.php?t=327174)
[http://ubuntuforums.org/showthread.php?t=199008](http://ubuntuforums.org/showthread.php?t=199008)
[http://ubuntuforums.org/showthread.php?t=144111](http://ubuntuforums.org/showthread.php?t=144111)
[http://ubuntuforums.org/showthread.php?t=88932](http://ubuntuforums.org/showthread.php?t=88932)
[http://thread.gmane.org/gmane.linux.ubuntu.devel/12422/focus=12448](http://thread.gmane.org/gmane.linux.ubuntu.devel/12422/focus=12448)

Ted

---

### Post by zetetic on 2008-01-20
Hi Ted_Smith.

It's easy:

sudo chmod -R go-rwx /home/<username>/

---

### Post by Ted_Smith on 2008-01-20
Yes, thanks zetetic, but I already know how to change the permissions and the other threads detail that too. My question is why is it like that in the first place? Why are the home folders of users not made private by default?

---

