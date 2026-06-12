---
title: "Admin user not in sudoers file???"
date: 2009-01-17
forum: General Help
---

### Post by CaesarLike on 2009-01-17
HI there,

Okay your going to love this one, its another - Ooops I stuffed up Ubuntu post.

So what has happened is this, I have been learning to use the terminal, and have been using the useradd, usermod, groupadd etc commands.  Somewhere in all this it seems I have stuffed up the sudoers file, as my main admin account can no longer act as root.  When I try to use sudo for anything I get a mesage saying the user is not in the sudoers file.  As I was creating groups, and making various groups the users extra groups, I suspect I may have stuffed up the main group for the admin user account, or something along these lines.

So, the obvious question is this, can this be fixed and if so how?  I am using Ubuntu 8.10.

---

### Post by kerry_s on 2009-01-17
boot into single user mode and "vi /etc/group" then fix it.

---

### Post by CaesarLike on 2009-01-17
Thanks Kerry, but this then leaves 2 problems, what exactly do I fix, and second, I have no idea how to use vi.  I know what it is but not how to use it.

---

### Post by DeMus on 2009-01-17
> **CaesarLike said:**
> Thanks Kerry, but this then leaves 2 problems, what exactly do I fix, and second, I have no idea how to use vi.  I know what it is but not how to use it.

Use gedit instead.

DeMus

---

### Post by ajcham on 2009-01-17
Boot to a root shell, and use the command:
```
adduser YOUR_USERNAME admin
```

---

### Post by Yellow Pasque on 2009-01-17
To edit your sudoers file, you should use visudo
```
su
visudo
```
Press 'i' to enter text edit mode (You'll see the word 'INSERT' at the bottom of the screen.) Make sure you have these three lines so:
```
Defaults	env_reset
root	ALL=(ALL) ALL
%admin ALL=(ALL) ALL
```
When you're done with vi, press <Esc>, enter this into the command buffer
```
:x
```
and press <Enter>

---

### Post by CaesarLike on 2009-01-17
Thanks everyone for your help.  I can now access the root privileges.

I notice in my groups list /etc/group that I am only in 2 groups, my own and the admin group.  I assume I should be in more groups than that?  Does anyone have a suggestion as to how I wiped out all my group inclusions?

---

