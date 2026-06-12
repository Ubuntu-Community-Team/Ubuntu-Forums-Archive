---
title: "xrdp user permissions problem"
date: 2009-04-26
forum: General Help
---

### Post by u1tramarine on 2009-04-26
Hi there,
Im using xrdp to use my windows machines to connect to my Ubuntu machine (9.04) but i do have one problem.

I have installed Xrdp with no problems and it works (yey!) but whenever i try to run certain applications i get the following message (note: i got this error trying to run synaptic)

Failed to run /usr/sbin/synaptic as user root.
Unable to copy the users Xauthorization file.

Does anyone know how to get around this or do i have to use vnc to get around this problem?

---

### Post by TwistedLincoln on 2010-01-24
I don't normally bump such old threads, but since I just ran into the exact same problem with Karmic, I though I might post the solution in case someone else runs into this:

Create a blank .Xauthority file in the home directory of the user you are connecting with.  Be sure to log in as that user (either graphically, or via the terminal), then run:

touch ~/.Xauthority
chmod 600 ~/.Xauthority

After that, apps such as Synaptic will run without giving you that error.

---

### Post by Whammy on 2010-12-04
> **u1tramarine said:**
> Hi there,
Im using xrdp to use my windows machines to connect to my Ubuntu machine (9.04) but i do have one problem.

I have installed Xrdp with no problems and it works (yey!) but whenever i try to run certain applications i get the following message (note: i got this error trying to run synaptic)

Failed to run /usr/sbin/synaptic as user root.
Unable to copy the users Xauthorization file.

Does anyone know how to get around this or do i have to use vnc to get around this problem?
Thank you!

---

### Post by izrafeel on 2010-12-15
TwistedLincoln, thanks for posting this solution.  I recently configured xrdp on Lucid and was running into this permissions error whenever I tried running system updates (during the xrdp session).  Now it's fixed!

---

### Post by mrmikefm on 2011-01-09
Thanks I've been fighting this RDP thing for a day now!!!!!!!!!!!!1

---

### Post by wormyblackburny on 2011-03-31
technically you could just run:

sudo /usr/sbin/synaptic (or whatever the error message is)

But your solution provides a permanent fix rather than a workaround, and for that I thank you! Had this exact same problem and was tired of copying and pasting into terminals to do stuff :)

---

### Post by t3ddyg on 2011-07-31
> **TwistedLincoln said:**
> After that, apps such as Synaptic will run without giving you that error.

THANKS SO MUCH! Helped me out big time.

---

### Post by t_huankiat on 2011-08-03
> **TwistedLincoln said:**
> I don't normally bump such old threads, but since I just ran into the exact same problem with Karmic, I though I might post the solution in case someone else runs into this:

Create a blank .Xauthority file in the home directory of the user you are connecting with.  Be sure to log in as that user (either graphically, or via the terminal), then run:

touch ~/.Xauthority
chmod 600 ~/.Xauthority

After that, apps such as Synaptic will run without giving you that error.

Just want to also confirm that this works like a charm! Thank you for your help!

---

### Post by drahst on 2011-10-17
any issues creating / editing users?

I'm using xrdp on lucid and the .Xauthority file worked, but I'm still unable to manage users via the Users and Groups app. 

Any ideas?

---

### Post by RKGraves on 2012-01-07
Thanks for posting this fix. I appreciate that you took time to share the solution! This fixed worked great on 10.04.3. And no issue using the Users and Groups utility via a Windows RDP client.

Again Thanks!

---

### Post by menelaosbgr on 2012-02-22
Great Post...

Saved me quite some trouble..even in 2012 :D

---

### Post by jdieter on 2013-02-08
Just ran into this today. 8 years and still a problem. Gotta love it.

---

### Post by wildmanne39 on 2013-02-08
Old thread closed.

---

