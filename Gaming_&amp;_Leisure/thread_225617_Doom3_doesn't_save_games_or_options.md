---
title: "Doom3 doesn't save games or options"
date: 2006-07-30
forum: Gaming &amp; Leisure
---

### Post by shookmon on 2006-07-30
I've got Doom3 running, but it doesn't save any options I change (like screen res, speakers set to stereo) and I can't save games.

Any ideas?

Running Dapper with all video and audio working correctly.

Thanks!!!

shookmon

---

### Post by jpkotta on 2006-07-30
I think Doom3 saves that stuff in ~/.doom3 (I installed the demo about a year ago and I'm not exactly sure anymore).  Do you have permission to write to that?  

I installed GoogleEarth a while ago and it gave me the option of running it immediately after install.  The problem was that I installed as root, and it ran as root the first time, but because I used sudo, the environment was setup so that $HOME was /home/jpkotta, not /root.  It created files in my home owned by root, and wouldn't work when I ran it as a user.

---

### Post by shookmon on 2006-07-30
Ok, the scenario you talk about sounds like what I probably did, so I checked and sure enough the .doom3 folder was set to root:root.

So I ran "sudo chown -hR myUser: /home/myUser/.doom3" and all is well.

Thanks for the help!!!!

shookmon

---

