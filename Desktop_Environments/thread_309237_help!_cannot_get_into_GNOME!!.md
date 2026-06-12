---
title: "help! cannot get into GNOME!!"
date: 2006-11-29
forum: Desktop Environments
---

### Post by kakyoism on 2006-11-29
My machine: dapper x86 on AMD64

big problem!

During last session, I believe that the only
change of the system I made is that I installed
gizmo and its dependencies (bonjour, libsipphone..)

after that, KDE session is fine to get in but the GNOME
session shows this:
After the splash is seen and the loggin music is heard,
the panels are flickering forever with a few
start-up apps I set beforehand such as amule flickering as well.
And they won't show up. I got the dialog asking if I wanna
force quit the amule though, but that didn't work either.
The only way left was to shut down the machine brutally.

Any idea?
Thanks.

P.S. was it not a good idea to specify start-up apps?
This makes GNOME look so vulnerrable:(...

Beinan

---

### Post by kakyoism on 2006-11-29
help, please!

---

### Post by frodon on 2006-11-29
You can always use the gnome safe session to remove amule from start-up apps list then retry to login as usual to see if it's the problem.

Just in case you don't know how to use the safe session :
In GDM (the login screen) click on option and choose the safe session then login.

---

### Post by kakyoism on 2006-11-29
I tried that actually and it won't let me in either, same syndrome as the normal GNOME session.

Any idea?
Thank you!

---

### Post by kakyoism on 2006-11-29
please help!!

---

### Post by kakyoism on 2006-11-29
please help

---

### Post by thedman on 2006-11-29
I had a similar issue, except it would hang on the splash page about half way through.  I could get in via the gnome safe login however.  Don't know if this will help, but it fixed my problem...

I deleted the "session" file from the hidden directory ./gnome2 in my home directory, and restarted my Xsession.  The session file was recreated and everything returned to normal.

Make a backup of the file and try, couldn't hurt.

Thedman.

---

### Post by kakyoism on 2006-11-29
Thanks, I'm now on my kubuntu-desktop. I tried all that but I didn't see anything that says "session" that can't be deleted.

But I did find the file ".xsession-errors" under my home folder REALLY suspicious. There are two versions after a successful KDE session was launched and a failed gnome session

1) The .xsession-errors after this kde session launched is here:
[http://www.music.mcgill.ca/~damonli/temp/xsession_error_kde.txt]("http://www.music.mcgill.ca/~damonli/temp/xsession_error_kde.txt")

2) .xsession-error after a failed gnome session:
[http://www.music.mcgill.ca/~damonli/temp/xsession_error_gnome.txt]("http://www.music.mcgill.ca/~damonli/temp/xsession_error_gnome.txt")

Please help me

I'd appreciate any help on this, because after a few week's struggle, I thought I finally got more comfortable with Ubuntu, but this makes me feel that maybe I'm not yet ready for this Windows-2-linux migration... If this can be solved through the community help I'd be more confident staying on the Linux battlefield; otherwise I cannot affort the time ...

Thank you very much!

Beinan

---

### Post by kakyoism on 2006-11-29
up and please help

---

### Post by kakyoism on 2006-11-30
help!

---

### Post by juniper1982 on 2006-11-30
i would recommend getting rid of the apps you installed that broke this in the first place.

---

### Post by kakyoism on 2006-11-30
help~~~

---

### Post by frodon on 2006-11-30
Please do not bump your thread every 2 or 3 hours to make it appear on the top of the list, be patient or your thread will be closed

---

### Post by kakyoism on 2006-11-30
to juniper1982

I did uninstall gizmo in the first place...
and along with bonjour and libsipphoneapi

still the same ....:(

---

