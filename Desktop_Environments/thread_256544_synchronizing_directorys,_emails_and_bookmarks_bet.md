---
title: "synchronizing directorys, emails and bookmarks between machines"
date: 2006-09-13
forum: Desktop Environments
---

### Post by canardo on 2006-09-13
Hi my current set up is this, they all have access on the same lan

main pc Ubuntu
laptop Ubuntu

works pc Windows


Id really like to be able to share my emails(thunderbird), bookmarks(firefox) and a work directory between the three so that when I connected a machine to the lan the other two were synchronized with the newest data.

I am sure I wont be the only person that wants to do this!

For email is it worth setting up postfix to run an IMAP server on my main pc and connect everything to that?

Had a quick look at ifolder and looks as though it will do what I require just wondering if there is any other options, before I go down this route

Thanks in advance

---

### Post by wieman01 on 2006-09-13
I know a solution for Linux PCs called "Unison" (I am using it):

[http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html]("http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html")

It is a Unix/Linux tool, however, it connects to other computers via SSH. So I am sure that you could use on the Linux machines to synchronize with a Windows system on which you install a SSH server.

Unison needs to be install only on 1 client, the rest is done by means of SSH. Great tool! I use it for my bookmarks, personal files, emails, you name it. And it's fairly easy to configure and well documented.

---

### Post by canardo on 2006-09-13
thanks will give it a go tomorrow

---

