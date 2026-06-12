---
title: "How best to share files between users on one computer?"
date: 2009-02-09
forum: General Help
---

### Post by Brian Vaughan on 2009-02-09
Today, my partner was frustrated, because I'd saved a spreadsheet in my /home/[mylogin]/Documents folder, which she wanted to edit, but that required logging in to my account, and she didn't have my password.

This raised the question of how best to have handled a file that would be edited by multiple users. There must be a relatively straightforward to do this, since obviously this is something most *nix users would want to do in a shared system. But I'm not sure how best to approach the problem.

Of course, it would be easy to create a folder, say /home/shared, and give all users read and write access to it. I expect it wouldn't be difficult to have that folder appear in the "Places" menu in Gnome (though I don't know how exactly to do that). But, the big problem I see is that files, by default, are created with read and write permission for the user, but only read permission for the group and for others -- i.e., -rw-r--r--, when you'd want a file available for multiple users to edit to have permissions like -rw-rw-r-- or -rw-rw-rw-, that is, writable for members of a group or for everyone.

Individual files could be fixed with chmod, but that would be a nuisance to do it one at a time for each file. Is there a straightforward way to set things up that way, automatically, perhaps just for files placed in a certain directory?

---

### Post by photon_man62 on 2009-02-09
I suggest making a new partition, and not mounting it as /home, / or anything.

---

### Post by photon_man62 on 2009-02-09
Or, you can also make a new folder in /home and both of you can use it.

---

### Post by Brian Vaughan on 2009-02-09
Making a folder in /home seems to be the obvious thing to do. It's the file permissions that's the real puzzle to me.

---

### Post by Slim Odds on 2009-02-09
> **Brian Vaughan said:**
> Making a folder in /home seems to be the obvious thing to do. It's the file permissions that's the real puzzle to me.

Create a new group
Make both of you members of that group
Make the shared folder belong to that group

Done.

---

### Post by bodhi.zazen on 2009-02-09
It is not as simple as it seems ...

See if these links help :

[http://hep.pa.msu.edu/user/groups.html](http://hep.pa.msu.edu/user/groups.html)

    Set Group ID : chmod g+s dirname

    OR (ACL works better)

    ACL : [http://ubuntuforums.org/showthread.php?t=145741](http://ubuntuforums.org/showthread.php?t=145741)

      or [http://ubuntuforums.org/showpost.php?p=1193555&postcount=1](http://ubuntuforums.org/showpost.php?p=1193555&postcount=1)

---

