---
title: "How do I remove the boatload of crap that comes with Ubuntu and still be able to work"
date: 2006-08-14
forum: Desktop Environments
---

### Post by harisund on 2006-08-14
Hello

I did a server install of AMD64 Ubuntu on my laptop and hit 'aptitude install ubuntu-desktop' by mistake. 

End result, I have a whole bunch of programs and services running that I *least* need. To name a few, CUPS, Avahi, mdadm, EVMS, spamassasin, LVM, postfix (I know Ubuntu is for your average joe and granny next door. Why they will need postfix is beyond my comprehension)

I know, I know, I can disable all those services by using something like update-rc.d or just deleting the symlinks. 

But my point is I want my system to only have software that I know or I deliberately want. 

Here's my problem. I remove postfix and it complains. anything I remove ,the ubuntu-desktop meta package vanishes. Why? Is it ok if I let go ubuntu-desktop? When I was upgrading from breezy to the various alphas and betas of dapper, I was told the ubuntu-desktop package was quite important. Now it vanishes with every small software I remove? 

Aside from switching to a way more powerful distro than Ubuntu (say Gentoo, or Debian), what are my options to have a system the way I want it rather than the way the developers want it? Or is Ubuntu so grandma friendly that like OS X, I just have to live with what is given to me and shouldn't be complaining?

---

### Post by calx on 2006-08-14
How about just reinstalling.

---

### Post by Titus A Duxass on 2006-08-14
I think what you want is a minimal install.
You can then select which WM you want or not.

Have a search with xcfe or icewm as a topic.

---

### Post by harisund on 2006-08-14
How about just reinstalling what? 

I will reinstall and still end up getting everything, right? What advantage does that provide?

---

### Post by anthro398 on 2006-08-14
> **harisund said:**
> How about just reinstalling what? 

I will reinstall and still end up getting everything, right? What advantage does that provide?

The advantage, obviously, would be that you not accidently select "ubuntu-desktop."  That is what you wanted, right?

---

### Post by ardchoille on 2006-08-14
The ubuntu-desktop package is just a meta package, it brings in other packages for a nice gnome desktop but the ubuntu-desktop package is empty in itself. It is safe to remove, I did that a long time ago, and the system will operate just fine. You might want to re-install it if you plan to upgrade from one Ubuntu version to the next.. but I always install a new version from an install CD.

---

### Post by harisund on 2006-08-14
Thanks ardchoille! That's what I wanted to hear, that it is safe to remove the Ubuntu desktop meta package. 

And with regards to the previous posts, sorry, I didn't realize you meant I should reinstall the server edition and go for a relatively less heavy desktop. :D.

The thing is, I still want Gnome, Firefox, Gaim, Thunderbid, OpenOffice and all that, just not the entire ubuntu-desktop stuff.

---

### Post by Titus A Duxass on 2006-08-14
As I said before, do a minimal server install then add the required WM and packages or install xubuntu.

sudo aptitude update
sudo aptitude install x-window-system-core xterm gdm icewm menu firefox synaptic

this will give you the basics.

---

