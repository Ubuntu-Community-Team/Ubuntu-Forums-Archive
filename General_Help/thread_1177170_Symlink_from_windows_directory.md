---
title: "Symlink from windows directory"
date: 2009-06-03
forum: General Help
---

### Post by HandleWithCare on 2009-06-03
So, I think this is rather impossible, but I've been wrong before so lets give it a shot. At the webdesign company where I work we use config (.ini) files on our local testmachines to set some environment variables. One of these is where the main system (the cms) is located. This is a path like "D:/path_to_cms". Since I prefer ubuntu over windows I try to pursue my colleagues to use a different approach, but for so far without any luck. 

So what I hope is possible, here it comes, to make some sort of a symbolic link which points "D:/" to let's say "/home/myuser/www/".

---

### Post by HandleWithCare on 2009-06-04
bump

---

### Post by HandleWithCare on 2009-06-05
bump

---

### Post by d3ngar on 2009-06-05
Hi Handle,

What you are doing is actually really simple (I'm going to assume that you have the other windows disk (D) mounted already):

Try the following:
```

ln -s  /media/[REST OF DRECTORY HERE] /home/[username]/www 

```

This works for me.
Let me know if you have problems

---

### Post by HandleWithCare on 2009-06-05
I think you misunsderstood my problem or I explained it wrong. There is no windows disk at all. I only have a config file witch points to 'D:/some_path'. Since there's no 'D:/' in ubuntu it will be unable to open this path. The contents the config file point to is in my case '/home/myuser/www/'. Sowat I want is that whenever a filename starting with 'D:/some_filepath' gets requested it wil internally be altered/redirected to '/home/myuser/www/some_filepath' like a symlink.

---

### Post by Chronon on 2009-06-05
What program are you running that makes use of this config file?

---

### Post by HandleWithCare on 2009-06-05
As you can read in the topicstart I work for a webdesign company. We have build a custom cms for our clients. It uses a configfile to set some 'system-wide' variables. One of these is the location of the cms on the server. On our local testmachines this is always 'D:/something' since we all use the exact same setup. We use subversion (svn) as our revision control system which means that these configfiles get committed as well when it changes. This means that when I want to work on some project at home (where I run ubuntu) I have to change the filepath, I can't set it to .ignore since things might change during development. 
Besides this, we have a set of tools, some of which are quite old that don't have a config file so the 'D:/someting' is hardcoded in many places.

---

### Post by HandleWithCare on 2009-06-11
bump

---

### Post by HandleWithCare on 2009-06-12
BUMP,

common, someone must know the answer to this, just a simple "no" or "yes, this way..." will do.

---

### Post by HandleWithCare on 2010-02-23
It has been a while, but I am still looking for this. So far I haven't founs a single soul how could give me an answer, but I'm sure someone exists out there knowing the answer?

---

### Post by eriktheblu on 2010-02-23
Would it be possible to edit the config file to be conditional based on the presence of those subdirectories?

---

### Post by HandleWithCare on 2010-02-23
yes, of course. But since the file is under svn version control it will overwrite the settings so than I will have to keep changing. I'm looking for a robust solution.

Edit, no it can not now that I think of it. The config file can not have conditions, the file that reads the config file on the other hand can, but same as above for that

---

