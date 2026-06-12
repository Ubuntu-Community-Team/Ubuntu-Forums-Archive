---
title: "rsync fails"
date: 2009-02-24
forum: General Help
---

### Post by poguemahone on 2009-02-24
I have a short shell script for backing up:

```
#!/bin/bash
EXCLUDEFILE=/media/backup/rsync_exclude.txt
SOURCE=/media/bigdog/
DEST=/media/backup/koolu/
rsync -v -rlt --human-readable --stats --delete --delete-excluded --exclude-from=$EXCLUDEFILE $SOURCE $DEST 
```

When the script is executed, it fails with the following error:

[INDENT]rsync: failed to open exclude file /media/backup/rsync_exclude.txt\#015: No such file or directory (2)
rsync error: error in file IO (code 11) at exclude.c(1062) [client=3.0.3][/INDENT]

Interestingly, I can execute the same thing in shell and it will work. It's only when I try to use rsync in a script that it fails.

Does anyone have any ideas? I think it has something to do with the "#015".

---

### Post by unutbu on 2009-02-24
Your script may have an invisible control character at the end of 
```

EXCLUDEFILE=/media/backup/rsync_exclude.txt

```

Perhaps open the script in a text editor, use backspace to delete
all the characters is red:

```
EXCLUDEFILE=/media/backup/rsync_exclude.t[COLOR="Red"]xt
SO[/COLOR]URCE=/media/bigdog/

```

and then re-type those characters.

I don't know if this will work, but perhaps it's worth a shot.

---

### Post by poguemahone on 2009-02-24
Good suggestion, but that doesn't seem to be the problem.

---

### Post by unutbu on 2009-02-24
Is the script being run through cron?
Is the script being run by you or by some other user? If it is some other user, perhaps it is a permission problem? Does that user have the permissions to read /media/backup/rsync_exclude.txt?

Perhaps delete these characters in the rsync command (marked in red) and retype them.
```

--exclude-from=$EXCLUDEFI[COLOR="Red"]LE $SO[/COLOR]URCE
```

---

### Post by poguemahone on 2009-02-24
Okay, I fixed it.  I actually just deleted the shell script and re-entered it in mousepad.  I'm wondering if it was some sort of text encoding problem. It's possible that I edited the script in notepad (windows) once before.

It's possible that [iconv]("http://www.cubiczone.com/Articles/tabid/65/EntryID/15/Default.aspx") could've been useful.

Thanks for the help.

---

