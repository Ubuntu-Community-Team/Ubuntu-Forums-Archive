---
title: "Sharing on ubuntu"
date: 2009-05-29
forum: General Help
---

### Post by disappearedng on 2009-05-29
Hey everyone,
Not sure which category does this thread belong to, so I will just list it here anyway. 

I want to collaborate a project with my friend. We have decided to use my computer to host code and data and he will mainly be using ssh to come to my computer to do some work.

1) I have a directory that has everything which we share. This include a git repository, some raw data files and some scripts

2) What is the best scenario for this? We are having a lot of trouble with file permissions: he belongs to a group b and I have added myself to that group. However, when I am on that directory, files that I create still belong to my default group rather than our group. What is the most convenient way around this?

3) Does linux have some mechanism for this sort of sharing: only ppl from our group can create, delete and update folders from this directory, and is there a way to exhibit different default behaviours when I am in that directory only( like I have to do a umask 002 before creating, deleting) is there a more convenient way around this problem?

4) When I am in my default account, files that I create cannot be commited to the git repository with much ease due to some permission issue. I have to login to his account then do a git commit which is kind of troublesome then when I am done writing new files I have to do a chown and chmod. What's the expert's solution to this?

Any suggestions are recommended. We are looking for ways to solve this.

---

