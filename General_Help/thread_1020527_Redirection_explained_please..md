---
title: "Redirection explained please."
date: 2008-12-24
forum: General Help
---

### Post by Barriehie on 2008-12-24
Hello Everyone,  I've recently had an issue with my backups running automatically and a suggestion was made that worked; however I don't understand it. :confused:  Can someone please explain what/where the numeric 1 and 2 are/do???

Thank You,
Barrie

```
0 4 * * 0 root /backmeup.sh 1>/home/barrie/Desktop/_cron.debug.1.log 2>/home/barrie/Desktop/_cron.debug.2.log
```

---

### Post by alecava on 2008-12-24
0 4 * * 0 root /backmeup.sh 1>/home/barrie/Desktop/_cron.debug.1.log 2>/home/barrie/Desktop/_cron.debug.2.log

When you execute a command it may produce an output, in the bash (...in the linux kernel api...) there are two output channels, the standard output (stdout) and the standard error (stderr), the stdout have the file descriptor 1, the stderr have the file descriptor 2 ( [http://en.wikipedia.org/wiki/File_descriptor](http://en.wikipedia.org/wiki/File_descriptor) ), so the output of your script will be splitted in two file, /home/barrie/Desktop/_cron.debug.1.log takes the output and /home/barrie/Desktop/_cron.debug.2.log takes the error messages because the ">" operator redirect the output to a file and if preceded by a number X redirect the output that will go to the X file descriptor

---

### Post by Barriehie on 2008-12-24
Thank you alecava!  That was exactly what I needed. :guitar:

Barrie

---

