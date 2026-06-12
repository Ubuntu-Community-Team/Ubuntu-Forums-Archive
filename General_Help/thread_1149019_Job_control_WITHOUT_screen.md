---
title: "Job control WITHOUT screen"
date: 2009-05-04
forum: General Help
---

### Post by cvp on 2009-05-04
I need to run a whole mess of jobs that will each take up to several days to run, but the machine I'm being asked to run it on inexplicably does not have **screen** installed.
I don't know why someone would do a linux install on what is intended to be a supercomputer whose only purpose is to run ungodly amounts of resource-hogging processes, but neglect to install screen, but hey, it's a new machine. I wrote an email to the sysadmin, but in the meantime I have to try work with what I have.

I *can* just leave my laptop at work and logged in, and running something to keep the connection active so that I'm not dropped, but that would be very annoying.

I've spent a good amount of time Googling the issue. Most of the results I got had no mention of resuming a process from a new terminal (which is what I'd very, very much like to do), and the rest simply conclude as expected with "just use screen!" "Wow, that worked brilliantly! I <3 screen! ^_^". There was one that simply said it wasn't possible without screen, and I'm hoping that's not true, even if there's a really ugly, hacky way.

So... *without* using screen, is there a way to fork a process to the background, (probably using **nohup** since I plan to:) log out, log back in later, and bring that process back to the foreground even though I started it in a different session?

---

