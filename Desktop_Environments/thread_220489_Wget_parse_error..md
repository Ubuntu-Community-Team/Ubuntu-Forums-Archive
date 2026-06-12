---
title: "Wget parse error."
date: 2006-07-21
forum: Desktop Environments
---

### Post by DeemanXu on 2006-07-21
Hi guys.

I've meesed up somewhere, and for that reason i believe that my 'wget' function no longer, ermm....functions.

No matter which 'wget' i try, i get the same old error:

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.

It's worked fine up until today....dunno what's gone wrong to be honest.

Am connected on a Network with WinXP SP2 as the host.

I've checked the network settings ( System/Administration/Networking), and everything adds up there. 
Could this be a config issue with wget ?

Many thanks, Dee :D

---

### Post by philippe_carlo on 2006-07-21
I do not think that this is a valid URL.

---

### Post by DeemanXu on 2006-07-21
It happens irrespective of which wget url i use.

It could be :

wget [http://www.doeweling.com/files/ubuntu/amsn/tcl8.5_8.5.0-1~neto3_i386.deb](http://www.doeweling.com/files/ubuntu/amsn/tcl8.5_8.5.0-1~neto3_i386.deb)

Or it could be:

wget [http://netosoft.no-ip.org/Ubuntu/breezy/amsn/amsn-plugins_0.95+cvs20060325-1~neto1_i386.deb](http://netosoft.no-ip.org/Ubuntu/breezy/amsn/amsn-plugins_0.95+cvs20060325-1~neto1_i386.deb).

The end-result is always the same: 
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name

I know both of these are from the 'beautifying amsn thread', i was just using them as examples.

---

### Post by DeemanXu on 2006-07-21
Anyone ? :(

---

### Post by Johnathon on 2006-07-21
sounds like a network error *possibly* I'm fairly new to linux/ubuntu...

have you got a proxy server configured somewhere?

You could also try "wget --help" or "man wget" to read up on wget, and see if you need to set an option.

---

### Post by DeemanXu on 2006-07-21
No, i'm not on a proxy, or at least i don't think i am. In Firefox, for instance, it's set to auto-detect proxy settings for this network. Ubuntu itself is automatically configured, so, even if i was, i wouldn't have a clue as to the settings.

---

### Post by DeemanXu on 2006-07-22
No one else with any ideas ? :(

---

### Post by SimonJW on 2006-07-22
This happens to quite a lot of people. I've yet to get a definitve answer as to why, but a lot of command line based apps seem to have problems with proxy settings.

You can work around it by running wget with the --no-proxy option

---

### Post by ScottKidder on 2007-09-18
/etc/wgetrc

uncomment the use_proxy option, that fixed this for me and also the issue with installing msttcorefonts

---

### Post by monestri on 2007-10-04
Thanks I just tried this and I confirmed it works. 

```
sudo gedit /etc/wgetrc
```

uncomment use_proxy and change the value to off.

---

