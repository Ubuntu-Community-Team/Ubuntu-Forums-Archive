---
title: "Prevent sleep while SSH session active"
date: 2018-05-10
forum: Desktop Environments
---

### Post by geronimo350 on 2018-05-10
Hi all,

I'm trying to prevent computer from going to sleep while there is an active SSH connection but just can't set it up. 

Found a short description on how to do it but it doesn't work:
[https://askubuntu.com/questions/521620/prevent-machine-from-sleeping-when-ssh-connections-are-on?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa](https://askubuntu.com/questions/521620/prevent-machine-from-sleeping-when-ssh-connections-are-on?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa)

Since I'm using ubuntu 16.04 I have tried to move the script to */lib/systemd/system-sleep/ *and it shows up in logs that script was executed and returned 1 before computer was suspended but it's not preventing it from going to sleep.

I have also tried using Caffeine but it will just crash every time I start it with following error:
[COLOR=#333333][FONT=monospace]/usr/bin/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]caffeine:[/FONT][/COLOR][COLOR=#333333][FONT=monospace]25: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]version([/FONT][/COLOR][COLOR=#333333][FONT=monospace]'Gtk', '3.0') before import to ensure that the right version gets loaded.

BR,
geronimo[/FONT][/COLOR]

---

