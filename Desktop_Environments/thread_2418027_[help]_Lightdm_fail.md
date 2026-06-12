---
title: "[help] Lightdm fail"
date: 2019-04-30
forum: Desktop Environments
---

### Post by crwo98 on 2019-04-30
[COLOR=#333333][FONT=&amp]Hi everyone, I'm new in the forums and I need your help.

[/FONT][/COLOR][COLOR=#333333][FONT=&amp]I've got a problem with lightdm, as it fails to start x session.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]The following message appears on startup:[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp][[/FONT][/COLOR][COLOR=#FF0000][FONT=&amp]FAILED[/FONT][/COLOR][COLOR=#333333][FONT=&amp]] Failed to start Light Display Manager.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]See 'systemctl status lightdm.service' for details.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]So that's what I did, and this is what came back:
[/FONT][/COLOR]```
[COLOR=#2E8B57][FONT=Monaco]&#9679; lightdm.service - Light Display Manager[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]   Loaded: loaded (/lib/systemd/system/lightdm.service; enabled; vendor preset: [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]   Active: failed (Result: exit-code) since Tue 2019-04-30 10:38:46 WEST; 5min a[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]     Docs: man:lightdm(1)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Process: 565 ExecStart=/usr/sbin/lightdm (code=exited, status=1/FAILURE)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Process: 561 ExecStartPre=/bin/sh -c [ "$(cat /etc/X11/default-display-manager[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco] Main PID: 565 (code=exited, status=1/FAILURE)[/FONT][/COLOR]
```[COLOR=#333333][FONT=&amp]

[/FONT][/COLOR][COLOR=#333333][FONT=&amp]I then run a [/FONT][/COLOR][COLOR=#00BF00][FONT=&amp]sudo lightdm --test-mode --debug[/FONT][/COLOR][COLOR=#333333][FONT=&amp] command to check what was going on:
```
[/FONT][/COLOR][COLOR=#2E8B57][FONT=Monaco][+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.00s] DEBUG: Starting Light Display Manager 1.18.3, UID=0 PID=1625[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/01_debian.conf[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.00s] DEBUG: Using Xephyr for X servers[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.00s] DEBUG: Registered seat module xlocal[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.00s] DEBUG: Registered seat module xremote[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.00s] DEBUG: Registered seat module unity[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Monitoring logind for seats[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: New seat added from logind: seat0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Seat seat0: Loading properties from config section Seat:*[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Seat seat0: Starting[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Seat seat0: Creating user session[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Loading users from org.freedesktop.Accounts[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: User /org/freedesktop/Accounts/User1000 added[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Seat seat0: Creating display server of type x[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Could not run plymouth --ping: Failed to execute child process "plymouth" (No such file or directory)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Using VT 7[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Seat seat0: Starting local X display on VT 7[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: DisplayServer x-1: Logging to /var/log/lightdm/x-1.log[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: DisplayServer x-1: Can't launch X server Xephyr, not found in path[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: DisplayServer x-1: X server stopped[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Releasing VT 7[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Seat seat0: Display server stopped[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Seat seat0: Can't create display server for automatic login[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Seat seat0: Session stopped[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Seat seat0: Stopping display server, no sessions require it[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Seat seat0: Creating greeter session[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Seat seat0: Creating display server of type x[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Using VT 7[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Seat seat0: Starting local X display on VT 7[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: DisplayServer x-1: Logging to /var/log/lightdm/x-1.log[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: DisplayServer x-1: Can't launch X server Xephyr, not found in path[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: DisplayServer x-1: X server stopped[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Releasing VT 7[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Seat seat0: Display server stopped[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Seat seat0: Can't create display server for greeter[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Seat seat0: Session stopped[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.01s] DEBUG: Seat seat0: Stopping display server, no sessions require it[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.02s] DEBUG: Seat seat0: Stopping[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.02s] DEBUG: Seat seat0: Stopped[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][+0.02s] DEBUG: Failed to start seat: seat0[/FONT][/COLOR]
```[COLOR=#333333][FONT=&amp]

[/FONT][/COLOR][COLOR=#333333][FONT=&amp]I tried re-installing all the xorg package, but nothing changed.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Also, after the error message, it lets me manually run the startx, and the DE is there fully working.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]Any idea on how to solve this?
[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Thank you very much in advance.[/FONT][/COLOR]

---

### Post by Claus7 on 2019-05-08
Hello,

definitely this is not a fix you are seeking, yet it is the only time that I would advice switching from lightdm to gdm3. I do not know exactly if this is compatible with xubuntu, at least with ubuntu it is, so you will have to check it out. Usually lightdm is behaving better than gdm3 in the issues I have encountered. Maybe in your case, the other way around might help.

Regards!

---

