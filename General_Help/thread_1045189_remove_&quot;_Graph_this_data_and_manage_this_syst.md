---
title: "remove &quot; Graph this data and manage this system&quot;"
date: 2009-01-20
forum: General Help
---

### Post by monkeyking on 2009-01-20
The new version of ubuntu is plastered with an annoying advertisement that looks like

```


  System information as of Tue Jan 20 13:30:01 CET 2009

  System load: 0.32                Memory usage: 40%   Processes:       150
  Usage of /:  36.3% of 226.36GB   Swap usage:   0%    Users logged in: 1

  Graph this data and manage this system at https://landscape.canonical.com/


```


Does anyone know how to customize this message

thanks

---

### Post by schilcha on 2009-01-20
This message (Message Of The Day) is stored in /etc/motd. "man motd.tail" will tell you (amongst other things) that this is just a symlink to the (regularily updated) file /var/run/motd. 

If you want to disable this message completely, create an empty file like /etc/motd.static and make sure that the link /etc/motd points to this empty file.

In short:
```
cd /etc
sudo touch motd.static
sudo ln -sf motd.static motd
```

Good luck,
   schilcha

---

### Post by monkeyking on 2009-01-21
Thanks!
Quite helpfull,
but this tells me how to get rid of everything.
How do I get rid of only the last 3 lines of the motd.

---

### Post by monkeyking on 2009-01-21
a quick
```
locate landscape | xargs grep Graph
/usr/lib/python2.5/site-packages/landscape/sysinfo/landscapelink.py:            "Graph this data and manage this system at "
Binary file /usr/lib/python2.5/site-packages/landscape/sysinfo/landscapelink.pyc matches

```
So I gues I can just change this file.

againthanks for your reply.

---

### Post by monkeyking on 2009-01-21
Btw maybe I should elaborate futher
the file /usr/lib/python2.5/site-packages/landscape/sysinfo/landscapelink.py
looks like
```

cat /usr/lib/python2.5/site-packages/landscape/sysinfo/landscapelink.py
from twisted.internet.defer import succeed


class LandscapeLink(object):

    def register(self, sysinfo):
        self._sysinfo = sysinfo

    def run(self):
        self._sysinfo.add_footnote(
            "Graph this data and manage this system at "
            "https://landscape.canonical.com/")
        return succeed(None)


```
change this to
```

cat /usr/lib/python2.5/site-packages/landscape/sysinfo/landscapelink.py
from twisted.internet.defer import succeed


class LandscapeLink(object):

    def register(self, sysinfo):
        self._sysinfo = sysinfo

    def run(self):
#        self._sysinfo.add_footnote(
#            "Graph this data and manage this system at "
#            "https://landscape.canonical.com/")
        return succeed(None)


```
run update-motd like
```
sudo update-motd
```
that should fix it.

---

### Post by tiberiustibz on 2012-05-29
FYI the landscapelink.py resides in 
```
/usr/share/pyshared/landscape/sysinfo/landscapelink.py
```
for Ubuntu 12.04 in my install. It was slightly more annoying to locate.

---

