---
title: "Question about X, SSH, XDMCP for use with thin clients."
date: 2005-08-24
forum: Desktop Environments
---

### Post by Whatsisname on 2005-08-24
Greetings. 

I am trying to setup a little computer lab sort of setup, using a decent server and a bunch of thin clients. The best way for that would be using XDMCP to use remote graphical logons on all the terminals. My question is, is it possible to encrypt X through SSH before a user even logs in? I don't really want to have to have users startx manually or rely on a script in .bashrc, doing so would really be confusing to users. Does anyone have any experience with this? If SSH doesn't work, is it possible to use SSL or some other encryption method?

Thanks.

---

### Post by Gerie Langeveld on 2005-08-28
Take a look at [The Linux Terminal Server Project](http://www.ltsp.org) 

For Ubuntu I found a page on the wiki.
The first is a project in pre-alpha state, but it mentions SSH: [Thin Client How-To](https://wiki.ubuntu.com/ThinClientHowto) 
Maybe this can help you get started.

Cheers,
Gerie.

---

