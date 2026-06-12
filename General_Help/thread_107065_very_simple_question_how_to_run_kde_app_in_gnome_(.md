---
title: "very simple question: how to run kde app in gnome (ubuntu)?"
date: 2005-12-22
forum: General Help
---

### Post by unwoken on 2005-12-22
i have now recovered from the temporary destruction of my x, after blindly using sudo in an attempt to run guarddog...:p 

however, i am now in the situation where despite (my belief that i am) using the correct settings, i am not able to connect to my work VPN (using pptp).  i have read numerous threads by people who have said that firestarter can block this access.

pptp actually tells me that i am connected, but not long after this, my internet connection freezes.  this happens every time, without fail.  from what i have read, this appears to be a firestarter issue.

i am not the biggest fan of firestarter anyway, given that i get an error message regarding it every time i log on, even though i modified sudoers (and added a command to my startup sessions).  i have spent far too much time worrying about my troubles with it, so i am well ready for it to go back from whence it came.... :p 


so, this leads to my question.  can anyone tell me the terminal command i need to enter to run guarddog, given that it is kde and i am in gnome (ubuntu)?

i have read that i need to enter kdesu (eg. 'kdesu guarddog'), but when i try that i get a bash error stating that the command does not exist (or something similar).  do i need to load a particular package to use this command?  i have searched for the answer to this question, but stranegly i can't find it anywhere.

any help will be most happily received!

cheers in advance :)
u.

---

### Post by manicka on 2005-12-22
[QUOTE=unwoken]
i have read that i need to enter kdesu (eg. 'kdesu guarddog'), but when i try that i get a bash error stating that the command does not exist (or something similar).  do i need to load a particular package to use this command?  i have searched for the answer to this question, but stranegly i can't find it anywhere.
u.[/QUOTE]

what about just starting it with sudo in a terminal, it should still work

sudo guarddog

Post the error messages, this will help to solve the problem

---

### Post by unwoken on 2005-12-22
[QUOTE=manicka]what about just starting it with sudo in a terminal, it should still work

sudo guarddog

Post the error messages, this will help to solve the problem[/QUOTE]

thanks for the reply manicka.  i tried that and had problems, so i tried a few other things and finally posted here after getting 'firestarter rage' :) .  

what happened was that it seemed to run ok, but after i had saved my config changes to guarddog, nothing seemed to work.  i couldn't click on menu items or anything.  i logged out hoping that re-logging in would fix the problem, and found that my entire x session was un-startable.  i got a message saying that the session had lasted less than 10 seconds and that i should log into a fail-safe terminal.

it turned out that my .ICEauthority permissions had changed and therefore i could not log in.

if it might help, this is how my .xsession-errors file looked at the time (while it was still broken)


/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "fireball"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/cynopolis:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/cynopolis:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/cynopolis:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:8435): WARNING **: Unable to read ICE authority file: /home/fireball/.ICEauthority


i read around at the time and found a post where somebody said never to use sudo with a kde app.  is that true?  if not, what happened to my .ICEauthority? and will it happen again if i sudo guarddog?

EDIT: there were no other specific error messages given.  while x was down and i did not know the cause, i logged into my second (backup) user, completely removed guarddog, and made changes to my firestarter config in the hope of overwriting any problem changes (i was guessing :) ).  It took the renaming of the ICE file to restart the session, but when i did that, everything was fine (minus guarddog).

thanks.

---

### Post by unwoken on 2005-12-22
ok, i'll try asking another way.

is there anyone out there that uses guarddog with ubuntu (& therefore gnome)?

if so, what command do you use to run it in 'superuser' mode?

if it is sudo, have you experienced any of the problems i did (such as x crashing due to .ICE authority permissions changing)?

how can i avoid this if this?

if not sudo, is there anything else i need to install to to run the command (eg. to run kdesu)?

cheers.

---

### Post by manicka on 2005-12-22
What are the problems with Firestarter? It seems to do an okay job.

How about using gksudo instead of kdesu from an alt-f2 run dialogue

---

### Post by unwoken on 2005-12-22
firestarter in itself does seem to do a reasonable job.

i can get over the constant error messages i get on login due to permission problems.  i spent days trying to sort that out, but attempting to fix firewall error messages is not my favorite thing to do :) (especially when the error message is redundant - it starts as it tells me i have no permission), so i ended up just ignoring the message.

the real problem i have with it, is that i have a need to access my work VPN from home at times.  i mentioned some of it previously, but my internet freezes when i connect to the VPN, and others have described this as being caused by firestarter.

i would prefer to have an active firewall.  i know that others have argued that this is unnecessary, but i would still prefer it (with a gui), maybe i'm scarred by my win$ experience :)  

at the end of the day, i would prefer not to use XP to access my VPN, but it has never caused me any issues, and always connects perfectly.

this is just an attempt to escape the M$ dependency :)

.....

EDIT: manicka, can you describe the alt-f2 dialogue process?  is it as simple as it sounds?  do i just hit 'alt-f2' and enter 'gksudo guarddog' in a box which pops up?  i've never tried that before.

---

### Post by detyabozhye on 2005-12-22
[QUOTE=unwoken]EDIT: manicka, can you describe the alt-f2 dialogue process?  is it as simple as it sounds?  do i just hit 'alt-f2' and enter 'gksudo guarddog' in a box which pops up?  i've never tried that before.[/QUOTE]
Yep, that's all you do.

---

