---
title: "Applet error &quot;OAFIID&quot; Internode Usage Meter Applet"
date: 2009-06-05
forum: General Help
---

### Post by stuart221 on 2009-06-05
After updating to jaunty. Can no longer run this applet.

The panel encountered a problem while loading "OAFIID:InternodeUsageMeterApplet

---

### Post by mal on 2009-06-05
stuart221,

If you are referring to "Internode Usage Meter 1.6", note the following comment in the INSTALL file:

```
Note: if you are running Ubuntu 9.04, use sudo and specify the prefix:

# sudo python setup.py install --prefix=/usr
```

Hope this helps.

Mal

---

### Post by stuart221 on 2009-06-05
I am getting the following massage and still having the same problem.

stuart@stuart-desktop:~$ file:///home/stuart/internode-applet-1.6/internode/constants.py.in file:///home/stuart/internode-applet-1.6/internode/graph.py file:///home/stuart/internode-applet-1.6/internode/history_window.py file:///home/stuart/internode-applet-1.6/internode/__init__.py file:///home/stuart/internode-applet-1.6/internode/internode.py file:///home/stuart/internode-applet-1.6/internode/nodeutil.py file:///home/stuart/internode-applet-1.6/internode/nodeutil.pyc 

st

---

### Post by alawson on 2009-06-13
Thanks, mal. Adding the *--prefix* switch fixed it for me under Ubuntu 8.10.

---

### Post by AlanOz on 2009-07-09
I've encountered the same thing using Debian Lenny.  Just for the record, I'd like to mention that while using the "--prefix" option at installation time will work perfectly, if you have already installed it *without* this option then to fix it you don't need to install again.

The problem is likely because the locations where the files are installed don't correspond to the locations specified in /usr/lib/bonobo/servers/InternodeUsageMeterApplet.server (the latter are set by the "--prefix" option).  For instance, in my case the program was at /usr/bin/internode-applet.py and associated data were in /usr/share/internode.  However, the InternodeUsageMeterApplet.server file had references:[INDENT]<oaf_server iid="OAFIID:InternodeUsageMeterApplet_Factory" type="exe" location="/usr/local/bin/internode-applet.py">
[/INDENT]and[INDENT]     <oaf_attribute name="panel:icon" type="string" value="/usr/local/share/internode/pixmaps/internode-applet.png"/>
[/INDENT]So all you have to do to fix it is either:

  (1) change the references in InternodeUsageMeterApplet.server to "/usr/bin/internode-applet.py" and "/usr/share/internode/pixmaps/internode-applet.png"

OR

  (2) move the files to match what's in InternodeUsageMeterApplet.server:[INDENT]             $ sudo  mv  /usr/bin/internode-applet.py  /usr/local/bin/
            $ sudo mv  /usr/share/internode  /usr/local/share/
[/INDENT]Hope that gives a little bit of insight for anyone still having this or some similar problem.

Have fun
ao

---

