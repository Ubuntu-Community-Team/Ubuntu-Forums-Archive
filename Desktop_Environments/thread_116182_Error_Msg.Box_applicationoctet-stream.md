---
title: "Error Msg.Box: application/octet-stream"
date: 2006-01-12
forum: Desktop Environments
---

### Post by Snifffurt on 2006-01-12
Since a week or so, KDE is pulling up a error msg. Box after starting any Programm.

The msg.Box says:

ERROR <programmname>
MIME-Type not available
application/octet-stream
[OK]

After OKing the msg.Box all the programms start and work with no truble.

How can I get rid of this annoying Errorwarnings all the time?

Regards

Snifffurt

---

### Post by Snifffurt on 2006-01-14
Hello again

I sort of solved it. Or better found a sort of way arround.

First I createt in Kcontrol -> KDE-Components -> File associations a empty new type application/octet-stream wich helped allready. It seems KDE was searching this, so I made it confident ;-)

Afterwards I followed the instruction from this link [http://www.computerhilfen.de/hilfen-6-45717-0.html](http://www.computerhilfen.de/hilfen-6-45717-0.html) and deleted ~/.kde/share/mimelnk/application/octet-stream.desktop

I can't remove the application/octet-strem in KDE-Control now. 

However, it does not seem to cause any truble so far, so I'm just going to live with this. ;) 

Regards

Snifffurt

---

