---
title: "UltimateBet through WINE"
date: 2007-01-12
forum: Gaming &amp; Leisure
---

### Post by ahouterloot on 2007-01-12
I'm hoping someone can help.  I installed WINE so that I could run UltimateBet to play with some friends.  I got everything installed, and did a manual load of one of the dll's that was missing.  So I got as far as getting the initial splash screen loading, but I can't get the program to load completed.  Everything I have found says UltimateBet runs fine under WINE, but apparently I am alone in my problem loading the app.

Here is the read-out I get when I try to start the application through the terminal (seeing as it doesn't show this when I try to launch through the Apps menu):

ahouterloot@AHLAPTOP:~$ wine "c:\program files\UltimateBet\ultimatebet.exe"
fixme:winsock:NtStatusToWSAError Status code c0000024 converted to DOS error code 6
fixme:winsock:NtStatusToWSAError Status code c0000024 converted to DOS error code 6
fixme:winsock:NtStatusToWSAError Status code c0000024 converted to DOS error code 6
fixme:winsock:NtStatusToWSAError Status code c0000024 converted to DOS error code 6
fixme:winsock:NtStatusToWSAError Status code c0000024 converted to DOS error code 6
fixme:winsock:NtStatusToWSAError Status code c0000024 converted to DOS error code 6
fixme:winsock:NtStatusToWSAError Status code c0000024 converted to DOS error code 6
fixme:winsock:NtStatusToWSAError Status code c0000024 converted to DOS error code 6
fixme:winsock:NtStatusToWSAError Status code c0000024 converted to DOS error code 6
fixme:winsock:NtStatusToWSAError Status code c0000024 converted to DOS error code 6
fixme:winsock:NtStatusToWSAError Status code c0000024 converted to DOS error code 6
fixme:winsock:NtStatusToWSAError Status code c0000024 converted to DOS error code 6
fixme:shdocvw:PersistStreamInit_InitNew (0x1ab320)
fixme:shdocvw:PersistStreamInit_InitNew (0x1ab950)
fixme:shdocvw:navigate_url Unsupported arguments

I am assuming the problem lies in the last line, but am not sure how to fix it.  Can anyone give me some direction???

Thanks!

---

### Post by meng on 2007-01-12
Did you install IE6?

---

### Post by ahouterloot on 2007-01-12
Yes.  It won't even let you install UltimateBet until that is installed.

Ok...did a little more tweaking and it seems to be working now.  I've only been messing with this for a couple of days on and off!!![COLOR="Blue"][/COLOR]

---

### Post by sdjkfhk123j4h2jk on 2007-04-21
Could you explain what was the tweaking you did?

Now I'm stuck where you were, with the "navigate_url Unsupported arguments".

---

