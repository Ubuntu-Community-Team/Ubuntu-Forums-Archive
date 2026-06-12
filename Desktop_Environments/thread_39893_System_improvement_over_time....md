---
title: "System improvement over time..."
date: 2005-06-06
forum: Desktop Environments
---

### Post by nemik on 2005-06-06
Sorry the topic is so vague but I am having trouble describing what i'm looking for in a concise manner.

i use my ubuntu box primarily as a SMS "server." i have a phone hooked up to it via serial port and a program (smstools) that i run from root terminal that queries the phone for new SMS messages every 10 seconds. if it finds one, it does a task.

now i plan to put this into 'production' use but am having problems after it running for more than ~16 hours. the permissions or something get screwed up. it can no longer write files (even in the root terminal) to the /var/spool/... folder it needs to. trying to load any of the 'GUI' programs such as firefox or the file explorer doesn't work, and i can't even delete icons from the 'desktop' because of some permission problem.
i then have to reboot for everything to be fine.

so i'm hoping i can maybe improve this by loading ubuntu without GNOME and just booting it with root console. how can i do this? or is there maybe a better solution to my problem?

thank you all for any suggestions you may have!

---

### Post by benplaut on 2005-06-06
[QUOTE=nemik]Sorry the topic is so vague but I am having trouble describing what i'm looking for in a concise manner.

i use my ubuntu box primarily as a SMS "server." i have a phone hooked up to it via serial port and a program (smstools) that i run from root terminal that queries the phone for new SMS messages every 10 seconds. if it finds one, it does a task.

now i plan to put this into 'production' use but am having problems after it running for more than ~16 hours. the permissions or something get screwed up. it can no longer write files (even in the root terminal) to the /var/spool/... folder it needs to. trying to load any of the 'GUI' programs such as firefox or the file explorer doesn't work, and i can't even delete icons from the 'desktop' because of some permission problem.
i then have to reboot for everything to be fine.

so i'm hoping i can maybe improve this by loading ubuntu without GNOME and just booting it with root console. how can i do this? or is there maybe a better solution to my problem?

thank you all for any suggestions you may have![/QUOTE]

i think there is a timeout on sudo... if that's what you're using right now.

To go into a root console, first actvate the user:

System>Admintration>Login Screen Setup>[tab]Security>Enable Root login

And then, login using GDM with the root account, and for Session, choose "failsafe terminal"

Just curious... what are you doing with an SMS trigger?

---

### Post by nemik on 2005-06-06
[QUOTE=benplaut]i think there is a timeout on sudo... if that's what you're using right now.

To go into a root console, first actvate the user:

System>Admintration>Login Screen Setup>[tab]Security>Enable Root login

And then, login using GDM with the root account, and for Session, choose "failsafe terminal"

Just curious... what are you doing with an SMS trigger?[/QUOTE]
 sudo?....not familiar with it so don't know if i'm using it. sorry i'm kind of a noob to linux, installed it last week and just wrote my first shell script this weekend to handle the SMS's!

as for the for the SMS trigger, i extract the phone number that sent the SMS as well as the message they sent and pass the both of them as variables via URL via cURL to a php script i wrote. from there i can do a lot with it.

---

### Post by nemik on 2005-06-06
[QUOTE=nemik]sudo?....not familiar with it so don't know if i'm using it. sorry i'm kind of a noob to linux, installed it last week and just wrote my first shell script this weekend to handle the SMS's!

as for the for the SMS trigger, i extract the phone number that sent the SMS as well as the message they sent and pass the both of them as variables via URL via cURL to a php script i wrote. from there i can do a lot with it.[/QUOTE]
 btw, benplaut, i just tried your instructions and while everything works, it still says "terminal emulator" in the window before logging into it. is there any way to get to the pure terminal?

---

