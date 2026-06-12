---
title: "sync files over network"
date: 2012-11-15
forum: Desktop Environments
---

### Post by rwslippey on 2012-11-15
Hello,

I have been looking for a simple solution to not so big problem or more or less just a pain in the you know what...

I have 2 systems at home. My laptop running ubuntu 12.04 desktop and a server running 12.04 Server... both 64 bit.

I generally work directly on my laptop and I'll generally take it with me when I have to go on the road. The problem is, I'd like to be able to take my laptop with me, modify things, files, databases, ect and then when I return and the laptop sees my local network is connects to my server and copies the files over to the server. 

The main reason is a backup. All my backups are done through the server onto another external disk, additionally I need to open some of these different files up for other users to access them from the web(web sites I'm working on, that kind of thing)

I've looked at mysql replication and think I've got that covered... although with much frusctration (anyone looking to do this, watch your versions... mysql seems to be changing the names of setting in my.cnf)

My question now is, does anyone know of a really good simple file sync tool to go from a desktop version to a server version?

Also just for more information is anyone has seen a really good howto on mysql master/master replication for version 5.5 I'd love to see it...

Thanks

Rob

---

### Post by LewisTM on 2012-11-15
You could run a **rsync** (for one-way sync) or **unison** (for two-way sync) task through an SSH connection, either from the Internet or as soon as you connect to your local network. There is **lsyncd** which monitors file changes and syncs them on-the-fly using rsync.

I don't know of a software that will detect the presence of a server and initiate a sync but I'm sure it could be scripted. 

For the dead simple, services like Dropbox and Ubuntu One will do the sync for you in a more transparent way. The total size may be limiting though.

Cheers!

---

