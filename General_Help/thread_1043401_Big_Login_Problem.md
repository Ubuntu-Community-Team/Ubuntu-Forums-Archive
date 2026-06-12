---
title: "Big Login Problem"
date: 2009-01-18
forum: General Help
---

### Post by nothingtoprove on 2009-01-18
Been using Ubuntu for about six months now with no significant probs.
I use it for the family laptop and for web/email/office it does it's job more reliably than Windows.

However...

I'm not at all technical so have never had to step into the world of the terminal, until today.

I was basically trying to amend a file (as described on the web) and had to use the terminal.

The upshot is that I've moved my /home folder and now can't login.

I'm logged in on my wife's account who has no admin (su?) privileges so I can't seem to rectify my major cock up.

My /home folder (paul) is now in /etc/udev/rules.d

Any help gratefully received!

---

### Post by taurus on 2009-01-18
Boot into recovery mode from GRUB menu and move your $HOME back to /home.

```
mv /etc/udev/rules.d/paul /home
ls -la /home
shutdown -r now
```

Otherwise, just post the output of this command.

```
ls -la /etc/udev/rules.d
```

---

### Post by nothingtoprove on 2009-01-18
Phew! Thanks.

I'd like to see MS give that kind of response time for free on a Sunday evening.

It's a shame that Ubuntu/Linux is still reliant on a certain degree of coding - as soon as it's free from that it can maybe truly get to the masses.

Many, many thanks again.

---

