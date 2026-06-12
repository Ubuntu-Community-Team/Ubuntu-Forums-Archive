---
title: "Script password question"
date: 2009-03-31
forum: General Help
---

### Post by kooldino on 2009-03-31
I recently wrote a script to backup a database.  One of the lines in the script is the following:

mysqldump -u wikiuser -p**MYPASSWORD** wikidb > $this_backup_file

I'd like to be able to somehow hide MYPASSWORD and possibly pull it in from a secured file somehow.  Is this possible?  If so, how?

---

### Post by kooldino on 2009-04-02
bump

---

### Post by unutbu on 2009-04-02
Are you running this script as root or as a normal user?

Are you running this command on a machine that you have physical contact with? or is it a remote server? 

Are there many users simultaneously using this machine?

Are you sure you need/want mysqldump? An alternative might be to copy /var/lib/mysql/DATABASE... If you simply backup the directory, then you don't have to reveal the mysql password. You will need to be able to run commands as root or at least the mysql user however.

---

### Post by kooldino on 2009-04-02
> **unutbu said:**
> Are you running this script as root or as a normal user?

A normal user.

> Are you running this command on a machine that you have physical contact with? or is it a remote server? 

I could do it on both, but it's actually running via a cron job.

> Are there many users simultaneously using this machine?

Yes, via http and smb.

> Are you sure you need/want mysqldump? An alternative might be to copy /var/lib/mysql/DATABASE... If you simply backup the directory, then you don't have to reveal the mysql password. You will need to be able to run commands as root or at least the mysql user however.

I don't need mysqldump persay, but I want to be able to completely back up the db.

---

### Post by unutbu on 2009-04-02
Perhaps try
```

sudo rsync -a /var/lib/mysql/wikidb/ /path/to/backup/wikidb/
```

To restore from backup:
```

sudo rsync -a /path/to/backup/wikidb/ /var/lib/mysql/wikidb/ 
```

---

### Post by kooldino on 2009-04-02
That would pose the problem of having to have the password entered somehow, since this is being executed by the crontab.

---

### Post by unutbu on 2009-04-02
If you put the command in /etc/crontab, then cron can run the command as root:

```

27   9     * 	 *   7   root rsync -aq --delete /var/lib/mysql/wikidb/ /path/to/backup/wikidb/
```
This crontab entry would run the rsync command every Sunday at 9:27am.

---

### Post by kooldino on 2009-04-02
So wait...if I write "root" in that one column, I can run any command as root, and it won't require a password? if that's the case, then I can just take my original script and set it so that only root can see it.

---

### Post by unutbu on 2009-04-02
Oops! I hadn't thought of that. :oops: 
I think your idea should work just fine.

---

### Post by kooldino on 2009-04-09
Tested.  Works like a champ.

---

