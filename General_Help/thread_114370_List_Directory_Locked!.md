---
title: "List Directory Locked!"
date: 2006-01-08
forum: General Help
---

### Post by babygigi on 2006-01-08
$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

Now What? Please Help

---

### Post by stuporglue on 2006-01-08
Do your apt-get update with sudo power!

$ sudo apt-get update

Sudo lets you run a command as super user (root), which apt-get must be done as.

---

### Post by babygigi on 2006-01-08
yeah i've tried that then i get all the hits and everyrthing and tehn it tries to connect but i get that it doesn't... but the internet is working and everything

W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

it does thesame thing when i put in sudo apt-get upgrade it just never connects...
Err [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ wine 0.9.5-winehq-1
  Error reading from server. Remote end closed connection
Fetched 2815kB in 10m12s (4597B/s)
Failed to fetch [http://wine.sourceforge.net/apt/binary/wine_0.9.5-winehq-1_i386.deb](http://wine.sourceforge.net/apt/binary/wine_0.9.5-winehq-1_i386.deb)  Error reading from server. Remote end closed connection
 

Does it have anythign to do with my repositories?

---

### Post by babygigi on 2006-01-08
Anybody know how to fix this?

---

### Post by Thirsteh on 2006-01-08
It does indeed seem like a repository problem. Try using something else than planetmirror. Also, does your /var/lib/apt/lists  folder exist, if it does, is there anything in it?

---

### Post by babygigi on 2006-01-08
yeah it does... it has all my repositories, a partials folder and the file "lock"

---

### Post by Thirsteh on 2006-01-08
I don't know then, it seems the only possibility is that your repositories are bad, so try changing them.

---

### Post by fct on 2006-01-08
Your repositories are wrong. The planetmirror one seems specially broken (I can't even connect from here).

Try setting the default ubuntu repositories.

P.S.: the wine one looks like a server being down, right now I can download the file here using just the browser. Might work for you now.

---

### Post by babygigi on 2006-01-08
well how do i get back my default repositories? do i manually add them? or is there a easier way?

---

### Post by ::Lagro on 2006-01-08
Applications > Add Applications > Settings > Repositories
Enable the "Universe" & "Multiverse" sections.
You cand delete all, and after that Add again all (**Ubuntu 5.10 "Breezy Badger"** Binary, **Ubuntu 5.10 Security Updates** Binary, **Ubuntu 5.10 Updates** Binary) with the options:

Officially Supported
Restricted Copyright
Community maintained (Universe)
Non-free (Multiverse)

---

