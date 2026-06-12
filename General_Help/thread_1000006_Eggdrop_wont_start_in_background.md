---
title: "Eggdrop wont start in background"
date: 2008-12-02
forum: General Help
---

### Post by Jers on 2008-12-02
Hello All, 

I have been use ubuntu for about a year now i just reformatted and i cant seem to get eggdrops runniing without useing ./eggdrop -m eggdrop.conf -n 

I have done research on this problem i found an old link for eggdrop version 1.6.17.. I have tryed this method with the newest version of eggdrop which is 1.6.19 but dont seem to work.


When I use ./eggdrop -m eggdrop.conf it starts as normal but wont connect to the server. I tryed to let it sit over night to see if it needed time to connect but no luck. I Have tryed useing other network servers as well and they still wont connect.

But when i start it. It comes back normal like this.

Eggdrop v1.6.19 (C) 1997 Robey Pointer (C) 2008 Eggheads
[13:22] --- Loading eggdrop v1.6.19 (Tue Dec  2 2008)
[13:22] Listening at telnet port ***** (all).
[13:22] Module loaded: dns
[13:22] Module loaded: channels
[13:22] Module loaded: server
[13:22] Module loaded: ctcp
[13:22] Module loaded: irc
[13:22] Module loaded: notes            (with lang support)
[13:22] Module loaded: console          (with lang support)
[13:22] Module loaded: blowfish
[13:22] Module loaded: uptime
[13:22] Userinfo TCL v1.07 loaded (URL BF GF IRL EMAIL DOB PHONE ICQ).
[13:22] use '.help userinfo' for commands.
[13:22] Creating channel file


STARTING BOT IN USERFILE CREATION MODE.
Telnet to the bot and enter 'NEW' as your nickname.
OR go to IRC and type:  /msg Botnick hello
This will make the bot recognize you as the master.

[13:22] === Botnick: 0 channels, 0 users.
Launched into the background  (pid: 21084)


Any Help Would Be Great 

Thanks

---

### Post by Jers on 2008-12-02
I Have Found A Way Of Fixing This Issue By Uninstalling tcl8.5-dev and installing tcl8.4-dev 

(solution)

---

