---
title: "gPodder, permission problem?"
date: 2006-04-19
forum: Desktop Environments
---

### Post by jipke on 2006-04-19
I've just compiled gPodder v0.7 from source. 
It won't let me add channels unless I run 'gksudo gpodder' instead of just 'gpodder'.

This is the output I get in a terminal:
```

jipke@ubuntu:~$ gpodder
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/gpodder/gpodder.py", line 436, in on_it emAddChannel_activate
    self.add_new_channel( result)
  File "/usr/lib/python2.4/site-packages/gpodder/gpodder.py", line 323, in add_n ew_channel
    self.refetch_channel_list()
  File "/usr/lib/python2.4/site-packages/gpodder/gpodder.py", line 302, in refet ch_channel_list
    gPodderChannelWriter().write( self.channels)
  File "/usr/lib/python2.4/site-packages/gpodder/libgpodder.py", line 291, in wr ite
    fd = open( filename, "w")
IOError: [Errno 13] Permission denied: '/home/jipke/.config/gpodder/channels.xml'

```

It is a permission problem? Do I need to 'chmod' something? 
Who can help me out?

Thanks in advance!

---

### Post by jipke on 2006-04-19
Answered my own question.
I had to change permission for the directory (and it's contents) using this command:

$ sudo chmod -R o+rwx .config

Now everything works like it should.
BTW, there is also a .deb package for Ubuntu, missed that :)

---

