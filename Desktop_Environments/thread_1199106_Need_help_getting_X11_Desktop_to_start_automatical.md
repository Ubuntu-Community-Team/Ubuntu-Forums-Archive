---
title: "Need help getting X11 Desktop to start automatically"
date: 2009-06-28
forum: Desktop Environments
---

### Post by chocobosage85 on 2009-06-28
So set up a little file/print server with a few extra spare parts I had lying around and it's working fine. Just so you understand the setup, I don't have a spare monitor lying around so I set up a VNC server (x11vnc) and that works great.

However... A recently gave it a bit of an upgrade (new mobo, processor, ram and storage disk). And I did a clean reinstall, But now the server starts up in cosole/terminal text based OS instead of the x11 desktop environment whenever it's restarted without a monitor attached. I'm assuming it does that because it can tell there's no monitor attached, because if I attach one prior to starting it up, it goes right into xfce. How can I override that setting? I would like it to start the desktop environment with out me having to manually type "startx".

Thank you so much for any help you guys can provide, I really appreciate it. I'm new to linux, but I'm liking it more and more as I use it. If I weren't such a video gamer... i'd probably switch, lol.

My System specs:
        Mobo: ECS A780GM-A AM2+ AMD780G RT
                    CPU:   AMD A64 LE-1640 2.6G
                  Memory: 2GB DDR2 (1GB x 2) PATRIOT PDC22G6400LLK
                Drive 1: Some 40G IMB Deskstar (OS)
Drive 2: 500G Hitachi HDP725050GLA360 (Storage)
        
Thanks Again!

---

### Post by Harii on 2009-06-28
try this it worked for me

[http://www.debianadmin.com/how-to-auto-login-and-startx-without-a-display-manager-in-debian.html]("http://www.debianadmin.com/how-to-auto-login-and-startx-without-a-display-manager-in-debian.html")

---

### Post by chocobosage85 on 2009-06-29
Hey thanks for the advice, however it didn't work. I started to try both methods found in the link you provided, but I found that the "/etc/inittab" file doesn't exist system (or at least not at the location? or in some other form?).

Does anyone know where the equivalent file is in the xubuntu 9.04 system?

---

