---
title: "Fakeraid 0- almost there, help!"
date: 2006-06-13
forum: Desktop Environments
---

### Post by Anything Generic on 2006-06-13
I've followed this how-to for Fakeraid with success, substituting for xubuntu where required: [https://wiki.ubuntu.com/FakeRaidHowto]("https://wiki.ubuntu.com/FakeRaidHowto")


I can boot to Xubuntu, but when I login to my username 'eric', it tells me that I don't own the /home/eric directory and others, and says the session lasted less than 10 seconds and boots me out.

I'm assuming it has to do something with this instruction at the bottom of the above Raidraid how-to link:
> Suggested early set-up tasks: adduser yourself (create a regular user) nano /etc/group (create an admin group) visudo (duplicate the root line except with %admin where root was) reboot, and you should be able to log in a normal user through gdm, and continue normally with sudo privileges. 

I did the adduser eric
mkdir the /home/eric directory
and visudo adding the %admin line.

I don't have any idea how to create the admin group though.  Do I create an admin group, and put the user eric into it?  How do I do this?

Any other ideas to as why the eric account is still flawed?

Thanks for any help
-Eric

---

### Post by Anything Generic on 2006-06-13
bump, still stuck :(

---

### Post by Anything Generic on 2006-06-13
found a fix for those interested:


deluser eric
addgroup --system admin
adduser eric admin
(follow prompts)

---

### Post by scxtt on 2006-06-13
read the man page on 'addgroup' ...

who owns "/home/eric"?

if you sudo mkdir /home/eric it will be owned by root, which would then create the issue for "eric" when logging in ...

---

