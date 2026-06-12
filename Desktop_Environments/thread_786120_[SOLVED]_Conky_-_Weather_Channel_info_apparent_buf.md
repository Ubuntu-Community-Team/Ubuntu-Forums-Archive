---
title: "[SOLVED] Conky - Weather Channel info apparent buffer overrun"
date: 2008-05-07
forum: Desktop Environments
---

### Post by infraction on 2008-05-07
Thank you in advance.  I have an xslt script to feed info from the weather channel to my Conky display.  This script was fine under Feisty, but broke immediately under Hardy.  There is no question in my mind that the problem is due to a buffer size problem, but I cannot fix it.

[COLOR="Red"]First, has anyone seen a change in the Weather Channel DTD that might cause this?

Next, has something changed in 'xsltproc' with Hardy?

Last, I'm using CURL....has anyone noticed anything weird with that?

Again, thank you for even reading this.  Any and all responses are truely appreciated.  I am lost on this one.
[/COLOR]
Take Care!

5/11/2008 - 
OK, after additional research I still believe this is a buffer size problem but it is Conky and/or Torsmo that has the problem.  Please disregard the text in 'Red' above....I think that is junk.  My 'weather.sh' script that Conky executes via it's 'execi' command works flawlessly from the command line, yet within Conky only a portion of the output is displayed.  I no longer suspect Curl or Xsltproc at all.

Knowing nothing about Torsmo, I could seriously use some guidance.  I intend to do more research, but any and all insight from the community would be appreciated.  Should you need script(s) and/or screen shots posted I would be happy to do so.  I am stuck at this point......please help!!!

Again, thank you all....Take Care!


5/16/2008
Solution was to add the following configuration variable to .conkyrc.......

text_buffer_size 1024

Apparently the default value is 128.

---

