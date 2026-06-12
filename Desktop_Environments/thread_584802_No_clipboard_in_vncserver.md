---
title: "No clipboard in vncserver"
date: 2007-10-21
forum: Desktop Environments
---

### Post by lptr on 2007-10-21
vncserver working fine so far on a Gutsy box. vncviewer connecting to Gutsy using F8 brings up VNC menu dialog in Options... Accept clipboard from server and Send clipboard to server options are enabled.

Result: I cannot paste anything into the viewer window except those content that is already inside local clipboard of Gutsy box. 

Tried also using RealVNC viewer from XP machine (so viewer should not be the problem). Same trouble. I tried this also on a Feisty and a Hoary installation as vncserver. On all machines same: No clipboard content will be copied into the viewer window.

Any ideas what is wrong, here? Or is this a known bug?

rob*


[Update]
Tried around and found that KDE has something built into that is called [COLOR=Red]Desktop Sharing[/COLOR]. The server component is included in package [COLOR=Red]**krfb**[/COLOR]. This is located under KDEstart / Internet menu. With it a local user can share his own display ( x:0 ). This server is using VNC protocol, too. Compared to vncserver It _provides working_ clipboard functionality. Seems there is indeed a problem with vncserver anyhow - regarding clipboard. 

Stupid thing because for admin purpose it is often needed to log on to another machine without any user interaction. :( 
Yes there is SSH, too. I know... but it is more comfortable and sometimes even needed, to use a graphical environment.

---

### Post by pedro_p on 2008-04-24
It works all right. Just run the program 'vncconfig' within the remote window, check the options regarding the clipboard and try again. 

BTW - I've got the program in the config script vncconfig -iconic & etc, but it does not work this way. 

Piotr

---

