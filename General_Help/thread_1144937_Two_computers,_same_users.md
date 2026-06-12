---
title: "Two computers, same users"
date: 2009-05-01
forum: General Help
---

### Post by randyklein99 on 2009-05-01
I have 2 computers, 1 desktop and 1 laptop.  I have two users that will need to be able to use both computers.  Also, I want the desktop to hold all of our pictures/videos data and share it between both computers and both users.

How can I setup the computers and users so that no matter what computer I'm working on, it's the same user profile with the same settings, same everything.

I probably don't have the terminology correct, but is this a server vs desktop issue?

---

### Post by loell on 2009-05-01
you might looking for LDAP (Lightweight Directory Access Protocol) .

---

### Post by lisati on 2009-05-01
A few thoughts to help start the ball rolling. Note: There's more than one way of tackling your question.

**Option 1:** set up file sharing so that the user of one computer can access some of the files on the other computer using the places->network menu item. One way of doing this can be found [here]("http://ubuntuforums.org/showthread.php?t=202605")

**Option 2:** use remote login, (In other words, use one computer as a smart terminal for the other computer.)

**Option 3:** .... (there are probably more)

---

### Post by randyklein99 on 2009-05-01
I like option 1 so far, with the shared folders.  But is there a way to map the Pictures folder on both computers to the shared folder?  That way opening up the folder on the laptop is really opening up the folder on the desktop.

Since they are both Linux, I don't need Samba for this right?

---

### Post by Iowan on 2009-05-01
> **randyklein99 said:**
> Since they are both Linux, I don't need Samba for this right? Samba is an option, but not a requirement.  There's also NFS, SSHFS - to name a couple.

---

