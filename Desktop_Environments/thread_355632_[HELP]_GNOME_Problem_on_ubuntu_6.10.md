---
title: "[HELP] GNOME Problem on ubuntu 6.10"
date: 2007-02-07
forum: Desktop Environments
---

### Post by BabyUbuntu on 2007-02-07
[[img]http://upload6.postimage.org/141618/Screenshot.jpg[/img]](http://upload6.postimage.org/141618/photo_hosting.html)

when i log in without internet connection...this message always show ... and it makes my laptop running so slow.. would you please help me to fix my problem? 
NB: my themes, sounds and backround running good

thank you very much for your attention

---

### Post by kevinlyfellow on 2007-02-08
Well, lets see if its a problem with some user settings.  Create a new account and log in to see if you still get that message

---

### Post by kevinlyfellow on 2007-02-08
Your certainly not alone, check out this bug report
[https://launchpad.net/ubuntu/+source/control-center/+bug/61381](https://launchpad.net/ubuntu/+source/control-center/+bug/61381)
some suggestions that I pulled out of the discussions

CHange your theme back to Human
[U]
Make sure that your loopback is set up properly[/U]
     Check you /etc/hosts file
     Check your /etc/network/interfaces file

---

### Post by BabyUbuntu on 2007-02-08
kevin.... thank you verymuch for your advice

i was change my themes. back to human... i was checkd my /etc/hosts file
& /etc/network/interfaces file.. lookback setup already

when i log in... error message not detected but need almost 4 minutes to finished windows manager loading.. now.. what i have to do ??any advice?

thank again

---

### Post by kevinlyfellow on 2007-02-09
Have you tried creating a new user and logging in as the different user?  

Edit: Oh, sorry, it appears I've already made the suggestion.  I found this here [https://launchpad.net/ubuntu/+source/control-center/+bug/59217](https://launchpad.net/ubuntu/+source/control-center/+bug/59217)

> 
Found this on the Ubuntu Forums:

Had the same problem and permanently got rid of it
by adding the following $HOME/.Xsession file:

------------------------------------------
#!/bin/sh
exec gnome-session
------------------------------------------

That solved the problem, but don't ask me why...


---

