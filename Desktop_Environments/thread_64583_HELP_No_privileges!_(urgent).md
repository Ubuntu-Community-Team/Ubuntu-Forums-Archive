---
title: "HELP: No privileges! (urgent)"
date: 2005-09-11
forum: Desktop Environments
---

### Post by Zalbor on 2005-09-11
When I installed Ubuntu, I created a user by (let's say) the name of "bill". For reasons that don't really matter, I decided to create another user (let's say "will") and delete bill. Before I did that though, I **did** give Will all privileges through the users-admin tool.
I'm not sure that this is what caused the problem, but now Will seems to have no privileges at all. I can't sudo, I can't connect to the internet (I'm using the live-cd right now), I don't hear any sound, I can't do anything.

How can I fix this?

---

### Post by lol on 2005-09-11
I am not 100% sure about this, but... using the live CD, you can mount the root partition on your drive, and edit /etc/shadow. Remove the password for the root user, and reboot. This should enable you to log in as root without any password. Of course, the first thing to do right after this is to setup a new password for root (with the command 'passwd').
As root, you should have no problem to check/correct the permissions for "Will"...

---

### Post by Zalbor on 2005-09-11
I never set a password for root, the shadow file only has a * there. Should I delete this for it to work?
And also, if I do log in as root, it will be from a terminal, right? So I won't be able to run users-admin. Is there a terminal tool that can help?

---

### Post by Zalbor on 2005-09-11
[QUOTE=Zalbor]I never set a password for root, the shadow file only has a * there. Should I delete this for it to work?
And also, if I do log in as root, it will be from a terminal, right? So I won't be able to run users-admin. Is there a terminal tool that can help?[/QUOTE]
 Alright, they told me how to make it work. In case someone reads this someday, here's what I did:

Chose the "recovery mode" option from GRUB
Ran the command "adduser will admin" which made "will" able to use sudo
Logged in as "will" and used users-admin to fix the rest of the privileges.

---

