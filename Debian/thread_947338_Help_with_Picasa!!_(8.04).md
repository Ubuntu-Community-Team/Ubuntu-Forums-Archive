---
title: "Help with Picasa!! (8.04)"
date: 2008-10-14
forum: Debian
---

### Post by hananias on 2008-10-14
I'm having problems with Picasa also.  At first it was working fine, I loved it...way better than f-spot.  But now When I start it, the Picasa 3 beta splash screen shows up, but then it goes away (as if the program is about to come up) but it doesn't... I uninstall/ reinstalled and still same thing.:confused:
  
I'm running gOS (pretty much ubuntu 8.04 hardy)

Please any help I will appreciated so much.  I actually need this for work:(

---

### Post by Sef on 2008-10-14
>  I'm running gOS (pretty much ubuntu 8.04 hardy)What version of gOS do you have?  While gOS 3.0 is [based]("http://en.wikipedia.org/wiki/Green_OS") on Hardy, it is not the same as it.

Moved to Debian and its progeny forum.

---

### Post by hananias on 2008-10-14
Well my system monitor says 
Ubuntu Release 8.04 (hardy)
Kernel Linux 2.6.24-19-generic
GNOME 2.22.3

Isn't this the same thing??? I'm new to linux, so please take it easy on me.

---

### Post by meganox on 2008-10-14
It's not quite the same thing, maybe you should post on a gOS forum as well.

Try running Picasa from a terminal (Applications -> Accessories -> Terminal in Ubuntu) and see if there's any error output.  I guess the command is just "picasa"
```

# picasa 2>&1 | tee picasa-err.txt
```will send picasa's output both to the screen and a file called picasa-err.txt

What version of Picasa is it?

---

### Post by hananias on 2008-10-14
I have the beta version 3.  Thanks for the reply.  You guys seem to know what you are talking about, so what's the difference between gOS and regular ubuntu?

---

