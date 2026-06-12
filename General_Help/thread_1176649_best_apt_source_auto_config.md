---
title: "best apt source auto config?"
date: 2009-06-02
forum: General Help
---

### Post by jbird80 on 2009-06-02
when using synaptic in gnome you can run a ping test to locate the quickest mirror, which will then modify your source.list file, is there an equivalent when using the command line only?

Jason

---

### Post by unutbu on 2009-06-02
Hello jbird80, welcome to the forums.

Save this to ~/bin/best_server.py

[PHP]#!/usr/bin/env python
import os
import aptsources.distro
import aptsources.sourceslist
import socket
from softwareproperties.MirrorTest import MirrorTest

socket.setdefaulttimeout(20)
distro = aptsources.distro.get_distro()
distro.get_sources(aptsources.sourceslist.SourcesList())

pipe = os.popen("dpkg --print-architecture")
arch = pipe.read().strip()
test_file=("dists/%s/%s/binary-%s/Packages.gz" % 
           (distro.source_template.name,
            distro.source_template.components[0].name,
            arch))
mirrors=distro.source_template.mirror_set.values()
app = MirrorTest(mirrors,test_file)
app.running.set()
app.start()
app.run_full_test()
[/PHP]
Make it executable:
```

chmod 755 ~/bin/best_server.py
```

Run it like this:
```

best_server.py
```

---

