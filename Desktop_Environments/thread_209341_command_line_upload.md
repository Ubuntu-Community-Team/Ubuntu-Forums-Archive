---
title: "command line upload"
date: 2006-07-05
forum: Desktop Environments
---

### Post by evaristegalois on 2006-07-05
I am always interested in doing things from the command line, partially because I like to schedule tasks using cron. Question: how do I upload a file with a single command from the command line? wget will do the trick for a download, but ftp expects a dialogue which is difficult to automatize. The command would need username and password of the remote site as options, such as (this is fictional)

wput file.name remote.site -u "username" -p "password"

to put the file file.name on the remote site remote.site.

Is there a command that can do this?

--evaristegalois

---

### Post by dmizer on 2006-07-05
probably not exactly what you're looking for, but it does work like you describe ... by using ssh:
[http://easylinux.info/wiki/Ubuntu#How_to_copy_files.2Ffolders_from_local_machine_into_remote_Ubuntu_machine_.28scp.29](http://easylinux.info/wiki/Ubuntu#How_to_copy_files.2Ffolders_from_local_machine_into_remote_Ubuntu_machine_.28scp.29)

this is of course depending on an existing ssh server being active on the remote machine.

---

### Post by atoponce on 2006-07-05
[quote=evaristegalois]I am always interested in doing things from the command line, partially because I like to schedule tasks using cron. Question: how do I upload a file with a single command from the command line? wget will do the trick for a download, but ftp expects a dialogue which is difficult to automatize. The command would need username and password of the remote site as options, such as (this is fictional)

wput file.name remote.site -u "username" -p "password"

to put the file file.name on the remote site remote.site.

Is there a command that can do this?

--evaristegalois[/quote]
Are you using FTP or SSH?  For FTP, there is already a built in command called 'PUT'.  For example, if I were to upload index.html to an FTP site, it would be as follows:
```

~$ ftp user@ftp.somesite.org
Password:

ftp> put index.html
```

If using SSH, then SCP (secure copy) would be used.  You will need to know the directory structure before uploading, and the contents of the directory that you are uploading to making sure that you don't overwrite the file.  It would be as follows:

```
~$ scp index.html user@somesite.org:/home/user
Password:
```

Naturally, make sure that you know the ports as well.  Both will work just fine.

---

### Post by evaristegalois on 2006-07-07
My problem is with the password. I want to schedule a weekly upload from a computer with cron so that I am not actually there to provide the password. Can I add the password as an option? Other than that, scp seems to be exactly what I am looking for.

--evaristegalois

---

### Post by evaristegalois on 2006-07-25
found a great program to do exactly what I want it to do and easy to install:

ncftpput

--evaristegalois

---

### Post by stashj on 2006-08-02
I know you have this sorted now but just to let you know that there is a wput command. You can install it with Synaptic by allowing community repositories. The syntax is wput <filename> ftp://username:password@<remote file address>
Seems simple enough but I am at a loss with it so I think I might try your program now. I keep getting a segmentation fault with wput. :-(

---

### Post by Skerit on 2007-07-25
So I've jsut had my second break-in in 22 days, I tried to install motion & wput last time, but it failed *miserably* and I thought "what the hell? What are the chanes!?"

So here I am ... Euhm, my wput is giving me some nasty error I have no idea how to fix!

It simply says "SIZE (FILENAME.JPG) ... FAILED!"
followed by:

Setting data protection level to private ... PROT P failed.

So, can anyone comment?

---

### Post by evaristegalois on 2007-07-28
try ncftpput

---

### Post by ionhs on 2008-05-08
I have another question about wput. Which is the correct syntax for the wput command.
I need to move a big file from one linux machine to a windows pc.
I write this syntax in the window´s putty:

wput filename [ftp://username:pass@pcIP](ftp://username:pass@pcIP)

but the answer is:
=> [ftp://username:xxxxx@192.168.1.2:21/filename](ftp://username:xxxxx@192.168.1.2:21/filename)
Connecting to 192.168.1.2:21... connected!
Logging in as ion ... Logged in!

later
Send Failed. Waiting 10 seconds...Send Failed. Waiting 10 seconds... 

and it repeats
I dont understand what I do bad, anybody can help me please?

---

### Post by Monicker on 2008-05-08
Perhaps you need to specify a subdirectory.  FTP sites do not always put you in a writeable directory when you first connect.

---

### Post by ionhs on 2008-05-09
Monicker, I have writen one directory, but the answer is the same. Now in the pc has created a directory but no file.

wput filename [ftp://username:pass@IP:Port/](ftp://username:pass@IP:Port/)**directory**/

I have written this one too with the same answer.

wput /home/user/directory/filename/ [ftp://username:pass@IP:Port](ftp://username:pass@IP:Port)

another idea please, I am lost. thank´s

---

