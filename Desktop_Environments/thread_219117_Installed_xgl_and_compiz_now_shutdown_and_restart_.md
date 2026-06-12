---
title: "Installed xgl and compiz now shutdown and restart are gone"
date: 2006-07-19
forum: Desktop Environments
---

### Post by chadk on 2006-07-19
I click on the red power button icon and I have the top three options (change user, etc) but on the bottom all I see is "SLEEP" or "SUSPEND" I don't see Shutdown or Restart any longer?

---

### Post by goobers on 2006-07-19
Yeah, that happened with me. You can just log out and then on the logon screen click the bottom left menu and shut down from there...

Not really a solution I know :p

---

### Post by chadwick359 on 2006-07-19
It actually sounds to me like you aren't launching your desktop/Xgl through gdm, so Gnome can't interface with the shutdown scripts the way it normally does. 

('sudo reboot' or 'sudo shutdown' from a term work too.)

---

### Post by hotani on 2006-07-19
I got the same thing. It's from setting up compiz/xgl to run as a session rather than editing the .Xsession file which would make it load every time. I'm probably going to go back and do it that way.

Here's a HOWTO that uses the .Xsession method: 
[http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)

---

### Post by hotani on 2006-07-20
Don't mind me...

I tried that method and it didn't work. Still missing the buttons. I like the buttons. Can I have them back please? 

After 5 installs of Compiz on 5 different machines, I still haven't kept it on any of them. They are all back to metacity now because I couldn't get it to work correctly. On top of that, each install is different, and changes daily it seems.

---

