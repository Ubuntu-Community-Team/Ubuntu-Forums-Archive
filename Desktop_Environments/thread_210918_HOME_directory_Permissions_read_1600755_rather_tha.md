---
title: "HOME directory Permissions read 1600755 rather than 755 -- 7 digits rather than 3"
date: 2006-07-07
forum: Desktop Environments
---

### Post by computerease on 2006-07-07
This was originally posted as a Change UID question but it was not a UID problem.
I discovered approx two days after the original post how confused my question was. I had, indeed, changed my ID to the root ID and I did change it back only to discover the numbers at which I was looking were for a different purpose than the user ID.
I still have a problem. I ran the command sudo chmod 0644 ~/.dmrc and it did not impact my problem. Instead, I discovered it may be more extensive than originally thoughtl
It is as follows:  I will create a Table to expose the issue (Tables don't show well unfortunately so I'll spell it out carefully). I will be comparing three computers with Ubuntu and will call them Main, Back and Loft. Main is the computer with the problem:

File/Directory   Permissions
HOME Directory: Main = 1600755;  Back = 755;  Loft = 755
Filesystem Directory: Main = 1200755 Back = 755;  Loft = 755
.dmrc file:  Main = 1600775;  Back = 600;  Loft = file not present

When I ran the command: sudo chmod 0644 ~/.dmrc
I was asked for the password and then the command supposedly executed and I was returned to the prompt. However, the Permission number code remained as above: 1600755
Upon reboot the error message [User's $/HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's HOME directory must be owned by user and not writable by other users.] remained in place.

I have the following questions:

1. Why are the permissions on the Main machine in such total nonconformity to the what I understand to be the permissions grid?
I understand the permissions grid to be as follows:

Read:  Owner = 400;  Group = 40;  World (Others) = 4
Write:  Owner = 200;  Group = 20;  World = 2
Execute: Owner = 100;  Group = 10;  World = 1
None:  Owner = 0;  Group = 0;  World = 0

If this is the case, 777 should be the largest permission number that should appear and 000 the lowest. The computer known here as Main has a Permission number of 1600755. The chmod command did not touch that number.

2. This system began as a Breezy system and was updated through Synaptic to Dapper. Could that be the issue for the differences in Permission numbers and does Dapper have additional factors to consider not present with Breezy (or other flavors of Linux releases if my research serves me well)?

3. Could the fact that I've modified my system to allow for a Root login have had an impact on the presentation of the Permission numbers?

4. I HAD changed my UID from 1000 to the root number at one time but changed it back. Could that have diddled the system?

5. Am I seeing the symptoms of something other than simple user numbers and Permissions numbers here, such as a security breach of some type?

Thank you in advance for your time, consideration and patience.

---

### Post by hegenious on 2006-07-07
"4. I HAD changed my UID from 1000 to the root number at one time but changed it back. Could that have diddled the system?"

Possibly.
I think the system is confused about who owns or rather owned the file.
Did you try changing the ownership of the file?

(sudo chown user:group /home/<user>/.dmrc)

you can look up user and group in /etc/passwd.
and give the full path to .dmrc, to make sure the system is not confused about that either...

---

