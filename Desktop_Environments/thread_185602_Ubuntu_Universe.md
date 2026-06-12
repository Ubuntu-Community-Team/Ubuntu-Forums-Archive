---
title: "Ubuntu Universe"
date: 2006-06-01
forum: Desktop Environments
---

### Post by helpdeskdan on 2006-06-01
I don't understand why this is not working.  Quick look at my /etc/apt/sources.list includes:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

Apt-get update, pull up aptitude, look for bcrypt.  /bycr... nope, not there. 

Yet, it should be there!  
[http://us.archive.ubuntu.com/ubuntu/pool/universe/b/bcrypt/](http://us.archive.ubuntu.com/ubuntu/pool/universe/b/bcrypt/)

Have I done something wrong?  Is there more than one universe at this site?

Thanks, 
-Dan

---

### Post by Phlosten on 2006-06-01
my sources.list includes a '/' as the end of the first bit.

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse


Obviously replace 'dapper' with 'breezy' for your case.
Don't know if the / makes the difference but worth a try.

---

### Post by helpdeskdan on 2006-06-01
Yeah, it was worth a try, but it didn't work.  I can't imagine why.  Would there be any reason why this would not update?

---

### Post by helpdeskdan on 2006-06-02
$ sudo apt-get update
...
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
....
Looks right!

Perhaps apt is really messed up.  When I click on "Add Application" and then hit file -> Advanced, I get a message "Unable to get exclusive lock." There is no lock though; I haven't launched aptitude and if I try to launch it, I have no problems.  This is a minor inconvenience; I can use aptitude instead, but I have to wonder if it's a symptom of a deeper problem.  Security updates have been working fine though.  I added a wine repository recently which works fine.  Weird. 

I really hope to not have to reinstall; I've got my voodoo3 3500 card setup correctly and I can't even remember how I did it.  :(

---

