---
title: "Moving File"
date: 2005-12-26
forum: Desktop Environments
---

### Post by reb68 on 2005-12-26
I am using Kubuntu and Mozilla. In trying to get RealPlayer10 or Mplayer to work in Mozilla the install says I need to move the "mplayerplug-in.xpt" file to the mozilla/components folder. It is in the mozilla/plugins folder and will not copy,drag and drop or cut and paste. I do not have access. Does anyone have a solution? I will use either media program as to connect to the Fire/ems radio 0n the web. My grandson is a Fireman/EMS and I would like to listen to the calls. Thanks for any help or ideas. I will even go back to Firefox if I have too. I hope I am not in the wrong forum. I could not find an answer in the Fire Fox/Mozilla pages.

---

### Post by HermanAB on 2005-12-28
You probably need higher permissions, so change to the super user root and do it from the command line:
$ sudo su -
password
# cd wherever
# cp whatever somewhere

'Hope that helps!

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by aysiu on 2005-12-28
Alt-F2
```
kdesu konqueror
```

---

