---
title: "sshfs or rsync with subversion (svn)"
date: 2009-01-07
forum: General Help
---

### Post by willd819 on 2009-01-07
Hello everyone. this is my first post on ubuntu forums; just wanted to say hi, and ask my first question...

So, i'm working on a project that requires me to check out files from subversion on my web server - the web server is on my LAN. I've done that by mapping a folder on my local machine usings sshfs, the only problem is the I cannot check out the subversion files into that folder mapped with sshfs.. I am, however, able to create folders and files, and edit those files without problem within that sshfs mapped folder, so I'm pretty sure that it's set up at least somewhat correctly.

I've tried checking out the files from svn to my local machine and dropping them onto the server using my sshfs mapped folder, but when I do that I'm unable to do svn update on the file, even though it says it completed successfully - no existing files update, only new ones (if they are in the repository) come in.

I'm sort of stumped on what the issue is here,... I've been searching around and reading a little bit about rsync.  I'm wondering if there's a way i can use rsync and/or sshfs to do what I need to do, which is: work on files locally on my laptop and have them copy to my web server when i save them - whether this is an sshfs mapped folder or something that uses rsync and copies files over every times I save - either one would be great.

If anyone can help I'd be greatly appreciative!  I hope my question was clear enough, please let me know if I need to provide more information!

Thanks!:)

---

### Post by willd819 on 2009-01-07
bumpage

---

