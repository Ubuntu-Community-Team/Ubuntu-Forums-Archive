---
title: "Poor performance with evolution-exchange component"
date: 2005-10-23
forum: Desktop Environments
---

### Post by VR6Pete on 2005-10-23
Hi,

Using Breezy and the default version of Evolution, I'm interfacing into my work's exchange OWA environment. 

I've set up my account within evolution, but I find it totally unreliable and buggy. 

Some times it's fine, and I can browse some of my my folders. but other times it toally locks up the client for upto 5 minutes at a time, making it totally unreliable  to work with. 

Has anyone else had these type of problems? or have you found any fixes?

Thanks,

Pete

---

### Post by VR6Pete on 2005-10-23
Anyone?

---

### Post by joshmachine on 2005-10-25
Yes, I am having the same problems.  I haven't been trying to hard to find a fix.  I'll dig around and post if I see anything helpful.

Cheers

---

### Post by joshmachine on 2005-10-26
I don't seem to be having any significant problems any more.   I had configured the exchange account folder to copy content for offline access.  i disabled that, and it seems to be working ok now.

You may want to try the following:

run /usr/lib/evolution/2.4/killev (to kill all of evolution and related)

open a terminal and run
export E2K_DEBUG=4 

then start evolution from the command prompt.

This will print out some debugging information from the exchange connector.  hope this help.

cheers.

---

### Post by billycub on 2005-10-26
I am also having no luck with the exchange connector.  It sometimes starts up fine, other times can't connect at all.

After downloading some message headers, it invariably crashes.  Then, killall ev is required or I can't start up again.

Very, very buggy.  Used to be fine with Hoary.  What happened?

---

