---
title: "E17 crashes at start"
date: 2010-05-16
forum: Desktop Environments
---

### Post by bootninja on 2010-05-16
I have ubuntu Lucid installed in a virtualbox vm with guest utils addon installed.  everything works great, but I wanted to try e17 since I've heard so many great things about it.  

I used a thread on these forums to install from svn, and after a couple hours mucking with dependencies I finally got it installed.

I created the e17.desktop file and it shows up in gdm, but when I try to log in to e17, I get a flickering screen and it crashes back to gdm.

I haven't yet tried starting it from command line because I can't figure out how to completely kill gdm and the x server.  CTL ALT BACKSPACE seems to have been deprecated/disabled.

Any help y'all can provide will be appreciated, and if you need further information I'll be happy to provide it.

---

### Post by portentum on 2010-05-16
Does /var/log/Xorg.0.log have any information about the e17 crash?

As for stopping GDM and X, a quick way would be to
```

sudo service gdm stop
sudo pkill Xorg

```

The way I would start e17 from there would be to alter ~/.xsession to contain
```
exec enlightenment_start
```
Then startx and hope everything works.

(I assume enlightenment_start is the e17 start command from a look at some Arch documentation, if not I apologize, I haven't tried out e17 in a while)

---

### Post by bootninja on 2010-05-16
Thanks for the quick response.  that at least gives me somewhere to start.

my xorg log is at [http://www.mack-attack.com/Xorg.0.log.old](http://www.mack-attack.com/Xorg.0.log.old)

this should be the one from the last failed start of e17

when I killed the xserver and ran exec enlightenment_start, i get the following output:

[http://www.mack-attack.com/enlightenment_start.txt](http://www.mack-attack.com/enlightenment_start.txt)

when I run exec enlightenment_start from gnome, I get  the following:

[http://www.mack-attack.com/enlightenment.txt](http://www.mack-attack.com/enlightenment.txt)

---

### Post by portentum on 2010-05-16
Well, I see a segfault there at the end but I have no idea what might have caused it. Hmmm.

As for running exec enlightenment_start, well, if you don't have an X server running e17 can't put itself on a display and will crash like that, which is why I recommend adding exec enlightenment_start to the ~/.xsession file (you can simply comment out anything currently there with #) and then using the startx command. startx will start the X server, then read the ~/.xsession file and start e17 itself.

As for the log from within Gnome, I'm not really certain what's going on there. I'm going to assume it has to do with e17 simply not being happy about an attempt to be started from within another desktop environment for now. :???:

If I misunderstood and you did what I described above with the ~/.xsession file already, sorry, and if not - mind giving it a try? I can try to explain a little better if it's still unclear.

---

### Post by stanca on 2010-05-16
Have you tried these packages?
 [http://packages.enlightenment.org/ubuntu/pool/](http://packages.enlightenment.org/ubuntu/pool/)

---

### Post by bootninja on 2010-05-17
portentum:

     My system doesn't seem to have a ~/.xsession file.  I'll go ahead and create one.  To be clear, are you saying all it needs in it is one line,

```

exec enlightenment_start

```

since startx is what calls .xsession?

---

### Post by portentum on 2010-05-17
> **bootninja said:**
> portentum:

     My system doesn't seem to have a ~/.xsession file.  I'll go ahead and create one.  To be clear, are you saying all it needs in it is one line,

```

exec enlightenment_start

```

since startx is what calls .xsession?

Correct, just the one line. Let me know how it turns out.

---

### Post by bootninja on 2010-05-17
segfault :)


When I created the .xsession file, and ran startx, the x server would not start.

here's the new log, which I believe will be the same as the last one I posted.

[http://www.mack-attack.com/Enlightenment_log.txt](http://www.mack-attack.com/Enlightenment_log.txt)

---

### Post by bootninja on 2010-05-17
could this problem have something to do with the fact that I can't seem to find an xorg.conf file?  or has that been deprecated since the last time I was mucking around with X?

---

### Post by portentum on 2010-05-17
> **bootninja said:**
> segfault :)


When I created the .xsession file, and ran startx, the x server would not start.

here's the new log, which I believe will be the same as the last one I posted.

[http://www.mack-attack.com/Enlightenment_log.txt](http://www.mack-attack.com/Enlightenment_log.txt)

Hmmm, yes, it's looking like you just got a bad svn revision that's segfaulting when it starts. :???:
I'd say either try updating to the latest revision, assuming it has been updated since, or possibly an older revision - otherwise, those packages linked above by stanca might be the way to go.

Assuming everything compiled ok and the particular svn revision is good, it should have started right up.

> **bootninja said:**
> could this problem have something to do with the fact that I can't seem to find an xorg.conf file?  or has that been deprecated since the last time I was mucking around with X?
Ubuntu doesn't seem to use xorg.conf anymore, as it's not necessary. I prefer to maintain one simply because I'm stubborn and set in my ways, but that it's missing shouldn't be causing any problems, no.

---

### Post by bootninja on 2010-05-17
yeah, I looked at the packages he linked and they don't seem to have any for lucid.  will it do bad things to my system to try and install the ones for jaunty?

---

### Post by portentum on 2010-05-17
Actually, if you look below where it says References, they do appear to have lucid packages and simply haven't updated the list above. It wouldn't hurt to try to add ```
deb http://packages.enlightenment.org/ubuntu lucid main extras
```
to see if the repo is in fact there.

(you can click lucid down there and browse through the lucid packages, giving download links such as [this one]("http://packages.enlightenment.org/ubuntu/pool/lucid/binaries-20100123/main/e/e17-data_0.16.999.063+svn44144-1_all.deb") for e17-data_0.16.999.063+svn44144-1_all.deb)

---

### Post by bootninja on 2010-05-17
Guess I didn't look hard enough.  I'll try that, and if it doesn't work, maybe I can update the svn installation.

thanks for the suggestions.

---

