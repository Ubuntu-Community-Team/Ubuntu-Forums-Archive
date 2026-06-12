---
title: "Suspend stopped working"
date: 2009-04-09
forum: General Help
---

### Post by psychoelf on 2009-04-09
Ok, so suspend was working on my laptop after I turned off compiz, visual effects and made sure my swap was larger then ram.  Now all of the sudden it stopped working.

It goes to sleep fine, and when I wake it up it looks like its going to give me the login, but the prompt never appears.  The background is there like normal, but nothing else and the keyboard does not respond.  This is with kernel 2.6.27-11-generic.

I tried booting with kernel 2.6.27-7-generic and I got a step further by having a login prompt pull up.  I typed in my user/pass and after hitting enter the window disappeared and just the background stayed.  No response from keyboard.

I've also tried sudo gedit /etc/default/acpi-support and changing this:

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true  <---to false, but it didnt help.

Any ideas?

Running on a Gateway 6850FX with ATI 2600HD.

Thanks!

---

### Post by psychoelf on 2009-04-09
Ok, I tried disabling all the "extras" I have.  No screenlets, cairo dock, conky.  Changed to a standard theme.  Disabled compositing through metacity as well.  Still the same outcome.  I get the login on resume, punch in my password and thats it, still stuck.

---

### Post by psychoelf on 2009-04-12
So....after reinstalling and going step by step to find out what went wrong...it was the GL screensavers...sucks because I love Hufus smoke.  Basically I installed a program, then tested suspend and then went on to the next program or change.  Will ATI ever work well with Linux?

---

