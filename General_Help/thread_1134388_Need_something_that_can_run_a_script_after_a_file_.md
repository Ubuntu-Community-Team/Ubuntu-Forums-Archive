---
title: "Need something that can run a script after a file upload"
date: 2009-04-23
forum: General Help
---

### Post by bmturney on 2009-04-23
I have an FTP server that users log in to and uploads files periodically.  What I would like to do is have something that monitors a directory for new files and when it finds a new file in the directory it will kick off a script to process the file.

I'm currently using cron jobs that are set to start up at a certain time, and run the script to process the files, however, a file could set there for several hours before the cron job is schedule to kick off.  I would like to be able to process these files as soon as they come in.

Any ideas/suggestions?

---

### Post by bmturney on 2009-04-23
I guess I should have checked another post I had before posting again... 

Someone suggested fsniper... after a quick look, that looks like exactly what I was looking for.

---

### Post by KyleBrandt on 2009-04-24
I think you probably want inotify / incron .  The thing you want to keep in mind is that you don't want to act on the file until it is done uploading, I think inotify and incron will support this.

-Kyle

---

### Post by bmturney on 2009-04-24
Thanks Kyle.. i'll check that out...

---

