---
title: "Flash/Firefox Gaim sound issues"
date: 2006-05-29
forum: Desktop Environments
---

### Post by gearshifter on 2006-05-29
I know many people have sound issues with flash/firefox but all sound works fine on the computer I'm describing, except when Gaim starts beeping and making sounds.  It seems like there is an also-oss/gaim issue making flash in firefox stop making sounds whenever a sound interferes from gaim.  It may also stop working from other system sounds.  None the less does anyone have any ideas to fix this issue?  

Thanks!

ps.  i've tried alsa-oss and adding it to the rc file (i added it to a blank file since no file actually existed).  I've tried numerous other forum suggestions.  I'm open to more :mrgreen: 


Thanks!
Jason

---

### Post by iamsobored0056 on 2006-05-29
if you are using firefox 1.5 edit last line of /usr/bin/firefox

```
sudo gedit /usr/bin/firefox
```

then do this to the last line (add aoss after exec):
Code:

```
exec_verbose aoss ${MOZ_PROGRAM} "$@"
```

hope this helps

---

### Post by Whoopie on 2006-05-29
Hi,

the right way would be to edit /etc/firefox/firefoxrc.

Mine looks like this:
```

# which /dev/dsp wrapper to use
FIREFOX_DSP="aoss"
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See https://launchpad.net/malone/bugs/29760.

```

Best regards,
Whoopie

---

### Post by gearshifter on 2006-05-29
great!  I really appreciate your help.  so far it's working!  If i have anymore issues i'll find this thread and post back!


once again thanks!

---

### Post by cbudden on 2006-05-30
I am using the official firefox from mozilla.com, and adjusting the /etc/firefox/firefoxrc file does not seem to help flash sound work through aoss, but it is working with the ubuntu build of firefox.  How can I get it to work using the install I have in /opt/firefox/ ?
Thanks

---

### Post by gearshifter on 2006-05-31
alright, the aoss in /usr/bin/firefox is giving my troubles.  it is causing firefox to freeze and making me force quit.   It was allowing both gaim and firefox to use sound at the same time.. anyone know why it's freezing?  aoss in firefoxrc isnt working sadly.

---

### Post by gearshifter on 2006-06-06
i am still having the same issue wtih sound.  it seems like all the sounds mesh together, sadly when it comes to firefox and gaim.  eitehr one sound or the other is not working.

---

### Post by shuttleworthwannabe on 2006-06-06
I installed [COLOR=Red]alsa-aoss[/COLOR]
then added a prefix [COLOR=Blue]aoss firefox [COLOR=Black]to launch firefox (or epiphany or opera, which ever applies). Flash and simulataneous sound in GAIM, Media players works.
important: make sure you change the sound device to ALSA (on everything that has this option)[/COLOR]
[/COLOR]

---

### Post by gearshifter on 2006-06-06
it seems that when i do that, the firefox page will stop responding all together.  This causes me to force quit the page.

---

