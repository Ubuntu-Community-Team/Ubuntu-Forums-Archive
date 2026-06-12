---
title: "$HOME/.drmc problem on log-in"
date: 2006-01-24
forum: Desktop Environments
---

### Post by Luke771 on 2006-01-24
Hi, here I go again:
This time I must have done something wrong but I dont'know what; the problem is that when I get to the log-in screen, type in "root" and and the root password, (I have enabled root logging so I skip typing in the user password all the time).
After hitting Enter, a warning pops up, saying: 
> "your Home/.drmc file has [something like "faulty" or "wrong"] permissions and is being ignored.
"Should be owned by user and have 644 permissions."
I click OK and everithing works fine, so I guess I could just ignore that, but I'm not that kind of guy: I want to know what happened and I don't want to see any annoyng warning messages when I log in.
So, I went to the Home directory and checked that file; it was owned by root and it had read and write permission fot root only, the sum was something else than 644; so I changed the permissions setting them to read and write for root and read only for user and group, and the sum was exactly 644.
I logged out and in again, but the problem persisted:>  Your $Home/.drmc file... [blah blah blah] ...is being ignored ... [blah blah bla blah] ... 644 permissions.
Maybe it was some other file; I went to the main user's (not root)  /home/username directory and found a similar file; changed the permissions to 644 with not much of a hope and as I guessed, the problem was still there.
Now I've tried the little I could, I tried to google it but I didn't get any answer, I'm going to try googling a little more and browse some other forums as well, just in case, but in the meantime, if someone can post here the solution and possibly some kind of explanation I would really appreciate it.
Thanks.

---

### Post by linuxden on 2006-01-24
[http://www.ubuntuforums.org/showthread.php?p=479186#post479186](http://www.ubuntuforums.org/showthread.php?p=479186#post479186)

Been fixed here .. 

Hope that helps...

---

