---
title: "FTP to Desktop Scheduled Transfer"
date: 2009-04-01
forum: General Help
---

### Post by dlebowski on 2009-04-01
Hi.  I am having a hard time finding a program that I can schedule to run at certain times during the week to copy files down from my web server to my local machine.  I basically want to schedule backups to copy database files and website directories to my local machine.  I use Filezilla for my FTP client, but I'm not aware of a way to automate it.  Any help would be great.  Thanks.

-Ryan

---

### Post by studout on 2009-04-01
The console program "wget" will get both HTTP and FTP files for you.  It will also allow you to specify a username and password if necessary.

You can type "man wget" in a console/shell window and get the full manual page, but I think the option that is most relevant for you if you need a password is "--user=user", and "--password=password".

If you need a more cut-and-paste solution (for backgrounding and scheduling), I would be happy to create that too... but if this is enough....   :)

-HTH

---

### Post by dlebowski on 2009-04-01
Thanks for you help.  I would need to automate it and I would want to only copy a certain directory or two to a specific location on my workstation.  Can you help me with that? Thanks again.

---

### Post by studout on 2009-04-01
Ok, so this is a website you run, have password protected ftp access to, and want to create a backup copy of it every so often by logging in with ftp, and downloading an entire directory[ tree], or directories.

If it is a specific set of files, that's easy, if it's just "grab this entire directory", that's slightly different.

Am I close, or totally wrong?

---

### Post by dlebowski on 2009-04-02
You are right on the money.  If I could download a whole directory, that would be fine.  I can just have my backups dump the files in the directory and then I would use this to copy the directory down.  Thanks again for taking the time to help me.

---

### Post by studout on 2009-04-02
I think this command will do the recursive downloading for you.

```
wget -m ftp://user:pass@domain:port/path/to/dir
```

The -m option turns on recursion and time-stamping, sets infinite recursion depth and keeps FTP directory listings.

How often/when do you want this to run?
I think you can probably use cron/crontab.

---

### Post by dlebowski on 2009-04-02
I need it to run nightly.  where do you specify where you want it to be copied to on the local machine?  Thanks again.

---

### Post by studout on 2009-04-02
open your favorite text editor and put this in it...

```
#!/bin/bash
cd /directory/where/you/want/the/backup
wget -a /path/to/logfile/to/save -m ftp://user:pass@domain:port/path/to/dir
```
Save that file into a suitable location.  My favorite is to make a dir named "bin" in my home directory.  So that would be /home/username/bin

Save the file as backupweb.sh or something like that.
You will need to make it executable.  If you're running in the gui, you can simply right click on it, select the permissions tab, and then check all of the checkboxes for executable.
Alternatively, if you're using the shell, which you will have to in a moment, you can simply type ```
chmod +x /home/username/bin/backupweb.sh
```

Open a shell and type ```
crontab -e
```
It should ask you what editor you would like to use.
If you have one that you use and like, go for it, but if not, select vi, and proceed.
When vi is displayed, you will see a line at the top of the shell window showing
```
# m h  dom mon dow   command
~
~
~
~
~
~
~
~
~
```

Press the lower case "o" character on the keyboard.
You will see the cursor move to the next line, and it will say
-- INSERT -- at the bottom.
On that second line, type this...
```
5 0 * * * /home/username/bin/backupweb.sh
```
Then press the escape key on the keyboard, the -- INSERT -- will go away, and then press colon key, and then "wq" then press Enter.

That command will make it run on the 5th minute after midnight, every day (well.. night).

---

