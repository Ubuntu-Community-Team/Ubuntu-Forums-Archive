---
title: "Teamviewer screen not refreshing after login"
date: 2012-11-27
forum: Desktop Environments
---

### Post by Stijndg on 2012-11-27
Hey Guys,

Been having this problem, i installed teamviewer7 on my Ubuntu 12.04.1 Headless server, it runs fine and i can connect to it via my other pc at work or at home but is does not update the screen.

When i VNC into my server and then teamview in to it at the same time i can see my mouse moving etc in the vnc session so teamviewer does send my inputs but the screen is static.

Since teamviewer is the only app that passes through my work's firewall i'd like to get it fixed.

I think it has something to do with how i start my xfce session, i have a feeling i'm starting it wrong.

some log files:

wine log:
[http://paste.ubuntu.com/1391777/](http://paste.ubuntu.com/1391777/)

teamviewer log:
[http://paste.ubuntu.com/1391780/](http://paste.ubuntu.com/1391780/)

xstartup file how i launch my vnc session on boot:
[http://paste.ubuntu.com/1391783/](http://paste.ubuntu.com/1391783/)

Any ideas onhow to fix this would be most welcome [-o<

Kind regards,
Stijn

PS: If more log files are needed plz let me know

---

### Post by anms on 2013-04-11
Hello,
I had the same problem and this solved it:
On client side, go to "view/quality/custom settings" and turn on the option "better compatibility".
Regards T.H.

---

