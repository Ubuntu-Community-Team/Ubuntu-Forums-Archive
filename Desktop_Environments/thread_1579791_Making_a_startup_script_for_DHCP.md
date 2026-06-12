---
title: "Making a startup script for DHCP"
date: 2010-09-22
forum: Desktop Environments
---

### Post by PhilMize on 2010-09-22
Hey all, I'm setting up a image server at a company I work at. I want to set it up so that my fellow coworkers who are new to linux and terminal in general don't really have to do anything when they want to use Fog to image a set of computers. For my setup I need to DHCP to run. Normally when I need to use fog, before-hand I just run *Sudo /etc/init.d/dhcp3-server start/stop* to get things going. Apparently remembering this command in terminal is too difficult for them to do. So I want to make a startup script that starts DHCP as ubuntu boots. I've never made a start up script before. Can someone help? Or point me in the right direction to figure out how to do this?

I tried using the start-up script application thing under system preferences, but I can't figure out how to give the start-up command root privileges in order for it to run.

---

### Post by Captain Giraffe on 2010-09-22
If your not interested in a .bash_profile (google provides good links early) login script you should check these out:
[http://www.linux.com/archive/feature/114107](http://www.linux.com/archive/feature/114107)
Talks about your question.  The rc#.d directories contains stuff to load at different runlevels.

and
[http://wiki.df.dreamhosters.com/wiki/Ubuntu_Forums_FAQ#How_can_I_make_Ubuntu_execute_a_script_or_program_at_startup.3F](http://wiki.df.dreamhosters.com/wiki/Ubuntu_Forums_FAQ#How_can_I_make_Ubuntu_execute_a_script_or_program_at_startup.3F)

---

### Post by PhilMize on 2010-09-22
Ok thanx!

Basically what I did was created 2 launchers. One is named "Start DHCP" and the other is named "Stop DHCP". Both icons on the desktop. For the commands I just pointed it to the script in the /ect/init.d/ called dhcp3-server and added Sudo at the begining and start/stop at the end of the command. 

So this way when they first boot the machine, all they have to do is click the "Start DHCP" icon, terminal pops up prompting for password input. They type it in, hit enter and there you go! Same goes for the "Stop DHCP" launcher icon.

It's not a fabulous method but it works for now. Thanks! :guitar:

---

