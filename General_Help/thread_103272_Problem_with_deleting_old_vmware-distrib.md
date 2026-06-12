---
title: "Problem with deleting old vmware-distrib"
date: 2005-12-13
forum: General Help
---

### Post by NZ-Wanderer on 2005-12-13
I have a little problem I am hoping someone will be able to help me with...

The Story:
I have been running vmware 5.0 but it is due to expire in 4 days :(
I have now got the latest vmware 5.5 and want to install it..

Problem:
the vmware-distrib folder in home/john has a real BIG padlock on it

Question:
How on earth do I get rid of the padlock so that I can copy the new files into that folder (I presume I can just copy the new files over top of the old files since I dunno how to delete whole folders..)

Help please.... :)

---

### Post by BabaFree on 2005-12-13
In Terminal, go to the directory that houses you VMWare folder and use the command ```
sudo chmod -R 777 VMWarefoldername 
```  Hope this helps, it did for me when I ran across that annoying Padlock.  By the way, I love the history in Terminal.  I used the above command weeks ago and just pushed up until I got to it :)
BabaFree

---

### Post by NZ-Wanderer on 2005-12-13
Thanks for that :)

Worked great....

Only problem is that I have now discovered that nearly every file and folder inside vmware-distrib also has that damn padlock on it.. - It gonna take me forever to unlock them all....

Update: - did a * instead of filename and it seems to have worked...

Now when I do a "tar xzf VMware-workstation-5.5.0-18463.tar.gz"

I get: "Cannot utime: Operation not permitted"

Fixed that as well, deleted the whole vmware-distrib folder, then used the File Browser to manually unpack the files...
Now all I need to do is install it :)

Update 2: All installed and running perfectly...

Thanks for the original help :)

---

