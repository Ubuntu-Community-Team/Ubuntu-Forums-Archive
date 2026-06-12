---
title: "Time setting changes randomly"
date: 2005-02-01
forum: Desktop Environments
---

### Post by jozmak on 2005-02-01
Hi,

I have just noticed that my time setting occasionally changes. It works for a few weeks ok, then it changes seemingly randomly.
Did anybody experience something like this? 
I wonder how to fix this.
 
Thanks
jozmak

---

### Post by valadil on 2005-02-02
Do you boot into windows at all?  You might want to try rdate.  It gets the time and date from a server and sets your computer to that time.

---

### Post by jozmak on 2005-02-02
Yes, i have a dual boot system.
Could you please elaborate on the rdate term?

thanks

---

### Post by valadil on 2005-02-02
You'll need to install the package rdate.  It should be in your repositories.

You'll also need to find a server to give you the time.  I use a local one.  To reset the time I type:
sudo rdate time.unet.brandeis.edu
And rdate  checks the time on brandeis' time server and sets that to my local time.

You can (ubuntu might do this for you I'm not sure) write a script and put it in /etc/rc2.d that will do that automatically at bootup.

The problem with using rdate is that this doesn't actually solve your problem - it just fixes the time periodically.  Your problem comes from you using gmt or local time.  It's a setting that comes up fairly early in the ubuntu installer and I don't know how to get back to it.  I also never seem to remember which option is which and usually end up guessing wrong, hence my familiarity with rdate.

---

### Post by xurizaemon on 2007-12-10
are you looking for "tzconfig"? (to configure your system timezone)

there's undoubtedly a GUI method too via admin => time something blah blah

---

