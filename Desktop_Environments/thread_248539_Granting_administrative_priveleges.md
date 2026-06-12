---
title: "Granting administrative priveleges"
date: 2006-09-01
forum: Desktop Environments
---

### Post by alecjw on 2006-09-01
How can I grant a normal user the same privilges as root?

---

### Post by Anonii on 2006-09-01
You can become a root with the console.
Just type sudo, to become a root for a command. (You wont have to enter your password for 15' in the next sudo commands)
Or "sudo su" to become root for a whole console session. _BUT_ remember to close the terminal when you finish your job, because leaving the terminal open as root is dangerous. Also, read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by alecjw on 2006-09-01
Nah, I mean i want the user to acutally **be** root, s that they don't have to use sudo, but with their normal username.

---

### Post by Ramses de Norre on 2006-09-01
I know you can change the name of root to something else but I don't think you can just make a second user with the same priviliges as root..

---

### Post by alecjw on 2006-09-01
I'll add it as a feature request for edgy then.

---

### Post by Anonii on 2006-09-01
> **alecjw said:**
> Nah, I mean i want the user to acutally **be** root, s that they don't have to use sudo, but with their normal username.
Why would you want to do something like that?

---

### Post by alecjw on 2006-09-01
Because the "please type in your password" thing's very annoying and i'm not *too* interested about security.

---

### Post by Anonii on 2006-09-01
So.. You want the default user to be the root? Thats masochistic. And I dont really think that your request will be granted. Its tooooooo unsafe and tooooooo careless and tooooooo non-sense.

---

### Post by alecjw on 2006-09-01
Well, lets just wait and see then!;)

---

### Post by Ramses de Norre on 2006-09-01
It's not really possible I think.. I'm afraid (and glad maybe) that the current system for file permissions just doesn't support a feature like this..

And I just think of this: you might be able to use sudo without a password prompt, so you will need to type sudo for your commands but you wont need to type passwd. 

To obtain:
```
export EDITOR=gedit && sudo visudo
```
Then add a line to permit nopasswd on all apps, I'm not sure how to make that line though..

---

### Post by ayoli on 2006-09-01
make root become default user is a really bad idea on linux i think.
the line to add to sudoers must be something like this:

```
username ALL = NOPASSWD: ALL
```

regards.

---

### Post by kazuya on 2006-09-01
I agree that it is unsafe, but I won't stop you. I do not know that you can fully do that, but the answer may lie in you first enabling a root user.
Do you know how to login as root? Once you do this, you should be able to go into user group and modify your normal user's administrative rights and group. 

I do warn you that this is a setup for disaster though for a primary machine. It still comes up as being safe though if you know what you are doing? 

But I understand your frustration with wanting to maybe move files from one partition to another and having to some how use sudo commands. 

Would just enabling a root account and login be enough. Then you can just login as root exclusively and work as root all the time. 

I used to want to do this, but by learning the other way, I started to see why they designed Sudo as they did. I thank them for the design. It really minimizes the issues that users face and teaches a safe working habit.

---

### Post by MrHorus on 2006-09-01
> **alecjw said:**
> I'll add it as a feature request for edgy then.

lol

---

### Post by Ramses de Norre on 2006-09-01
> **ayoli said:**
> The line to add to sudoers must be something like this:

```
username ALL = NOPASSWD: ALL
```
I tried that one but it didn't work.. (I tested a couple of possibilities trying to find an appropriate line)

---

### Post by ayoli on 2006-09-01
after a test, this one seems to work for me:
```
username ALL=(ALL) NOPASSWD: ALL
```

---

### Post by Ramses de Norre on 2006-09-01
It doesn't here.. I added a line like that to my /etc/sudoers file and logged in on a tty, I need to give my passwd for sudo there as usual.
Did you run a sudo -K after the visudo command to make sudo forget your passwd? You never need to give in your passwd in the next 15min after you entered it in the same terminal.

---

### Post by ayoli on 2006-09-01
nope i tried with another user who has not used sudo today.
and i've just teed as you said with a sudo -K before, it works.
regards.

---

### Post by alecjw on 2006-09-01
so i just need to run sudo -K then?

---

### Post by ayoli on 2006-09-01
> **alecjw said:**
> so i just need to run sudo -K then?

sudo -K just make sudo forget your passwd as Ramses de Norre said above.

here's my sudoers:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
ayoli ALL=(ALL) NOPASSWD: ALL
```
last line alow user ayoli to do sudo commands without entering password.
regards.

---

### Post by Ramses de Norre on 2006-09-01
No no, you need to add a line like ayoli's to your /etc/sudoers file. Edit that file with ```
export EDITOR=gedit && sudo visudo
```
Hopefully it will work on your machine. 

And maybe I have something strange configured here not letting that line work..

Ow and don't mind the sudo -K, that's of no use to you.

---

### Post by ayoli on 2006-09-01
> **Ramses de Norre said:**
> No no, you need to add a line like alecjw's to your /etc/sudoers file. Edit that file with ```
export EDITOR=gedit && sudo visudo
```
Hopefully it will work on your machine. 

And maybe I have something strange configured here not letting that line work..

Ow and don't mind the sudo -K, that's of no use to you.

like ayoli you mean ;)

---

### Post by ayoli on 2006-09-01
@alecjw: 
btw renember that allowing an user to do everything can be a security hole, can delete thing you dont want to be delete like nodes in /dev (seen in another thread).

---

### Post by Ramses de Norre on 2006-09-03
> **ayoli said:**
> like ayoli you mean ;)

Ow, yes, I corrected it =)

---

