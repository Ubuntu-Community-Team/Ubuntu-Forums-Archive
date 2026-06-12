---
title: "Problems with VNC"
date: 2008-05-04
forum: Desktop Environments
---

### Post by starfry on 2008-05-04
Hello, I am trying to use a VNC server in two ways:

(a) to gain "remote desktop" access to the console desktop (set up through the "System->Preferences->Remote Desktop" and discussed here: [http://howtoforge.com/configure-remote-access-to-your-ubuntu-desktop](http://howtoforge.com/configure-remote-access-to-your-ubuntu-desktop)

(b) to gain access to a second session that is independent of the console screen as discussed here: [http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

I can get both to work, however I have problems:

If I boot my machine and log in to the console desktop, I can then go to another machine and use a vnc client to access it as ":0". I can also access a second session as ":1".

If I log out of the console desktop, I can not access it via vnc again unless I re-boot and log in at the console again first. What happens instead is attempting to connect to vnc session :0 gets the session at :1 if a session exists. If a session does not exist on :1 then I get "unable to connect to host: connection refused(111)". Physically logging in on the console desktop again makes no difference.

If my attempt to connect to session :0 and get session :1 the performance is really bad, but it I connect directly to session :1 the performance is fine.

Furthermore, I have keyboard problems: I use mrxvt and that app uses the key sequence shift+ctrl+number to start a new tab but I don't think vnc sends shift+ctrl.

I'd appreciate anyone helping me
(a) get access to the console session after logging out
(b) resolve the keyboard problems

And any general pointers to make vnc work right...

Thanks!

---

