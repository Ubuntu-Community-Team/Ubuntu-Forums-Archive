---
title: "/var/lib/dpkg/info What is it?"
date: 2009-01-16
forum: General Help
---

### Post by xxmsaxx on 2009-01-16
This is my first post here in the Ubuntu forums so let me start off by saying Hello:guitar::guitar:!

I do not have a problem so much as I have a story and a question. I have an Ubuntu server that I was using apt-get to install Bacula on, and i was having some difficulty getting it to connect to my mysql DB. I did a remove and when I did the install again I did not get the pop up window I did first time I did the install. So I thought hmmm maybe it has some "ghost settings from the wrong value I input the first time" and proceeded to go into /var/lib/dpkg/info and del bacul.* . After wards of course I could not install or remove any package without getting errors along the lines of: Serious Dpkg Error:yada yada yada. 

 I know now it was a dumb move, but what happened afterward is the box slowed down to a crawl. Any user who would ssh into the box using their ldap credentials (set to auth against our Win03 server) would have lag to the point of where an ls command would take a min to list contents of a home dir. However, if you logged on with a local account it was fine. All web services stayed up and decently responsive. 

 I could not figure out how to get the apt-get to stop giving the errors so I had another Ubuntu  box same ver did same apt-get install and copied all the files from the /var/lib/dpkg/info directory back over to the box I deleted them from and now the box works fine. 

My question is what does this directory do, and why would performance be destroyed like it was by doing what I did?

---

### Post by Ahadiel on 2009-01-16
Lesson: *Don't mess with package manager files by hand.*

If you wanted to remove all configs related to a package,
```
sudo aptitude purge packagename
or
sudo apt-get remove --purge packagename
```

---

### Post by ajgreeny on 2009-01-16
It contains mainly plain text docs about the packages installed, but also a lot of shell scripts relating to them which are executable, and there probably lies your problem; a few perl scripts and one or two other files including one true-type font.  

Why removing a set of them relating to one package should cause such a problem to the system speed, I can't imagine, but it seems to confirm that it can be dangerous to remove system files you know little about.  I'm glad you are up and running again, and I suspect someone else may have more knowledge than me about the reasons for your difficulties.

---

### Post by xxmsaxx on 2009-01-16
Lesson most def learned, and thanks for the reply. It made sense to me that the package manager would give errors after I deleted the files but I just don't understand why it would effect the machine other wise. It may be unrelated but the machine did start to perform normal after I put the files back in.

---

