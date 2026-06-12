---
title: "America's Army installation"
date: 2006-06-14
forum: Gaming &amp; Leisure
---

### Post by mrmustardman on 2006-06-14
This had to be he easiest installation i have ever done.
So now its installed in my home directory (/home/myname/armyops/)
and I have now idea how to run it.
there is a armyops.sh but im not sure how to run it. 
im new to linux, so please help. :(

---

### Post by eqisow on 2006-06-14
armyops/armyops.sh (in the command line) should do it

Also, you can use the above to make a menu entry with Alacarte if the entry didn't make itself.

---

### Post by mrmustardman on 2006-06-14
nope didnt work
says armyops.sh is not a command

also i dont like the installation in my home directory... im used to windows... 
so is there a place i can put the installation where all the other installations are (like a Program Files)

---

### Post by eqisow on 2006-06-14
OK, run 'sh armyops/armyops.sh' (no quotes) instead.

Also, you can install it in your /opt directory instead of home by running the installer as root. (with sudo)

---

### Post by mrmustardman on 2006-06-14
ok. sh armyops.sh didnot work... so i got to thinkin... maby it isnt .sh ... it is shell script but it dousnt have a file extension. linux is wierd like that... so...
i ran 'sh armyops' and it gave me
'./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory'
what douse this mean?

---

### Post by eqisow on 2006-06-14
Well, from the error I would say you were missing the libstdc++5 package, but ubuntu-desktop is dependant on it, so you *should* have it. Regardless, you can try 'sudo apt-get install libstdc++5'.

(It might also be an issue with it being installed as a user, try uninstalling an dinstalling with sudo perhaps)

---

### Post by mrmustardman on 2006-06-14
i went into the synaptic thing and looked for that package, and found it.
i already had ++6, so i got ++5 also, and it worked... AA started up.
but now i have another problem... there is no background image... its all white. theres buttons but no background image

---

### Post by eqisow on 2006-06-14
no idea about that one I'm afraid :(

hopefully somebody else will know...

---

### Post by mrmustardman on 2006-06-14
ill start a new post for that thanks for your help

---

