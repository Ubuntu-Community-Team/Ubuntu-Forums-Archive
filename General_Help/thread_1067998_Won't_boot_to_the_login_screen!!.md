---
title: "Won't boot to the login screen!!"
date: 2009-02-12
forum: General Help
---

### Post by cacde on 2009-02-12
Ok, so I've been personalizing my Ubuntu for about 2 days now, and I rebooted several times and it worked every single time, but when I went to reboot it today it wouldn't load the login screen, it just booted the 1st splash screen, then went to a black screen and the mouse with the spinning circle just stays there (yes i can move it), I already tried resetting the xserver and that doesn't work. Anything else you need like more info, specs just ask sorry I'm a beginner ^_^

---

### Post by kanikilu on 2009-02-12
> **cacde said:**
> Ok, so I've been personalizing my Ubuntu for about 2 days now
A good start would be describing what you've done so far. That might give people a starting point to try to help you.

Do you see any errors in your /var/log/Xorg.0.log file? Or dmesg or syslog, for that matter?

---

### Post by cacde on 2009-02-12
A good start would be to read what I'm saying.... I said I get a black screen after the 1st splash screen does that sound like I can see if I have any errors? I have run file system check or whatever from the recovery mode and it doesn't say anything is wrong. and by personalizations I meant that I just changed the way the desktop looks and stuff like that.

---

### Post by kanikilu on 2009-02-12
> **cacde said:**
> A good start would be to read what I'm saying....
Obviously I read what you wrote, I even took the time to ask some follow up questions, unlike the 15+ other people that viewed the thread. You don't have to be rude, you just didn't provide very much information. If you don't want help, keep up the vague descriptions and the attitude.

> does that sound like I can see if I have any errors?
You obviously know how to go into recovery mode, so do it again, this time go to a root console and check out those log files. It's not rocket science.

> and by personalizations I meant that I just changed the way the desktop looks and stuff like that.
Well, then I guess next time specify that to avoid confusion.

BTW, did you even Google "[ubuntu black screen](http://www.google.com/search?q=ubuntu+black+screen)"? There seems to be a lot of related pages and threads on this and other forums.

---

### Post by cacde on 2009-02-12
You said I obviously know how to get into recovery mode, and if I've been there and found nothing wrong, why ask again? 




it gives me this when I try to restart the x-server: 


Postinst Warning: overwriting possibly-costumised configuration file; backup in /etc/x11/xorg.conf.2009021302747

---

### Post by kanikilu on 2009-02-13
> **cacde said:**
> and if I've been there and found nothing wrong, why ask again?

Ok, so you're telling me you've gone into recovery mode **and** checked those ***log files*** for errors? If so, there is nothing in any of your previous posts that state that. All you said was, and I quote:

> I have run file system check or whatever from the recovery mode and it doesn't say anything is wrong

I didn't ask what "it" said -- whatever "it" is...I suggested you check your **LOGS** for errors, not do a filesystem check ](*,)

Ironic that you would question whether *I* read *your* post :rolleyes:

I'm done with this thread, but if you want to do yourself a favor, for the last time, check your logs. If there really are **no** errors anywhere in the logs, then I can't help you - and judging by the fact that no one else has responded at all...well, good luck with that.

---

