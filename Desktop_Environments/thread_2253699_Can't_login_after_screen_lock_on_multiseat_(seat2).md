---
title: "Can't login after screen lock on multiseat (seat2)"
date: 2014-11-21
forum: Desktop Environments
---

### Post by charlie101 on 2014-11-21
Hi

 
 
 I'm running 14:10 with systemd and multiseat.
 I have two seats; a master and one additional (seat2).
 I can log in and out repeatedly on both seats.  
 However, if I use the screen lock or it activates after a timeout I can't login again.
 This is only an issue on seat2 not on the master.
 The login dialogue comes up and I enter the password only to receive the 'Failed to start session' message.
 
 
 I originally installed gnome with gdm  then switched to unity and lightdm.  
 Unfornately lightdm didn't work too well so I switched back to gdm and gnome.
 Shortly afterwards I noticed this problem.
 I don't know if it was there before.  
 This is a new install so I don't have any history to draw on.
 
 
 I can't find anything in the logs but then I don't know where to look other than syslog, X.log and /var/log/gdm.
 
 
 Any suggestion on what might cause this or how to go about debugging it would be much apprecaited.
 
 
 Thanks in advance.
 
 
 Charlie101

---

