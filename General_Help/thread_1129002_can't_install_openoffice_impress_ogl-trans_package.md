---
title: "can't install openoffice impress ogl-trans package"
date: 2009-04-18
forum: General Help
---

### Post by jmexia on 2009-04-18
Hi, 

I have been trying to install the OGL 3d transitions for OO Impress via apt-get. Every time I try however, I keep getting the message that the package cannot be found.

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openoffice.org-ogltrans


Is *ogltrans* in the Jaunty repos?  If not, is there another way of installing it--through an OO extension for example?

Sorry, still a noob!  Thanks...
J.

---

### Post by jdeslip on 2009-04-20
I would also like to know about ogltrans for jaunty.  It doesn't look like it is in the repos.

---

### Post by jmexia on 2009-04-22
I have found this [link]("https://launchpad.net/ubuntu/jaunty/+package/openoffice.org-ogltrans") which implies that there is/was an extension for the *ogltrans* package.  However the link leads to nowhere--well, it really leads you to this message:

> Lost something?

There&#8217;s no page with this address in Launchpad.

If you got here from a link elsewhere on Launchpad, sorry about that. We&#8217;ve recorded the problem, and we&#8217;ll fix it as soon as we can.

Otherwise, complain to the maintainers of the page that linked here.

If this is blocking your work, let us know by sending an message to [email]feedback@launchpad.net[/email]. Include the error ID OOPS-1208G1086 in your message. 

Maybe the official release of Jaunty will include the package.  Although, I heard that OO 3 would have the package installed by default.

Thanks,
J.

---

### Post by jdeslip on 2009-04-22
Ok.  Well, I filed a bug report here: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/365240](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/365240)

---

### Post by jmexia on 2009-04-23
Thanks for reporting it.  You must have gotten this response already:
> 

This is because it was broken on 3.0.x and causes crashes. It will be re-enabled for 3.1.x in Karmic.

Chris

I guess we'll have to wait, or do a manual install of OO 2.4 or 3.1.

Thanks,
J.

---

