---
title: "Unity 3D fails in Oneiric"
date: 2011-10-16
forum: Desktop Environments
---

### Post by windfix on 2011-10-16
I have had several problems with Unity 3D suddenly failing in 11.10 (Unity 2D was fine, thankfully). Since it worked with a newly created user, I knew the fault lay somewhere in my home directory.

Workaround:  
1.  I renamed my home directory from paul to paul2
2.  I created a new directory named paul
3.  I moved all my non-hidden files from paul2 back to paul
4.  (I think I also had to change ownership of the entire contents of paul2 with the following command line entry:  [COLOR="SeaGreen"]sudo chown -R paul: paul /home/paul2[/COLOR]) (remove space after the colon)

Unity 3D worked again.

5.  I moved just the config files that I really knew I wanted to keep (those that begin with a . and require CTRL-H to view them).  I moved my mozilla, firefox, thunderbird, and dropbox config folders.

Unity still worked.  

However, next day after working no problems - it happened again.  I had to repeat the above 5 steps to get my user account working in Unity 3D.

This time, I tried moving additional config files until it broke again, then reversed it.  The problem is somewhere in .config.  Based on time stamps on the files that changed just prior to the second breakage, I suspect the file .config/compiz-1/compizconfig/config

In my good version of .config this file is blank.  In the broken version, it reads:

[COLOR="Blue"][general_ubuntu]
profile = [/COLOR]

I am keeping a working copy of this .config file saved as .config.goodcopy just in case.  I hope this helps someone else who is having a similar problem.

---

### Post by deertan on 2011-10-17
Thanks!

Your fix worked for me.

I suspect this is caused by upgrade and wouldn't be a problem for fresh installs.

Too bad fresh installs are such a pain.

Thanks again, you saved me loads of head scratching.

---

