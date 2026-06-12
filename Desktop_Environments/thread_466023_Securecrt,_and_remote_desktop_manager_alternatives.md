---
title: "Securecrt, and remote desktop manager alternatives"
date: 2007-06-06
forum: Desktop Environments
---

### Post by jwiener3 on 2007-06-06
I posted a similar question in the beginner talk, but have not heard anything. And after searching I see a few similiar questions in this forum so hear it goes. 
I switched to ubuntu about a week ago and love it. I am a network engineer and I deal with routers and switches a lot so I was looking for an alternative to securecrt, something that will do save profiles, with automatic login, capture text, etc... 
I have setup gnome-terminal to login but it is just not as nice, or doesn't offer similar features.
I am also looking for a remote desktop manager similar to the one in microsoft's 2003 server administrative tools. 

Any help or recommendations would be appreciated.
thanks

---

### Post by volksman on 2007-06-06
There is nothing like SecureCRT that I'm aware of.  Reason is cause Gnome Term will do it all if you know how to tweak it right....

As for profiles I create profiles by doing one of many things:

1) Use your hosts file:

/etc/hosts

IP HOSTNAME

So:

192.1.1.1  router1
172.16.0.1 router2
123.123.123.123 router3

Then 'ssh router2' will do the trick.

2) Create scripts for each host:

/usr/local/bin is a great place to house them,

sudo /usr/local/bin/router1

```
#!/bin/sh

ssh user@192.168.1.1
```
sudo chmod +x /usr/local/bin/router1

then to use that profile run:

router1

from anywhere...


The second method provides more of a "profile" advantage as you can set environmental variables in the script to change term types etc....

As for RDP you can save sessions in "Terminal Services Client" which is in the repos....Pretty descent app...not the same as RoyalTS or the 2K3 Power tool or this new tool I am JUST about to test called visionapp RDP (for windows as I'm forced to use windows at work)....which sounds pretty sweet....

Hope that helps!

---

### Post by jwiener3 on 2007-06-06
Thank you very much I will look at all that stuff. I am more than willing to change the way I do things, just need a little help along the way (which you gave).  from what you stated I shold be able to make it even easier, the crt. :p
thanks again

---

