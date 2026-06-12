---
title: "setting up a 14&quot; wide screen (1280*768)?"
date: 2005-12-25
forum: General Help
---

### Post by tsr on 2005-12-25
Hi!

Sorry if this has been fixed before, but I couldn't find the solution neither on the forums or the wiki (I've been able to reconfigure Xorg with dpkg-reconfigure, but it doesn't solve the problem).

Currently my screen (backed by the device: "Intel Corporation 82852/855GM Integrated Graphics Device") runs in 1024*768 wich makes everything look a bit "fat", dont like :smile: 

My computer (laptop) is an "Amitech Freenote 5270 14" Wide" (I haven't found any information about this brand anywhere on the web conserning Linux, but the install wen't really smooth (apparently it's just a bunch of Intel suff in a nice portable box!)

Any help would be appriciated (I'd hate to skip using 20% of my screen - which is my current best shot at the moment).

Greets, tsr

---

### Post by sciurus on 2005-12-26
Have you tried manually adding that resolution to your xorg.conf? Just a guess. E.g.
```
SubSection "Display"
     Depth           24
     Modes           "1280x768" "1024x768" "800x600" "640x480"
EndSubSection
```

---

### Post by tsr on 2005-12-26
Ok, so I've done the whole 855resolution-thing that's been mentioned in a bunch og threads. Things are a bit better now:

I get the 1280x786 resolution that I want for the login-screen. But after the login the screen goes to a fattened version of 1024x786. What can I do to help you help me?

Also I suspect that I need to allocate some memory somewhere for the integrated graphics card. How would I do that?

/tsr

---

### Post by tsr on 2005-12-26
Ok, so I've done the whole 855resolution-thing that's been mentioned in a bunch og threads. Things are a bit better now:

I get the 1280x786 resolution that I want for the login-screen. But after the login the screen goes to a fattened version of 1024x786. What can I do to help you help me?

Also I suspect that I need to allocate some memory somewhere for the integrated graphics card. How would I do that?

/tsr

---

### Post by tsr on 2005-12-26
Ok, so now I realised that if i change the screen resolution to something like 800x600 and use that then I'll have the option to change to 1280x768.

Wierd, but it works, any hints o permanenting this?

/tsr

---

