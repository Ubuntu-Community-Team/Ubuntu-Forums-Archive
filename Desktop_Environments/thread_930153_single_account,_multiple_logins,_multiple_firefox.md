---
title: "single account, multiple logins, multiple firefox?"
date: 2008-09-25
forum: Desktop Environments
---

### Post by xris_xcess on 2008-09-25
Hi:

I've currently setup a diskless client network. Several Hardy clients boot off one server and have their /home folders on there thru NFS.

For the moment, I have ONE account for people to use, kind of a guest account. So I get multiple logins for the same user at any one time. It has worked relatively fine... except for firefox.

I have searched everywhere for a way to run multiple instances of firefox with one profile, but it is not possible/allowed (according to Mozilla docs).

However, it is possible to run multiple instances of firefox with -different- profiles, so that although there are several "user1" users logged on, each uses "user1.profile", "user2.profile"..etc.

I have tried to automate this, since I don't want the users noticing the fact of different profiles, using the hostname ($HOSTNAME) from each machine as a profile name and starting firefox with the "-p profile" option.

I kind of have all the pieces but I'm having difficulty putting them together. Any ideas, scripts, hints, how-to's are exceptionally welcome.

Thanks.

---

### Post by xris_xcess on 2008-09-29
Well, although I found a solution, I didn't actually solve the problem.

I ended up installing the Epiphany web browser. It seems to use a traditional preferences file, instead of the profile system preferred by Firefox. Anyhow, I tried it and it will allow the same user, logged in from different machines to use a web browser (firefox will not).

I'm still working on the root problem thou, which is to adapt/script/hack Firefox to select/create a different profile based on the hostname/location of the machine that is being used.

---

### Post by Murz on 2012-10-02
Hello! Did you find any solution for this problem?
I have diskless computers too, and if user is not close session on one computer, it can't use firefox on other.

---

### Post by overdrank on 2012-10-02
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

