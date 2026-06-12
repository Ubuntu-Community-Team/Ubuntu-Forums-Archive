---
title: "Backup over Network"
date: 2006-04-02
forum: Desktop Environments
---

### Post by IndigoMontoya on 2006-04-02
Hi.  I am looking for a way to backup my system over the network.  I have found a bunch of ways to do this which involve tar-ing the root directory (leaveing out a few choice places) and then sending the file someplace, but my hard drive is about 85% full and I don't think that option will work.  

Is there a way to pipe the output to another computer, or some other way to get around having the huge file on the harddrive I am backing up?  It is a laptop, so adding an extra harddrive is not really an option.  

Creative ideas always fun ;)


Thanks a bunch!
Scott

---

### Post by Azrael on 2006-04-02
Have a look at *rsync* (or a derivative thereof).

---

### Post by GeneralZod on 2006-04-02
I'm just going to go ahead and post this, if only because it was digg'd just today and I have a short memory :)

[http://metashell.blogspot.com/2006/03/how-to-backup-your-linux-system-using.html](http://metashell.blogspot.com/2006/03/how-to-backup-your-linux-system-using.html)

There are more elegant ways, though, especially if you have sshd set up on the target computer - something like (note - completely untested!) :

```

cd **<root directory of files to backup>**
tar -cjf - * | ssh **<targetcomputer>** "tee > **<dest backup file on target computer, .tar.bz2>**"

```

should do the trick - it says (roughly!) "take the contents of the current directory and (recursively) add to a .tar.bz2 file, except instead of an actual file we'll use stdout instead.  Meanwhile, on the target machine, take the input from stdin and pour it into a file.  Connect the stdout from the tar'ing operation on the source machine to the stdin on the target machine".

---

### Post by steffen on 2006-05-14
Simple Backup is a Google Sponsored (summer of code 2005) Ubuntu project for doing backups from your desktop to a local folder or over network. I have tried to set it to run backups over SSH or FTP, but I can't get it to work - getting error "The selected directory is not writable with current permissions" every time. I have tried from different computers.

If this was working, Simple Backup would be the perfect piece of backup software. It's incredibly simple and easy to use, as opposed to the myriad of enterprise grade backup software that exists out there, which wouldn't really suit desktop users.

If anyone has had success with Simple Backup for using over network, please let me know!

[http://sbackup.sourceforge.net/HomePage](http://sbackup.sourceforge.net/HomePage)

Edit: See bug report [http://sourceforge.net/tracker/index.php?func=detail&aid=1416276&group_id=145360&atid=761640](http://sourceforge.net/tracker/index.php?func=detail&aid=1416276&group_id=145360&atid=761640)

---

### Post by reubano on 2006-10-17
> **steffen said:**
> I have tried to set it to run backups over SSH or FTP, but I can't get it to work - getting error "The selected directory is not writable with current permissions" every time. I have tried from different computers.


Same problem here whenever I clicked on "test location". I have private keys and ssh agent enabled so that I could do passwordless backup. In the default backup location configuration, the prompt was 

ssh://username:<password>@server.example.com/remote/directory/

and I tried 

ssh://username@IPaddress/remote/directory/ since I wasn't sure of the security implications of including my password. After some searching, I found this site which is related but doesn't address this specific problem.

[http://sbackup.sourceforge.net/ProblemsAndWorkarounds](http://sbackup.sourceforge.net/ProblemsAndWorkarounds)

has neone else gotten this to work? What about any other programs that will allow passwordless ssh backups? I would really hate to have to write a script to rsync over ssh.

---

