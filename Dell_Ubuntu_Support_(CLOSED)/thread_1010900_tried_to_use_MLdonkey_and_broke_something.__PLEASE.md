---
title: "tried to use MLdonkey and broke something.  PLEASE HELP"
date: 2008-12-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chee on 2008-12-14
i recently was given a 4gb ipod nano video which seems pretty neat.  so i was trying to use Phex to gets tome songs to put on it but for some reason Phex wasn't doing anything.  i thought maybe i should look for another program so i gogled it and came up with MLdonkey.  i downloaded it out of the repos and it seemed to be fine but none of the networks or servers would connect so i did some searching and found out it was going to be harder then this NOOB is used to.  i thought i would try one last thing before giving up on the thing and a tutorial on how to set up MLdonkey said to run this:
 sudo apt-get build-dep mldonkey-server
so i did and it took a while but everything seemed fine,  except that when i tried to open my synaptics it gave me this message :
 An error occured
 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to    correct the problem. 
E: _cache->open() failed, please report.

now when i boot up my log in sceen is even different.  i haven't found any other problems yet. i have no idea what i did or why it went wrong.  i would really just like to go back to where i was before,  i know,  that is always what you want to do when you make a mistake.

any help would be greatly appreciated.  thank you.

---

### Post by ajgreeny on 2008-12-14
Just run ```
sudo dpkg --configure -a
``` in terminal and it should correct everything for you.

---

### Post by chee on 2008-12-14
thank you very much.  i apologize for the noob question.  everything seems to be fine now.

---

