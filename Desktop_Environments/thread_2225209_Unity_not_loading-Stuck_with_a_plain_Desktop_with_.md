---
title: "Unity not loading-Stuck with a plain Desktop with just a Wallpaper and mouse cursor."
date: 2014-05-20
forum: Desktop Environments
---

### Post by 7Starphy on 2014-05-20
[SIZE=3][FONT=times new roman][COLOR=#333333]I am using Ubuntu 14.04  and my Desktop is gone. After I log in, Unity would not start and I am stuck with just a working mouse cursor.[/COLOR]
[COLOR=#333333]I have a hybrid AMD-Graphic card and I have removed anything related to fglrx (I think) by using Ctrl + Alt + F1.[/COLOR]
[COLOR=#333333]I re-installled the xserver, ubuntu-desktop, unity. But nothing works.[/COLOR]
[COLOR=#333333]I installed compizconfig-settings manager and tried to enable the Unity Plugin package,but ccsm won't' load because I get an error saying No protocol Specified . No application which requires a GUI, works because it says it is not able to connect to the Xserver and X11 initialization failed.[/COLOR][/FONT][/SIZE]
[SIZE=3][COLOR=#333333][FONT=UbuntuRegular]I tried ```
dconf reset -f /org/compiz/
``` but that throws an error saying Error spawning command line 'dbus-launch .[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Can someone please help me and get my desktop back ?
 I ran 
```
DISPLAY=:0.0 ccsm I get
```[/FONT][/COLOR]
```
compizconfig - Info: Backend : ini
compizconfig - Info: Integration: true
compizconfig - Info: Profile: default
[690.211258] ata1.00: exception Emask 0x0 SAct 0x7fffffff SErr 0x40000 action 0x0
[690.211315] ata1.00: irq_stat 0x400000008
[690.212031] ata1: SError: { CommWake}
[690.212747] ata1.00: failed command: READ FPDMA QUEUED
[690.213444] ata1.00 cmd ____<some address>_________________ tag 8 ncq 4096 in

```[COLOR=#333333][FONT=UbuntuRegular]
The error continues, I could not write down everything from the terminal. In the end there was some Emask media error and I/O error,dev sda, Bus error(dumpped)[/FONT][/COLOR][/SIZE]

---

