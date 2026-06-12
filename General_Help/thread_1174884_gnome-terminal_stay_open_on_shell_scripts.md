---
title: "gnome-terminal stay open on shell scripts"
date: 2009-05-31
forum: General Help
---

### Post by bkbilly on 2009-05-31
[FONT=Comic Sans MS][SIZE=2]If you are using shell scripts, then many of you may wonder how to make "gnome-terminal" make a command and then stay open...
I found this solution!
It was hard to find but i finally found it :p[/SIZE][/FONT]

[COLOR=Blue]To run a command using the terminal through a shell script you can put this:[/COLOR]
> gnome-terminal **-e** "*fortune*"[COLOR=Purple]the problem with this command is that it immediately closes...[/COLOR]

[COLOR=Blue]The solution is this:[/COLOR]
> gnome-terminal **-x bash** **-c** "*fortune* **;bash**"[COLOR=Purple]with this command the user can continue typing commands on his own...[/COLOR]

[COLOR=Blue]If you want to close it after a period of time then you can use this:[/COLOR]
> gnome-terminal **-x bash** **-c** "*fortune* **&& sleep 2**"[COLOR=Purple]this will close the terminal after 2 seconds
[/COLOR]
[COLOR=Red]You must watch out for the bold commands to be right!
The command **fortune** is a command I chose! You can replace it with your own command.[/COLOR]

---

