---
title: "RDP Windows"
date: 2012-09-25
forum: Desktop Environments
---

### Post by mike acker on 2012-09-25
I am trying to establish RDP to my Windows box . I've tried various clients, KRDC looks like a good choice -- any clues on using this ?  it acts like it connects (wireless intranet ip address) but (1) just a blue screen and (2) no request for permission on the windows system . RDP is enabled on the windows box but normally a connect will result in a request for permission on the windows box

i'd like to escape from needing a monitor/keyboard/mouse switch ( i can't fine one ) or use of WINE -- when i switch to Linux as my main system

---

### Post by cogier on 2012-09-25
Try [Teamviewer 7]("http://www.teamviewer.com/en/index.aspx?pid=google.tv.s.uk&gclid=CNv46qGv0bICFQMMfAodijUAyw"). It's free and there are versions for Ubuntu and Windows.

---

### Post by spier on 2012-09-25
I'm using remmina for rdp and vnc connections to windows hosts, without any problem!

```
sudo apt-get install remmina
```

---

