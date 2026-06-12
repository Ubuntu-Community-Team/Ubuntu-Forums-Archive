---
title: "Remote Controlled Info Screen"
date: 2011-09-12
forum: Desktop Environments
---

### Post by frause on 2011-09-12
hello,
yes I'm new... I didn't found any near solution for the following problem which indicates a wrong search by myself - so maybe someone can redirect me.


Scenario:

debi-serv: lighweight debian server (no graphical user interface, not even a monitor)
media-ubi: full powered ubuntu server with all sound, monitors and all media.

so now media-ubi is already remote starting via WAKEONLAN from debi-serv. fine!
Next  I need to show something at its screen - eg firefox running - which is remotely controlled - eg via ssh - from debi-serv. 
I think i need to login a user with desktop interaction but how?
ssh -X could not help as the debi-serv cannot handle any window. so?


More-Info-than-you-need:
debi-serv is the all time powered router which starts media-ubi already, controlling its mpd and raise the music to give me a pleasant wakeup every morning... this works fine (i even control the room-light via usb power switches)
my desired next step is to save commands on debi-serv to let medi-ubi display me the current weather forecast and some news maybe... whatever, but the main point is to get a "x session"?? which has no user interaction BUT a display!

any help welcome :)
thx for reading

---

### Post by frause on 2011-09-13
ok, I will create a specific user on medi-ubi make him auto-login after some minutes and implement a startup script showing to my needs... not so fantastic but it'll work!

---

