---
title: "Maintaining permissions in a directory"
date: 2009-03-02
forum: General Help
---

### Post by personwholives on 2009-03-02
So, I have a linux box with basically a dropbox, where newly downloaded files are moved when they are finished by multiple users/accounts.  As such, I want it to keep permissions where anybody can delete the files out when they are done and have moved them.  I think I need a way to a) change the group of all files moved into this directory, including new directories, so they belong to the users group, and b) enforce that all files here will have g+w.  I could do this by adding a cronjob for running "chown :users /.../pickup && chmod -R g+w /.../pickup" every hour, but I would rather do it another way if possible.  Or tell me I'm dumb and doing this the hard way, but if you do that, you have to tell me the easy way while you're at it.

Thanks in advance for the advice,
personwholives

p.s. I tried google, and found very little of help.  I tried searching here, but may have just crafted a bad search, and so found little of help.

---

### Post by bodhi.zazen on 2009-03-02
for what you are asking a cron job makes the most sense.

Yea, it is not ideal but ...

The only other option would to modify each user such that their primary group is users. Then set their umask value in .bashrc (to 117).

You could *ask* the users to do this manually, ie make the changes themselves, good luck with that one :)

---

### Post by unutbu on 2009-03-02
For each user who you would like to be able to write to /.../pickup, run the command
```

sudo usermod -a -G users USERNAME
```

This will add USERNAME to the users group.
```

sudo chmod g+w /.../pickup 
sudo chown root:users /.../pickup 
```

An now for the magic:```

sudo chmod g+s /.../pickup 
```

Adding the setgid bit causes all files created in /.../pickup to have the same gid as the parent directory. Thus, all files created in /.../pickup should have gid=users.

Each user which is a member of the users group will be able to write (and delete) files in /.../pickup.

---

### Post by personwholives on 2009-03-02
> **unutbu said:**
> 
An now for the magic:```

sudo chmod g+s /.../pickup 
```

Adding the sticky bit causes all files created in /.../pickup to have the same gid as the parent directory. Thus, all files created in /.../pickup should have gid=users.

Each user which is a member of the users group will be able to write (and delete) files in /.../pickup.

Yeah, I figured that one out, but what about if another directory is placed there, with the wrong group set.  That works fine for /.../pickup/*, but not /.../pickup/foo/*.  You have to change the permissions of the new directory to add g+ws for that to work there, too.

---

### Post by Slim Odds on 2009-03-02
> **unutbu said:**
> An now for the magic:```

sudo chmod g+s /.../pickup 
```Adding the sticky bit causes all files created in /.../pickup to have the same gid as the parent directory. Thus, all files created in /.../pickup should have gid=users.

Isn't "+s" the setuid bit?

I think that "+t" is the sticky bit....

[http://en.wikipedia.org/wiki/Sticky_bit](http://en.wikipedia.org/wiki/Sticky_bit)

---

### Post by trwww on 2009-03-02
> **unutbu said:**
> 

An now for the magic:```

sudo chmod g+s /.../pickup 
```


The users have to have a compatible umask also, or directories and files won't be editable by others in the group.

I use 0002.

---

### Post by unutbu on 2009-03-05
pyinotify is a python wrapper around inotify, a Linux kernel feature would 
makes it possible for applications to be notified of filesystem changes.

Below is a little script which can be used to monitor /.../pickup.
Whenever a new file or directory is made in /.../pickup or any of its subdirectories,
"chown -R root:users /.../pickup/" will be run.

To use the script, save it as chown_pickup.py:
[php]#!/usr/bin/env python
import sys
from pyinotify import WatchManager, Notifier, EventsCodes, ProcessEvent
from subprocess import Popen,PIPE

class MyProcessEvent(ProcessEvent):
    def __init__(self,root_dir):
        self._root_dir=root_dir
    def process_IN_CREATE(self, event):       
        cmd='chown -R root:users %s'%self._root_dir
        proc=Popen(cmd, shell=True, stdout=PIPE, )
        proc.communicate()

if __name__=='__main__':
    try:
        path = sys.argv[1]
        if not path.endswith('/'):
            path=path+'/'
    except IndexError:
        print 'use: %s dir' % sys.argv[0]    
    wm = WatchManager()
    mask = EventsCodes.IN_CREATE
    notifier = Notifier(wm, MyProcessEvent(path))
    wdd = wm.add_watch(path, mask, rec=True, auto_add=True)
    while True:  
        try:
            notifier.process_events()
            if notifier.check_events():
                notifier.read_events()
        except KeyboardInterrupt:
            notifier.stop()
            break
[/php]

Make it executable, and put it in your path.
Install the python-pyinotify package (about 30kB in size).

Run it as root:

```
sudo chown_pickup.py /.../pickup
```

---

