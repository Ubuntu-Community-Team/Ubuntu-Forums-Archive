---
title: "Google Earth starts to open, disappears"
date: 2009-04-20
forum: General Help
---

### Post by 440roadrunner on 2009-04-20
I thought I installed Google Earth using these instructions:

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

running Ubuntu 8.10, intrepid ibex.

When I try to launch the program,  it starts to open,  I briefly see "Google Earth",  a "start tips"   window for a very brief flash,  and something else  that is evidently the main screen, then everything closes.

I am obviously NOT   very astute at Linux here   Anyone??

---

### Post by dcstar on 2009-04-20
> **440roadrunner said:**
> I thought I installed Google Earth using these instructions:

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

running Ubuntu 8.10, intrepid ibex.

When I try to launch the program,  it starts to open,  I briefly see "Google Earth",  a "start tips"   window for a very brief flash,  and something else  that is evidently the main screen, then everything closes.

I am obviously NOT   very astute at Linux here   Anyone??

Open a terminal and type the launch command, then post the messages back here.

---

### Post by 440roadrunner on 2009-04-20
Thanks for the reply,  David,  but you'll have to be careful to step me through--I barely know what's going on.

Opened a terminal,  cd  to directory,  is

/opt/google-earth,  and evidently   "launch command"  is just "googleearth"  ?


(That is I got to this point and hit ENTER)



 /opt/google-earth$ googleearth

  

I got this:


Warning: Unable to create prefs directory '/home/delars/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
delars@delars-laptop:/opt/google-earth$

---

### Post by 440roadrunner on 2009-04-21
bumper, bump,  the big "B"

---

### Post by dmizer on 2009-04-21
A quick google search on your error produced this: [http://skoroneos.blogspot.com/2009/02/googleearth-5-on-ubuntu-810.html](http://skoroneos.blogspot.com/2009/02/googleearth-5-on-ubuntu-810.html)

Which suggests that this will fix your problem:
```
mv /usr/local/google-earth/libcrypto.so.0.9.8 /usr/local/google-earth/bkp_libcrypto.so.0.9.8
```

---

