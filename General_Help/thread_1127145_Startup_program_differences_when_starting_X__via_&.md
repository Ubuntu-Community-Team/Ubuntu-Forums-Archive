---
title: "Startup program differences when starting X  via &quot;startx&quot; and &quot;gdm &quot;"
date: 2009-04-16
forum: General Help
---

### Post by uncle-c on 2009-04-16
Hi there,
I have a feeling that this could be an [COLOR="RoyalBlue"]**.xinitrc**[/COLOR] related query, but here goes. 
I wanted to avoid having to login via [COLOR="RoyalBlue"]**gdm**[/COLOR]  when I started up my Ubuntu box. My default runlevel was 2 so using [COLOR="RoyalBlue"]**sysv-rc-conf**[/COLOR] I unselected gdm to run at runlevel 2. I rebooted my machine and I got into standard console login, entered my details and got into a bash prompt. To use [COLOR="RoyalBlue"]**X**[/COLOR] I ran [COLOR="RoyalBlue"]**startx**[/COLOR] to initiate my gnome desktop session. Everything was fine and dandy until I saw a warning on my panel over my volume control icon stating that [COLOR="Red"]**Volume control could not find any elements / devices to control ....**[/COLOR]. Obviously no sound card / audio device was being recognised. I reverted to normal login via [COLOR="RoyalBlue"]**gdm**[/COLOR] and this error was no longer there - the sound card was  shown to be present and correct. The conclusion I draw from this is that there could possibly be some differences in the startup files that were read by the two different X session startup methods. I would like to start my gnome desktop by running [COLOR="RoyalBlue"]**startx**[/COLOR] but what modifications would I need to make to my system (or the .xinitrc file) so it recognises my audio device in the same manner that the [COLOR="RoyalBlue"]**GDM LOGIN**[/COLOR] method does ?

Cheers,
UC

---

### Post by kerry_s on 2009-04-16
in your ~/.xinitrc put "exec gnome-session".

i'm in arch mine looks like this, but i use jwm.

---

### Post by uncle-c on 2009-04-16
Thanks for the help , alas no luck.

---

### Post by kerry_s on 2009-04-16
try putting the same start up programs as in session?
example:
program1 &
program2 &
program3 &
etc... &
exec gnome-session

---

### Post by uncle-c on 2009-04-16
cheers kerry,
It is the "volume control" icon on the panel which is in error state when I fire up X using "startx." I think I may have caused much ambiguity when I said "startup program" in my original post. Does this make any difference ?

Screencap :

[http://i39.tinypic.com/tm5i.jpg]("http://i39.tinypic.com/tm5i.jpg")

---

### Post by kerry_s on 2009-04-16
ah ha, that's that stupid pulse audio thing.
run this in a terminal:
**/usr/bin/pulseaudio -D --log-target=syslog &**

if it works add it to startup.

---

