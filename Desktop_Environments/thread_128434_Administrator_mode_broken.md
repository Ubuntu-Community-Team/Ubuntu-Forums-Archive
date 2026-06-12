---
title: "Administrator mode broken"
date: 2006-02-11
forum: Desktop Environments
---

### Post by memius on 2006-02-11
I'm trying to get access to the internet, but kde won't let me go into administrator mode to change my network settings.

I hit the 'administrator mode' button, and the prompt for password comes up. I enter my password, and I am told the password is incorrect. I know it's the right password, because I manage to log in every time I start the computer.

As i understand it, this works like sudo, so it wants my user password, not the root password. I have, however, tried entering the root password too, with the same results.

From the second try out, I am told 'conversation with su failed'.

When I try to sudo in the terminal, I am also told that the password is incorrect.

---

### Post by Neo Ex on 2006-02-11
1. Are you using KControl or the System Settings program?
2. Why don't you try to change you password? KControl -> Security and Privacy -> Password and user account.

---

### Post by memius on 2006-02-12
I have tried both, of course, and I have tried with a variety of passwords.

---

### Post by gingermark on 2006-02-12
Are you using the account that you set up when you installed Kubuntu? I think sudo only works with that one. Not sure, but that's all I could think of anyways...

---

### Post by memius on 2006-02-13
I did an expert install, and it seems the first user, which I'm using is NOT allowed to use sudo, so I tried creating another user, but he can't use sudo either.

---

### Post by memius on 2006-02-13
Now, I've managed to get sudo priviliges, by adding the line username ALL = ALL in the sudoers file. The administrator button has changed its behavior, but it still doesn't work. Now, it pretends nothing happened, and goes back to before I invoked it without any error messages.

Update: suddenly, I got admin privileges. I typed kcontrol in the terminal, and got a bunch of error messages. It didn't work at all. In my frustration, I typed it again, and then it worked, albeit with a lot of error messages in the terminal window behind it. This is black magic. Sigh.

---

### Post by klett on 2006-02-13
Hi,
I've had the same problem recently. Deleting /home/your_user/.kde solves it, but I think it's not the best solution since it doesn't look for the source of the problem.

---

