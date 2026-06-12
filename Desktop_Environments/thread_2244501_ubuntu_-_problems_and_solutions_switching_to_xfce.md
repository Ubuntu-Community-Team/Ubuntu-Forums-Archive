---
title: "ubuntu - problems and solutions switching to xfce"
date: 2014-09-16
forum: Desktop Environments
---

### Post by ben107 on 2014-09-16
[FONT=arial]Posting in the hopes someone else finds this useful.

Before relating the problems and things I've learned, I think I should mention the default Ubuntu install "just worked" and I didn't have any problems. But I really didn't like the unity interface -- hiding menus until mouseover, close/min/max on the left, the taskbar/app pinner on the left -- didn't like those. Tried to change some settings, but could never get the interface how I liked it. So I installed XFCE. I think if I were to start over, I would just start with xubuntu instead of trying to convert to a different desktop environment.[/FONT]

[FONT=arial]Had to deal with tearing while watching videos in chrome. HD video in VLC seemed to work fine, but flash and html5 video in chrome had some slight tearing. I tried enabling override software rendering in chome ([https://code.google.com/p/chromium/issues/detail?id=160454](https://code.google.com/p/chromium/issues/detail?id=160454)), but that didn't help and after doing some searching, it seems like it was a vsync issue, not necessarily related to chrome. I installed compton following this guide ([http://duncanlock.net/blog/2013/06/07/how-to-switch-to-compton-for-beautiful-tear-free-compositing-in-xfce/](http://duncanlock.net/blog/2013/06/07/how-to-switch-to-compton-for-beautiful-tear-free-compositing-in-xfce/)) and that seemed to resolve the vsync issue.[/FONT][FONT=arial]
[/FONT]
[FONT=arial]Another problem that showed up when switching to XFCE was my keyboard volume keys quit working. I tried adding xfce hotkeys, but that didn't work. What seemed to be recommended the most was to set the active card in the settings editor, but that didn't work for me. Instead it was a comment about running the daemon not in daemon mode [http://askubuntu.com/a/423894/327651](http://askubuntu.com/a/423894/327651)[/FONT]
[FONT=arial]
[/FONT][INDENT][FONT=courier new]kill `pidof xfce4-volumed` ; mkdir -p /tmp/volumed && cd /tmp/volumed && nohup xfce4-volumed --no-daemon &[/FONT][/INDENT]
[FONT=arial]
[/FONT]
[FONT=arial]I left the amixer hotkey commands (volume down only sometimes works without keybinding?), and put the above in a startup script.[/FONT]

[FONT=arial]Other than that, things are great. Plugged in the usb printer and it just worked, same as external IDE through usb. And I'm enjoying netflix in chrome beta 38 and steam on linux.[/FONT]

---

