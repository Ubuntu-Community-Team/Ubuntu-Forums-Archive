---
title: "How to redirect output of systemd service to Ubuntu Boot Screen (20.04)"
date: 2020-06-15
forum: Desktop Environments
---

### Post by yevhenii8 on 2020-06-15
Hi there!

[COLOR=#242729][FONT=Arial]I have a systemd service that performs sync between local disk and Cloud Storage during shutdown. Something like this:
[/FONT][/COLOR]```
[Unit]
Description=Syncing with MEGA cloud storage v56
After=network-online.target

[Service]
...
ExecStart=/bin/true
ExecStop=/usr/local/sbin/auto-sync.sh
RemainAfterExit=true
TimeoutStopSec=0
...
 
[Install]
WantedBy=multi-user.target
```

[COLOR=#242729][FONT=Arial]Now, I've upgraded to Ubuntu 20.04 and during Ubuntu shutdown\boot see only black screen with 'Ubuntu' inscription in the bottom. I don't have any vendor image. And I'm wondering If I can redirect output of my auto-sync.sh script to Ubuntu shutdown screen.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The best option here would be to arrange some square in the center of the screen and print there white text just like any console/terminal does. So, I have several questions:[/FONT][/COLOR]

[LIST=1]
[*]Is something like that possible at all ?
[*]Could it be done just with Bash and some Ubuntu\Gnome configuration ?
[*]May be I have to write a separate application ?
[/LIST]
[COLOR=#242729][FONT=Arial]Any thoughts\idea\guidelines are welcome! Thank you![/FONT][/COLOR]

---

