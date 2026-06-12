---
title: "Execute script at login"
date: 2006-06-16
forum: Desktop Environments
---

### Post by vigleik on 2006-06-16
I want to execute a little script every time I log in to kde, and I thought I could do this by putting my script in ~/.kde/Autostart/. My script is named xbindkeys and looks like this:

#/bin/sh
xbindkeys

It is executable, and if I type "./.kde/Autostart/xbindkeys" after logging in it does start xbindkeys, but when I log in nothing happens.

This puzzles me. When searching the forum for starting things automatically I've seen several people suggest putting little scripts in ./kde/Autostart.

I guess I could put my script in /etc/init.d/ instead and mess around with update-rc.d, but that seems silly. I don't want/need to run xbindkeys as root anyway.

Vigleik

---

### Post by ifokkema on 2006-06-16
[QUOTE=vigleik]I want to execute a little script every time I log in to kde, and I thought I could do this by putting my script in ~/.kde/Autostart/. My script is named xbindkeys and looks like this:

#/bin/sh
xbindkeys

It is executable, and if I type "./.kde/Autostart/xbindkeys" after logging in it does start xbindkeys, but when I log in nothing happens.

This puzzles me. When searching the forum for starting things automatically I've seen several people suggest putting little scripts in ./kde/Autostart.

I guess I could put my script in /etc/init.d/ instead and mess around with update-rc.d, but that seems silly. I don't want/need to run xbindkeys as root anyway.

Vigleik[/QUOTE]

Hi,

I know nothing about KDE, but if you don't get it running like that, you can have a script run as a certain user by setting the 's' flag using chmod. This solves the problem you have with putting your script in /etc/init.d.

Commands:
```
sudo chown myusername /etc/init.d/scriptname
chmod u+s /etc/init.d/scriptname
```

Hope this helps at least a bit.

---

### Post by Fatjoint on 2006-06-16
[QUOTE=vigleik]I want to execute a little script every time I log in to kde, and I thought I could do this by putting my script in ~/.kde/Autostart/. My script is named xbindkeys and looks like this:

#/bin/sh
xbindkeys

It is executable, and if I type "./.kde/Autostart/xbindkeys" after logging in it does start xbindkeys, but when I log in nothing happens.

This puzzles me. When searching the forum for starting things automatically I've seen several people suggest putting little scripts in ./kde/Autostart.

I guess I could put my script in /etc/init.d/ instead and mess around with update-rc.d, but that seems silly. I don't want/need to run xbindkeys as root anyway.

Vigleik[/QUOTE]

I believe you need the "." before your filename to let bash know that you are executing a script. 

Try this -

#/bin/sh
. xbindkeys

---

### Post by Neo Ex on 2006-06-16
I'm not sure the problem is this, but... in other scripts I've always seen #!/bin/bash at the beginning of the file, not #/bin/sh. Maybe if you add that '!' you can solve the problem.

---

### Post by vigleik on 2006-06-16
[QUOTE=Neo Ex]I'm not sure the problem is this, but... in other scripts I've always seen #!/bin/bash at the beginning of the file, not #/bin/sh. Maybe if you add that '!' you can solve the problem.[/QUOTE]

Ah, yes. That's it exactly. I didn't remember what's usually on the first line, but I didn't think it mattered because it looks like a comment! Besides it worked when I executed it from the command line. Apparently it's not a comment, but rather an instruction to let bash execute the commands to come. Now everything is working as expected. Thanks.

Vigleik

---

### Post by ifokkema on 2006-06-17
[QUOTE=vigleik]Ah, yes. That's it exactly. I didn't remember what's usually on the first line, but I didn't think it mattered because it looks like a comment! Besides it worked when I executed it from the command line. Apparently it's not a comment, but rather an instruction to let bash execute the commands to come. Now everything is working as expected. Thanks.

Vigleik[/QUOTE]

Ah, missed that. Good call, Neo.

This line is meant to tell which interpreter to use. For instance, when writing a perl script that you want to run as an executable, you need to type
#!/usr/bin/perl
at the top of the script. I assume, when running the script from your terminal, bash just assumed it was a bash script since the interpreter was not specified. However, KDE probably does not run it without the interpreter specified.

---

