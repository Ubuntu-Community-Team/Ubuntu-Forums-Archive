---
title: "Ubuntu completely broken within first day of try!"
date: 2007-10-20
forum: Desktop Environments
---

### Post by robinzxp on 2007-10-20
Hello, I installed Ubuntu today to try it out, as my course requires knowledge of linux.

I been really pleased with it until, I tried to install Groovy. It requires setting up PATH environmental variable, so I google around for it a bit, and somewhere it said edit "/etc/environment", so after another digging to find how to get permission to edit that file, I add my location of Groovy/bin to PATH and added "export PATH=$PATH:/opt/local/groovy/bin".

Then I log off, and when I tried to log on I get

=============================================================
"Your session only lasted less than 10 seconds. If your have not.................... Try logging in with one of the failsafe sessions to see if you can fix this problem"

also on view details it said

"(profess:5321): Gtk-WARNING **: This process is currently running setuid or setgid.................. For further details, see" - this is there twice and after that

"Refusing to initialize GTK+
/etc/gdm/Xsession: Beginning session setup...
/etcprofile: 17: id: not found
/etc/gdm/Xession:  178: grep: not found
/etc/gdm/Xession: 192: ls: not found
/etc/gdm/Xession: Executing /usr/bin/gnome-session failed, will try exec: 204: x-terminal-emulator: not found"
==============================================================
(I have shorted some of error, but if it helps to see it all I can type it out)

After error I'm back on logging on again.
I tried "Failsafe GNOME" but that doesn't work either.
Failsafe Terminal works but if i type "ls" I get

"Command 'ls' is available in 'bin/ls'
The command could not be located because '/bin' is not included in the PATH environment variable.
bash: ls: command not found"

I'd be so greatful if someone could help me out with my problem, (and maybe get groovy working too!), otherwise I'm thinking of just going back to windows again.

Thanks

---

### Post by raul_ on 2007-10-20
Boot with a rescue CD, mount your hard drive, edit the file again, and undo the mess ;)

---

### Post by robinzxp on 2007-10-20
Does Ubuntu CD work as rescue CD? It wouldn't let me edit file and if I log in with permission I couldn't get to file, did I miss something? Also what rescue CD would be recommanded?

---

### Post by robinzxp on 2007-10-20
Ok phew, I deleted those lines and it's fixed. Thanks for advice

---

### Post by raul_ on 2007-10-21
Sorry I didn't reply earlier, I was away from home. 

Good thing you figured it out :)

---

### Post by TeaSwigger on 2007-10-21
Remember that there's a price for allowing you full control; it's yours to make or break. That's good in my book. You're actually in control of your computer ;)

---

