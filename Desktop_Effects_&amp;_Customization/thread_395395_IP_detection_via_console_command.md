---
title: "IP detection via console command?"
date: 2007-03-28
forum: Desktop Effects &amp; Customization
---

### Post by FoolsGold on 2007-03-28
Hi, I've got an interesting question (hopefully).

Is there a way I can get my external IP piped easily to a console command, such that I can exec the output into my Conky script? (If that didn't make sense, I'll explain a bit.)

My ISP give me a dynamic IP. I'm behind a NAT so my internal IP is the usual 192.168.x.x, but of course my external IP is something different, and changes from time to time. This is the IP I'm looking for, the one that you can also get using [http://whatismyipaddress.com](http://whatismyipaddress.com) . I'd like to be able to get this external IP and incorporate into my Conky script, as it would be extremely useful instead of having to load that page all the time.

Is there a easy way already available, or will I be up for some coding? Mucho appreciato.

---

### Post by BungaMan on 2007-03-29
instead use [http://whatismyip.org/](http://whatismyip.org/)

i'm not sure but try something like the following puts it in a document

wget [http://whatismyip.org/](http://whatismyip.org/) -O chooseafilename

and 

wget [http://whatismyip.org/](http://whatismyip.org/) -O -

sends the result to stdout

Then all you need to do is put it in a script at bootup but note that the ip can change while you are online (depends on ISP).  Then you could potentially think you have IP x while it is IP y.

---

