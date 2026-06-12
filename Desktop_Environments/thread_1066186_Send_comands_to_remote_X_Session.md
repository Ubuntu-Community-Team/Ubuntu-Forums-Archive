---
title: "Send comands to remote X Session"
date: 2009-02-10
forum: Desktop Environments
---

### Post by nolanpro on 2009-02-10
Hey Gurus!

I've searched and searched but I cant find an answer to this. I want to be able to send shell commands to a running xsession on my ubuntu box (8.10). I don't actually want to VNC anything or even send any GUI at all through SSH.

Heres an example: When I enter
```
$echo $DISPLAY
```
from the terminal in the xsession on the ubuntu box, it shows :0.0 but when I enter it from my remote ssh shell (putty) it is empty. Ideally, i would like to be able to do something like this from my remote ssh connection:
```
$ {voodoo to specify xsession} echo $DISPLAY
```
and it would in fact be sending that to my running xsession and output :0.0.

Ultimately, what I'm trying to do, is start VLC via command line from my SSH on another computer so that it opens and plays on my unix box at home. (will ultimately be controlled with an exec() command from PHP, and possibly cron)

Any help would be very very sweet! I'm open to taking this a whole different direction if necessary. Thanks!!!

---

### Post by nolanpro on 2009-02-11
Anybody? It seems there must be a way to do this. I'll try posting in VLC and X forums.

---

### Post by snova on 2009-02-11
As far as I know, it should be as simple as:

```
export DISPLAY=:0.0
echo $DISPLAY
```

This also works (but only for the one command):

```
DISPLAY=:0.0 echo $DISPLAY
```

I may have misinterpreted your question, though...

---

### Post by nolanpro on 2009-02-11
Your right it really is that simple! I'm almost sure I tried that but it might have been TOO simple and I just overlooked it! THANKS!!!!

---

### Post by nolanpro on 2009-02-11
AAAHHH Actually the secret is to configure 'xhost' to allow remote connections to control X apps.

---

