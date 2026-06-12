---
title: "Run a profile.d file as root? (Or other alternatives?)"
date: 2008-12-04
forum: General Help
---

### Post by minime283 on 2008-12-04
So I'm just finishing up a system that has a client-server architecture that limits users to 2 hours per day. In profile.d, I have a .sh file that inside it points to a php file like so:

#/bin/bash
php5 /usr/local/src/nlm/startup.php

so this program runs and keeps track of time etc, updates a database, at the end it does this (php command):

exec("sudo reboot");

unfortunately, I can't figure out a way to get this to work. So here's what I am trying to figure out I should do:

make it so "reboot" doesn't need to be sudod? ( I dunno if this is possible)
run as sudo -u username for a username that has a nopassword attribute in /etc/sudoers (as far as I tell, this doesn't work, and is probably dangerous anyway)
run the profile.d script as sudo
run the php script as sudo

So I'm not sure how to go about this. Any ideas? Thanks.

---

### Post by jbo5112 on 2009-07-16
I'm not sure if you still care, but someone googling this might...

There is a setuid bit on the permissions, that if you enable it, the program will be run as the owner.  It doesn't work on scripts though (at least shell scripts), because that would be easy to create horrible security problems.  

You cannot simply run "sudo reboot" either, because the program is in "/sbin", which isn't part of the user's path.  What you can do is run "sudo bash" and pass the script as an argument.  I've had some problems with passing scripts to bash under cygwin.  I don't remember the proper flags I had to set to get it to work, and I don't think it sets your environment variables (like your path).

What will work better is running "sudo /sbin/reboot" or "sudo `sudo which reboot`".  Running which reboot (as root) will output the full path to the reboot command.  The back-quote characters (the ` character next to 1) tell it to run the output of the command inside the back-quotes and not just the back-quotes.  For example, running "echo ls" will output "ls" on the screen, while using back-quotes around it like "`echo ls`" will run the command "ls" that would have otherwise been outputted.

Also, here are the commands to allow anyone to run the reboot command by typing "/sbin/reboot" (type these in a terminal window):
"**sudo chmod go+x /sbin**"
"**sudo chmod 6755 /sbin/reboot**"

The first command gives anyone permission to access files and directories inside the "/sbin" directory.  If users can't do this, they can't run any of the programs inside, but this step is probably unnecessary in Ubuntu.  I think Ubuntu gives everyone read and execute permissions, which is horrible for security, but depending on the setup, might be nice for convenience.

The second command will turn on the set user id and set group id bits; give read, write, and execute permission to the user root; give read and execute permission to everyone in the group root; and give read and execute permission to everyone else.  This is probably all you need for Ubuntu.

Lastly, if you're just looking for a way to boot someone off the machine, just run "pkill -u <username>" or if you're forcing the user to run this "pkill -u $LOGNAME".  This will kill all of the user's processes.

I hope there will be some sort of warnings given to the user before his access is abruptly halted.  If they're logging on with text access, it can be done with "write <username>", but I would have to track down how to do that with a GUI.

---

