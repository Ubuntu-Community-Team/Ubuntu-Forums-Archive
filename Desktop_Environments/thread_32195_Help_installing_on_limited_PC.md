---
title: "Help installing on limited PC"
date: 2005-05-06
forum: Desktop Environments
---

### Post by imc on 2005-05-06
Hey all,

I work at a local school district, and with the year winding down, we're going to be replacing hardware over the summer.  We thought it would be a good idea to, instead of tossing old machines, to install linux with openoffice and sell them for a couple bucks to the student population(that money gets thrown back into our budget to service machines in the district).  We figure some families who don't have the money to afford a brand new machine would find these useful.  The problem is, the resources on each machine are limited.  4 gig hard drive, 300mhz PII, 96-128mb of RAM.  I installed Ubuntu on a test machine, and installed XFCE as well.  XFCE loads up fairly quick, but OO is a dog.  Since we're going to be pushing these as basic word processors and web browsers(they have 3com NICs in them).  So my question would be, how do I go about finding what extraneous services are running on the machine to try and squeeze every little bit possible out of these computers so that they are fairly useable?  With 96MB or RAM, and running gnome, OO writer took over a minute to load.  XFCE knocks that down to about half a minute.  Still, even compared to windows 98, that's terribly slow.  

Any bit of info would be helpful.  :)

---

### Post by shakin on 2005-05-06
Do a board search for 'prelink'. It will speed up OOo a lot.

---

### Post by az on 2005-05-06
It depends.

"OO writer took over a minute to load. XFCE knocks that down to about half a minute. Still, even compared to windows 98, that's terribly slow. "

OO should not take that long to load.  I do not know what the problem is.  Anyway, probably running abiword for word processing would be a better idea.  I think you can be much more productive with abiword on older hardware than with open office.

I think Ubuntu is ideal for older machines.  You can install alternate environments and use whatever tools you need at the time.  

For example, Icewm (or fluxbox) is a really speedy window manager.  Usually, a michine running Linux which uses icewm can get things does a lot quicker than the comparable application in Windows.  You would need to manually install and tweak a lot of stuff, though.  XFCE contains a lot of interesting stuff to make the user's experience pleasant, but without a lot of extra unneccessary junk.

My reccomendation would be to do a default install with some minor changes. 

1.  add "archive-copier/copy=false" to your boot option at install time.  This will save you from filling up your hard drive with all the uninstalled packages on the cd.  I think you get about 300 megs of free space that way.  In your situation, that seems inportant.  You will need to give out an ubuntu cd with each computer, since if the user wants to install a package, it will look for it on the cd, unless a newer version is availble from the repository.

2.  Install XFCE4 using synaptic and tell it to start gnome services.  I beleive this turns on things like the gnome volumem manager which automatically mounts external drives and digital comeras.

Run XFCE as the default window manager.  That way, if an ubuntu tool is needed (like the networking thing, or VNC, or whatever) it is still available.  This should still leave you about 2 gigs of free hard drive space.

3.  If things are still too slow, either try Icewm or add some ram.

---

