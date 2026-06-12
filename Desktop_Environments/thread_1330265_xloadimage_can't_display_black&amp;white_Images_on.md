---
title: "xloadimage can't display black&amp;white Images on Ubuntu Desktop"
date: 2009-11-18
forum: Desktop Environments
---

### Post by smuggman on 2009-11-18
Hello all,

my problem is that " xloadimage " can't display black&white images (1bit color depth) properly. When i display such an image i can only see a black filled area where the image should be.

I have tried Kubuntu/Ubuntu 9.10 and Ubuntu 9.04 and only see black. 

I also tried Knoppix 6 and Debian 5 and some other Distros - anything fine. So i think it's an ubuntu specific problem.


Can anyone help?

---

### Post by smuggman on 2009-11-20
Update:

I have found out, that Debian 5 (Install Version) also doesn't work - i have tried "Debian Live" -> that worked.

Further i have found out, that the image is shown (on a high class monitor you can see darkdarkgrey on black) so i think it's "only" a wrong background color selected (black instead of white).

Mhh thought "-background white" can do the job. It doesn't work -> google some time i found a bug from year 2002 which i think is very similar to my problem: 
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=131423](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=131423)

Interessting: On XDesktops where the Background is correct i can change all colors wihtout any problem.

Interessting 2: On dektops xli isn't working i have noted an extra row ```
Using DirectColor visual
```


Can anybody help me?

---

