---
title: "Multimonitor doesnt persist settings after restart"
date: 2013-05-11
forum: Desktop Environments
---

### Post by kubco2 on 2013-05-11
Hello,

my problem is that everytime when I restart/start notebook I must set multimonitor settings in sudo catalyst, it is even worse, because I must after every change apply settings.
I do it in sudo AMD catalyst:
cloned display -> extended display -> apply settings
change res of extended display -> apply
change res of built in display -> apply
change position of extended display -> apply -> OK

I have AMD 5650 VGA ... ubuntu Gnome remix 12.10 and proprietary AMD catalyst 13.4

Thanks for help.

---

### Post by QIII on 2013-05-11
Hello!

First off, you should be using gksudo when running CCC in admin mode.   Get in the habit of using gksudo whenever you need to open a graphical  application with elevated privileges.  If you don't, you can really  wreak havoc with file permissions and wind up with a mess.

Could you give us a little more information about your notebook?  To what type of port are you connecting your external monitor?

---

### Post by kubco2 on 2013-05-11
Ok, I think I open it in gksudo: winkey ... find it in gnome shell and hit enter, password box will popup ....

I use Acer aspire 3820tg running in AMD VGA only mode .... and I have connected it to HDMI port.
>  I have AMD 5650 VGA ... ubuntu Gnome remix 12.10 and proprietary AMD catalyst 13.4

---

### Post by kubco2 on 2013-05-11
This partially solved my problem [http://ubuntuforums.org/showthread.php?t=970585&p=6622027#post6622027](http://ubuntuforums.org/showthread.php?t=970585&p=6622027#post6622027) ... I don't understand why this problem after many years is still here ...
Now I have only one problem, that after restart I must set Scaling options in amdcccle under external monitor ..... It is set to 0%(in reality it is 8%), but when I move slider, it jumps to 8%, and I must set it to 0% and apply ...

edit: this solved scaling issues ....
```
sudo aticonfig --set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,0
```

---

