---
title: "trying to install dtv, help pls..."
date: 2006-02-28
forum: Desktop Environments
---

### Post by dude of wonders on 2006-02-28
i tried the new to linux forum, but no answers so figured i'd try here.;) 

go here to see how i installed it.

[https://develop.participatoryculture.org/projects/dtv/wiki/GTKX11BuildDocs](https://develop.participatoryculture.org/projects/dtv/wiki/GTKX11BuildDocs)


```
cd tv/platform/gtk-x11 
./test.sh
```

when i typed in that i get this in my terminal



```

sh: /usr/lib/mozilla/mozilla-config: No such file or directory
sh: /usr/lib/mozilla/mozilla-config: No such file or directory
/usr/lib/python2.4/distutils/dist.py:236: UserWarning: Unknown distribution option: 'console'
  warnings.warn(msg)
running install
running build
running build_ext
building 'fasttypes' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O3 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.4 -c /home/lionheart/tv/portable/fasttypes.cpp -o build/temp.linux-i686-2.4/home/lionheart/tv/portable/fasttypes.o
unable to execute gcc: No such file or directory
error: command 'gcc' failed with exit status 1
Traceback (most recent call last):
  File "DTV.py", line 14, in ?
    import app
  File "/home/lionheart/tv/platform/gtk-x11/../../portable/app.py", line 2, in ?    import feed
  File "/home/lionheart/tv/platform/gtk-x11/../../portable/feed.py", line 1, in ?
    from downloader import grabURL
  File "/home/lionheart/tv/platform/gtk-x11/../../portable/downloader.py", line 1, in ?
    from database import DDBObject, defaultDatabase
ImportError: No module named database

```


any ideas what i need to do??

---

