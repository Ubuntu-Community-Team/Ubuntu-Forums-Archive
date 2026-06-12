---
title: "Help with Krfb"
date: 2006-05-16
forum: Desktop Environments
---

### Post by suziequzie on 2006-05-16
Hi. I was wondering if someone could help me with a problem.

I have installed Kubuntu on my sister's computer.  She likes the games, the way it looks, etc, etc, but is a complete noob when it comes to any administrative tasks.  I sold her my old computer, with the promise of tech-support for as long as she owns it.  However, she lives 3 cities away and usually needs help at the weirdest times, and I have no car.

And she chain smokes and it's a real pain being there in person.

I'd like to get some remote desktop sharing going between our machines so that I can take control of hers and run all administrative tasks for her. 

I believe i'll be using krfb as it's installed as part of kubuntu, but I need to know (and the how-to was kind of hazy to me) whether she should be sending the invitation to me, or vice versa?  Does it matter who initiates the sharing? I know her system password as well (being the one who did the install), so that should be no problem either once I'm in, or will it?

Any help with these questions would be appreciated. Any explicit how-to's or words of advice/caution are also very welcome.

---

### Post by aysiu on 2006-05-16
Maybe [this](http://www.ubuntuforums.org/showthread.php?t=135036) will help?

---

### Post by ryanakca on 2006-05-17
I'll quickly answer your questions.. but you should still read the howto's that aysiu posted...
She needs to create an invite threw Kmenu->Internet->Krfb, and then phone you and give you the password and the address to connect. If she has a router, she needs to make sure that the right ports are open on it. You connect using Krdc, and you'd type in something like:  vnc:/sis.ip.add.ress and click connect. You'll be promted for a password. Enter it and Voilà, connected (hopefully).
I don't know if the connection is encrypted.

---

### Post by suziequzie on 2006-05-19
[QUOTE=ryanakca]I'll quickly answer your questions.. but you should still read the howto's that aysiu posted...
She needs to create an invite threw Kmenu->Internet->Krfb, and then phone you and give you the password and the address to connect. If she has a router, she needs to make sure that the right ports are open on it. You connect using Krdc, and you'd type in something like:  vnc:/sis.ip.add.ress and click connect. You'll be promted for a password. Enter it and Voilà, connected (hopefully).
I don't know if the connection is encrypted.[/QUOTE]

Thanks. Done and now done!  Nice to know I can fix her linux from here.  
Next, getting into her windows os from here.  But that is for another forum.

---

### Post by rich.bradshaw on 2006-05-21
By default (and I don't even know if VNC can have encryption without using SSH tunneling) there is no encryption.

If the krfb server is behind a router then they need to forward port 5900 to themselves on their router, and set krfb to always use that port (alt-f2 krfb, settings tab somewhere).

---

