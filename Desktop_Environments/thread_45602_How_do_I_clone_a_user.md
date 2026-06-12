---
title: "How do I clone a user?"
date: 2005-06-30
forum: Desktop Environments
---

### Post by dgantony on 2005-06-30
Hello all,
    I've been using Ubuntu on all my computers (1 desktop, 3 laptops) since Warty. I have a quick question. I set up 2 users - one for me and one for my wife. I made a lot of customizations for me and would like to copy over all the settings to my wife. I tried to copy over all the files and folders in my home folder to my wife's home folder. Only a few settings seem to have stuck. Is there a way to completely clone a user?

Thanks in advance.

dgantony

---

### Post by metasyntax on 2005-06-30
it's doable, here is how I'd do it:

```

$sudo -s (you'll be typing lots of commands, but you can put sudo infront of them all if you'd rather)

# cd /home

# mv wife wife.old (just in case)

# cp -rp husband wife (cp recursivly and preserver permissions)

# chown -R wife:wife wife/ (change ownership recusivly, to owner wife, group wife)

```

replace "wife" with your wife's username, and "husband" with yours.  Of course she can't be logged in that the time or you'll have problems. if anything goes wrong, or dosen't work, you can delete the new "/home/wife", and put the old one back.

HTH,
meta

---

### Post by Xian on 2005-06-30
[QUOTE=dgantony]I tried to copy over all the files and folders in my home folder to my wife's home folder. Only a few settings seem to have stuck. Is there a way to completely clone a user?[/QUOTE]
Don't forget that all those files in your /home folder have your permissions.
If you move them over the permissions will stay intact.

Those all have to be re-set for her username:group.

Easy way I guess would be to rename her /home/username folder ro serve as a backup, then re-create that username folder for her and populate it with everything from your /home directory. Re-set all the permissions and that should finish the job.

---

### Post by dgantony on 2005-07-01
Thanks to Meta and Xian, I have a perfect clone.   :smile: 

Now the problem is that it is too perfect. Firefox gets messed up when I try to open it when logged in as my wife.

When I run:

```
 grep -r '/home/husband/' *
```

in the .mozilla directory, I get 577 occurances in various files. 

I need to replace all occuarances of /home/husband/ to /home/wife/ in multiple files.

After googling I stumbled upon this piece of code :

```
for fl in ./*; do cat $fl | sed 's/husband/wife/g' > $fl; done
```

This works fine with 2 problems :
1) cat breaks when $fl is a directory
2) does not recursively go into sub-directories

Any scripting gurus want to help me out?

Thanks.

dgantony.

---

### Post by dgantony on 2005-07-01
Finally got this to work : :)  :smile:  :) 

```

find ./* -type f | while read fl; do cat $fl | sed 's/husband/wife/g' > $fl.new; mv $fl.new $fl; done
```

---

