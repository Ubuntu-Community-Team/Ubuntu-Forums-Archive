---
title: "Need to set Natty machine to accept remote desktop connections."
date: 2011-01-29
forum: Desktop Environments
---

### Post by OneMixDJ on 2011-01-29
Greetings all,

After digging around, I remain stumped in a way.

I'm trying to set a laptop running Natty to accept remote connections (VNC).

I've tried everything, including command line entries to open 5800 & 5900; but no dice.

In earlier versions (i.e Hardy), you used to be able to go to Preferences to set Accept Remote Desktop Connections. 
However, there doesn't seem to be a similar option in Natty.

If someone can shed light, it would be most appreciated.

Mind you, I can remote out; just can't remote in. :confused:

Thanks all!

---

### Post by HereInOz on 2011-01-29
You could try NX

[http://www.nomachine.com/](http://www.nomachine.com/)

Sets up a server on the machine to which you want to connect, but you do have to have a client installed on the machine from which you want to connect.  Clients are available for Windows and Linux.

Much more betterer that VNC, and it is a SSL connection.  You will need OpenSSL server on the host machine as well.

---

### Post by OneMixDJ on 2011-02-05
> **HereInOz said:**
> You could try NX

[http://www.nomachine.com/](http://www.nomachine.com/)

Sets up a server on the machine to which you want to connect, but you do have to have a client installed on the machine from which you want to connect.  Clients are available for Windows and Linux.

Much more betterer that VNC, and it is a SSL connection.  You will need OpenSSL server on the host machine as well.



Sorry I didn't respond sooner; I will try this.
Many thanks!

:)

---

### Post by craig-hansen on 2011-09-28
The "Remote Desktop" panel is still accessible under the "System Settings" application in Natty. From the "Ubuntu" icon in the left corner, select "Applications" (looks like a + sign in a circle), search for "settings" and choose "System Settings." From the app, you can start the "Remote Desktop" panel and set the options as appropriate.



> **OneMixDJ said:**
> Greetings all,

After digging around, I remain stumped in a way.

I'm trying to set a laptop running Natty to accept remote connections (VNC).

I've tried everything, including command line entries to open 5800 & 5900; but no dice.

In earlier versions (i.e Hardy), you used to be able to go to Preferences to set Accept Remote Desktop Connections. 
However, there doesn't seem to be a similar option in Natty.

If someone can shed light, it would be most appreciated.

Mind you, I can remote out; just can't remote in. :confused:

Thanks all!

---

### Post by craig-hansen on 2011-09-28
...or access the "System Settings" menu item under the "Power" icon the in the upper right corner.

---

