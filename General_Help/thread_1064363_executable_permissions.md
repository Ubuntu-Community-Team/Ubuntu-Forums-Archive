---
title: "executable permissions"
date: 2009-02-08
forum: General Help
---

### Post by colsandurz on 2009-02-08
Hello I recently ran this program, KeepNote, as root.  Now, I have to run it as root to run it all.  I didn't have to run it as root before.  This is the error message I get.

```

$ keepnote
==============================================
KeepNote 0.5.1: Sun Feb  8 19:35:08 2009
Traceback (most recent call last):
  File "/usr/bin/keepnote", line 241, in <module>
    main(sys.argv)
  File "/usr/bin/keepnote", line 216, in main
    app = keepnote.KeepNote(basedir)
  File "/usr/lib/python2.5/site-packages/keepnote/__init__.py", line 652, in __init__
    self.pref.read()
  File "/usr/lib/python2.5/site-packages/keepnote/__init__.py", line 446, in read
    raise NoteBookError("Cannot read preferences", e)
NoteBookError: IOError(13, 'Permission denied')
Cannot read preferences

```

How can I fix this?

---

### Post by x33a on 2009-02-08
post the output of ls -l for /usr/bin/keepnote.

---

### Post by colsandurz on 2009-02-08
Ah.. that got it.  That somehow changed the owner to root, when it should have been my user name.  Weird.

---

### Post by x33a on 2009-02-08
you mean ls -l changed the permissions? 

well, anyway the problem got solved :D.

---

### Post by colsandurz on 2009-02-08
Actually it didn't! I actually tried running the program and it didn't work.  I think I have to try to change the permissions of some preference file or something.

---

### Post by x33a on 2009-02-09
well try doing "chmod 755 filename"

---

### Post by colsandurz on 2009-02-09
hrm 
```
ls -l /usr/bin/keepnote
-rwxr-xr-x 1 devin devin 6291 2009-01-25 19:56 /usr/bin/keepnote

```

I think it's trying to access something else it doesn't have permission to.

Also, thanks for the help.

---

### Post by x33a on 2009-02-09
ok, let's have a last go at it.

try "lsof -p pid" where pid = process id of keepnote. you can find pid with the "ps -e" or "top" command.

lsof will list all the files opened by keepnote, and you can use this information to debug your problem.

Note: This won't work if keepnote doesn't open at all, or crashes immediately. if it remains in a hung state, it might work.

And, if this doesn't work or is too much for you, try re-installing keepnote, and hope it works :D

---

### Post by rasmusmit on 2009-02-10
well this is random.  I am the author of keepnote and I just found this post.  This sounds like you have the wrong permission and/or ownership of preference files (because you ran as root, which you should avoid). 

The preference files of keepnote are stored at

~/.config/takenote
and
~/.local/share/takenote

note: the directories are called takenote (older name) not keepnote.

As ROOT (because only root can change their files ownership) run these commands to get the ownership corrected again:

```

sudo chown -R USER_NAME.USER_NAME ~/.config/takenote/
sudo chown -R USER_NAME.USER_NAME ~/.local/share/takenote/

```

where USER_NAME is your username.  Remove the beginning sudo command if your setup doesn't use it.

Hope this helps.

---

### Post by colsandurz on 2009-02-10
ahh that did it.  Thanks.  Is it supposed to change the owner of those files when you run keepnote as root?  Also, thanks for writing keepnote.  I find it pretty useful.

---

### Post by rasmusmit on 2009-02-10
good to hear.  I believe KeepNote would only create files with root ownership if you ran keepnote as root the first time after you installed it.  After the first execution, all the preference files it needs will already be created and shouldn't change owner if you ran as root.  For more documentation see [http://rasm.ods.org/keepnote/manual.shtml](http://rasm.ods.org/keepnote/manual.shtml)

---

