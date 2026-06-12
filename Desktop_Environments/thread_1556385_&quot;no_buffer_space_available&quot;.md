---
title: "&quot;no buffer space available&quot;"
date: 2010-08-19
forum: Desktop Environments
---

### Post by chitowner2 on 2010-08-19
Hello All;

I am getting this error message in a bash shell trying to open ssh. I have rummaged about on google looking for useful info, but nothing appropriate has turned up. 

I am not looking for a resolution so much as intending to open a forum for folks to discuss this issue because I am quite sure that if I reboot, the issue will go away as this is the first time I have seen it and it is on a stable install that's been running for over a year. 

What this seems to be: Something blocking access to ALL _network_ functions. Internally all seems to be OK.

What this IS NOT: This is not a problem with CPU, MEM or swap! All of those parameters are quantitatively within nominal limits, eg 50% or less of available. It is also not a problem (as far as I can tell) with my network manager app, router or other hardware. 

Clues: The error is given in a bash shell when I try to open ssh. NMAP identifies only 'self' but does not report "host unreachable" or similar. Other hosts report "broken pipe", "connection closed" or "connection timed out" when trying to connect to the PC in question. 



Background: This is a system running karmic/kde4 with only a ra0 (wireless) connection to a router. (I can use eth0 in a pinch but I don't think that's relevant here.) I am using WICD for network connections.

So folks, chime in with your comments. Let's see what you have to say.

CT
:guitar:

---

