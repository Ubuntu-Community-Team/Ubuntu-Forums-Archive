---
title: "Icons are not added to system tray"
date: 2011-05-03
forum: Desktop Environments
---

### Post by krojew on 2011-05-03
Hi,
After installing Kubuntu 11.04, the system tray has gone wild. It contains network manager, volume etc. icons, but applications cannot add theirs. For example Skype status icon positions itself in the top left screen corner; Pidgin icon floats in a small window on the desktop. What could be wrong?

---

### Post by BryanFRitt on 2011-05-04
*(ops... mine is just that application's icons are gone altogether, not crazy... even though I've seen tray icons go crazy in the past)*
Same problem here... Tried searching for an answer, and so far I'm no solutions for KDE's panel.

As far as I can tell I'm only running one 'system tray' or 'notification tray'.
All 'Entries' in 'System Tray Settings are set to 'Always Visible'

Wierd... I just tried removing my system tray... It went away, but if I go to 'Add Widgets' it has a check mark next to it like there's one still running, but there's NOT one on the task bar.

---

### Post by BryanFRitt on 2011-05-05
Fixed my application system tray icons not showing up ...

in a a 'terminal emulator' such as '[FONT="Courier New"]konsole[/FONT]':
[FONT="Courier New"]kquitapp plasma-desktop[/FONT]
opened this file with a text editor such as kate:
[FONT="Courier New"]kate ~/.kde/share/config/plasma-desktop-appletsrc &[/FONT]
found the section that had '[FONT="Courier New"]systemtray[/FONT]' in it
and deleted the lines that had the matching groups of text that had as their headers the same the '[FONT="Courier New"]systemtray[/FONT]' one
[FONT="Courier New"][Containments][***][Applets][***][/FONT]
where [FONT="Courier New"]***[/FONT] is the same number as the ones with '[FONT="Courier New"]systemtray[/FONT]' in them
saved the file
[FONT="Courier New"]Ctrl+s[/FONT]
and restarted the system tray with this command:
[FONT="Courier New"]plasma-desktop[/FONT]
added a system tray back to the panel:
Cashew->Add Widgets->Type in '[FONT="Courier New"]System Tray[/FONT]' into the text box->Drag the System tray icon to where it's wanted in the panel->...->Configure '[FONT="Courier New"]System Tray Settings[/FONT]' to liking...

---

### Post by krojew on 2011-05-18
Unfortunately it didn't help.

---

### Post by BryanFRitt on 2011-05-18
> **krojew said:**
> Hi,
After installing Kubuntu 11.04, the system tray has gone wild. It contains network manager, volume etc. icons, but applications cannot add theirs. For example Skype status icon positions itself in the top left screen corner; Pidgin icon floats in a small window on the desktop. What could be wrong?

I think I remember what did to fix that error back when I had this icons out of tray problem...

I think it was something to do with the way Compiz, etc... is started up. 

If you want to have Compiz automatically start at login, you can set it up to start automatically via '*System System Settings->Workspace Appearance and Behavior->Default Applications->Window Manager->use different _w_indow Manager->Compiz*'. 

If you have an [FONT="Courier New"]~/.kde/Autostart/...[/FONT] script try adding '[FONT="Courier New"]sleep XX[/FONT]' where [FONT="Courier New"]XX[/FONT] is an integer (like [FONT="Courier New"]5[/FONT] or [FONT="Courier New"]15[/FONT]... it's in seconds) between commands. <-This can be very time consuming if you want a faster boot, and try to tweak it to the nearest second. In tweaking sometimes it may boot/login fine one time, but even with no changes, it might not work the second time(not so much fun), longer times are more likely to work more often, but makes it take longer to boot/login everytime. Also order might make a difference, try putting things in a order that makes since in this file.

Also look at '*System Settings->Startup and Shutdown->Autostart*' and '*System Settings->Startup and Shutdown->Session Management*' and see what you do with them.

---

### Post by Tilex on 2011-07-08
> **BryanFRitt said:**
> Fixed my application system tray icons not showing up ...

in a a 'terminal emulator' such as '[FONT="Courier New"]konsole[/FONT]':
[FONT="Courier New"]kquitapp plasma-desktop[/FONT]
opened this file with a text editor such as kate:
[FONT="Courier New"]kate ~/.kde/share/config/plasma-desktop-appletsrc &[/FONT]
found the section that had '[FONT="Courier New"]systemtray[/FONT]' in it
and deleted the lines that had the matching groups of text that had as their headers the same the '[FONT="Courier New"]systemtray[/FONT]' one
[FONT="Courier New"][Containments][***][Applets][***][/FONT]
where [FONT="Courier New"]***[/FONT] is the same number as the ones with '[FONT="Courier New"]systemtray[/FONT]' in them
saved the file
[FONT="Courier New"]Ctrl+s[/FONT]
and restarted the system tray with this command:
[FONT="Courier New"]plasma-desktop[/FONT]
added a system tray back to the panel:
Cashew->Add Widgets->Type in '[FONT="Courier New"]System Tray[/FONT]' into the text box->Drag the System tray icon to where it's wanted in the panel->...->Configure '[FONT="Courier New"]System Tray Settings[/FONT]' to liking...

This fixed my problem, thanks !

---

### Post by ronwilhoite on 2011-09-24
> **BryanFRitt said:**
> Fixed my application system tray icons not showing up ...

in a a 'terminal emulator' such as '[FONT="Courier New"]konsole[/FONT]':
[FONT="Courier New"]kquitapp plasma-desktop[/FONT]
opened this file with a text editor such as kate:
[FONT="Courier New"]kate ~/.kde/share/config/plasma-desktop-appletsrc &[/FONT]
found the section that had '[FONT="Courier New"]systemtray[/FONT]' in it
and deleted the lines that had the matching groups of text that had as their headers the same the '[FONT="Courier New"]systemtray[/FONT]' one
[FONT="Courier New"][Containments][***][Applets][***][/FONT]
where [FONT="Courier New"]***[/FONT] is the same number as the ones with '[FONT="Courier New"]systemtray[/FONT]' in them
saved the file
[FONT="Courier New"]Ctrl+s[/FONT]
and restarted the system tray with this command:
[FONT="Courier New"]plasma-desktop[/FONT]
added a system tray back to the panel:
Cashew->Add Widgets->Type in '[FONT="Courier New"]System Tray[/FONT]' into the text box->Drag the System tray icon to where it's wanted in the panel->...->Configure '[FONT="Courier New"]System Tray Settings[/FONT]' to liking...

This fixed two blank icons in the system tray (knotes and konversation) following an upgrade to 11.10 Beta2. Thanks!

---

