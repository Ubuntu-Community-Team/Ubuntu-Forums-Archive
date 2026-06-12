---
title: "No root password"
date: 2006-01-10
forum: General Help
---

### Post by Red Knuckles on 2006-01-10
When I installed Ubuntu [just hours ago] it never asked me to create a root password. I can't become root in terminal with 'su' or 'su -'. How do I address this issue???:confused:

---

### Post by southernman on 2006-01-10
It's the same as the user's password you setup during the installation.

You would need to type in: 

> sudo su

at the command prompt.

---

### Post by healychan on 2006-01-10
One of the difference between Debian and Ubuntu is that Ubuntu remove (although I say remove but that isn't what happened, in fact, we still have the root account with uid 100) the root account.

In Ubuntu, we use sudo to gain the root privilege.

---

### Post by Red Knuckles on 2006-01-11
Hey, thanks guys. That was kind of a RTFM question anyway and I should have realized it before posting. I then discovered the "Ubuntu FAQ Guide" and the How to for "Restricted Formats". Very Helpful. In fact we all should be guided to them as soon as initial install is complete. The two documents remind me very much of the "Stanton-Finley Fedora Core Installation Notes" except that for me things have gone faster and easier in Ubuntu.:D 

At any rate this is well covered in the "Ubuntu FAQ Guide".:rolleyes:

---

