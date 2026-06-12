---
title: "Home dir permissions for a public account?"
date: 2008-12-22
forum: General Help
---

### Post by nicholasd on 2008-12-22
I'm setting up an Ubuntu desktop for use in a little cybercafe, primarily for web surfing, email checking, that sort of thing.  The desktop machine will be accessible to the public, and is specifically for their use.  The volume of customer traffic is pretty low.  I'd like some reccomendations on how to configure the computer.

So far, I have set up the computer with my own account (for administration), and an account named "public".  "Public" logs in automagically on startup.  I have installed all the software I need to make the computer usable (multimedia, web browser & plugins, you name it...) and I have configured the account the way I like it.

I would like to set it up so that a user can't permanently change the "public" account settings, but can change them temporarily for their own use.  Should I be write-protecting the home directory some way?  What would the best course of action be?

Also, is there any way of setting up an account so that it does not require a password? (I can hear the security-minded folks just cringing right now)  Don't worry, I'm not allowing inbound ssh access to this account, and it has seriously limited permissions :-)


So what say you all?  What is the best setup for a computer that is going to be used primarily by the unwashed masses^H^H^H^H^H err... public?

I would really appreciate your input!

---

### Post by dcstar on 2008-12-22
> **nicholasd said:**
> I'm setting up an Ubuntu desktop for use in a little cybercafe, primarily for web surfing, email checking, that sort of thing.  The desktop machine will be accessible to the public, and is specifically for their use.  The volume of customer traffic is pretty low.  I'd like some reccomendations on how to configure the computer.
.............
So what say you all?  What is the best setup for a computer that is going to be used primarily by the unwashed masses^H^H^H^H^H err... public?

I would really appreciate your input!

[http://ubuntuforums.org/showthread.php?t=338980&highlight=kiosk+cafe](http://ubuntuforums.org/showthread.php?t=338980&highlight=kiosk+cafe)

---

### Post by dagnabit dang doohickey on 2008-12-22
You can copy the contents of the freshly setup public home directory to [/etc/skel]("http://www.linfo.org/etc_skel.html") and, whenever you see fit, delete and create the public user anew.

---

