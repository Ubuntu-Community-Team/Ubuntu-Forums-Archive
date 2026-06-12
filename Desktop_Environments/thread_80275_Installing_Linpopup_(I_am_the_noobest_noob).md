---
title: "Installing Linpopup (I am the noobest noob)"
date: 2005-10-21
forum: Desktop Environments
---

### Post by likesilverr on 2005-10-21
I am brand new to this program, and I am not a programmer.  I can't get any of the install commands to work off of ubuntuguide.com.   I says "host not found" or something about the E drive.

can someone please IM me over AIM (SX5622) and help me out!

---

### Post by DJ_Max on 2005-10-21
Couldn't have mention something about an *E* drive...

What command(s) are you trying to run?

---

### Post by likesilverr on 2005-10-21
stephen@humpy:~$ sudo apt-get install linpopup
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linpopup
stephen@humpy:~$


I have no idea how to do this.

Also - is there a way I can connect to my LAN and retrieve files off of another computer?

---

### Post by invalid on 2005-10-21
> stephen@humpy:~$ sudo apt-get install linpopup
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linpopup
stephen@humpy:~$

What does this have to do with "host not found"?

Anyhow, you probably just need to edit your repositories to the correct locations. 
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Cheers,
Cb

---

### Post by aysiu on 2005-10-21
[QUOTE=invalid]What does this have to do with "host not found"?

Anyhow, you probably just need to edit your repositories to the correct locations. 
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Cheers,
Cb[/QUOTE] That's out of date. Try this instead:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

---

### Post by likesilverr on 2005-10-21
[QUOTE=invalid]What does this have to do with "host not found"?[/QUOTE]


If i try to install limewire or any other program like that it says host not found 

stephen@humpy:~$ wget -c [http://frankandjacg.com/ubuntuguide/limewireother.zip](http://frankandjacg.com/ubuntuguide/limewireother.zip)
--20:20:46--  [http://frankandjacg.com/ubuntuguide/limewireother.zip](http://frankandjacg.com/ubuntuguide/limewireother.zip)
           => `limewireother.zip'
Resolving frankandjacg.com... failed: Host not found.


EDIT:  Is there a way to update versions without reinstalling?  I have 5.4 and want to upgrade to 5.10

---

### Post by DJ_Max on 2005-10-21
Again, this has nothing to do with you installing programs. frankandjacg.com doesn't even exsist. So of course you can't download anything for it.

Use synaptic to install programs. Read documentation.

---

### Post by aysiu on 2005-10-22
[QUOTE=likesilverr]
EDIT:  Is there a way to update versions without reinstalling?  I have 5.4 and want to upgrade to 5.10[/QUOTE] There is a way, but I think you have to slow down and explain more about your situation. Is your internet connection working in Ubuntu? If so, just follow the directions people have given you in this thread (the Ubuntu Guide is out of date right now) and you should be fine for installing the stuff you want to install.

I'd stick with 5.04 for a while until you're a bit more comfortable with installing software. Doing a dist-upgrade is probably not something for someone who proclaims herself/himself as "the noobest noob."

---

