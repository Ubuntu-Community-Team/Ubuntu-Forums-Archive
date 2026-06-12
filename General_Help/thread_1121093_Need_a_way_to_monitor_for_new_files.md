---
title: "Need a way to monitor for new files"
date: 2009-04-09
forum: General Help
---

### Post by bmturney on 2009-04-09
I am running an FTP server on Ubuntu and I need a way that I can monitor for a file being added to a folder and as soon as it is added have the system fire off a script.  

Currently I have a cron job that kicks off periodically checking for new files, but I was hoping to find something that could possibly be a little more immediate... so that just as soon as the user's upload completes my script will kick off to process the file.

Any ideas???

---

### Post by Wayne_V on 2009-04-09
Don't know of anything that would fire off a shell script directly but you could write a small program to interface to gamin to do that:

[http://www.gnome.org/~veillard/gamin/](http://www.gnome.org/~veillard/gamin/)

---

### Post by VCoolio on 2009-04-09
Maybe [fsniper]("http://www.linux.com/feature/150200") can help you. Good luck.

---

