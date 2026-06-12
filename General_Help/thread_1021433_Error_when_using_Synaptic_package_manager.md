---
title: "Error when using Synaptic package manager"
date: 2008-12-25
forum: General Help
---

### Post by soundpath on 2008-12-25
I installed Moblock & moblock control today and I thought everything was installed correctly, but when I tried to open the Synaptic package manager I recieved this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

so I did what it asked me to do and I got the Moblock configuration screen. I wasn't sure how that was relevant, so I just closed it.

I disabled moblock in the terminal, but that didn't do anything.

I'm not really sure what I did wrong or what is causing this. I've only had Ubuntu for about a week & all of this is still new to me. I'd really appreciate some help.

---

### Post by taurus on 2008-12-25
Make sure you close down synaptic first.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by thingy87654321 on 2008-12-25
if that does not work turn the computer off
when it says "press esc" when grub is loading press it 
go to safe mode
run the option on the blue menu that pops up "fix broken packages"
that should work

---

### Post by jre on 2008-12-27
When you come to the configure Moblock screen next time, don't abort but run through the whole procedure. To do so you may do a
```
sudo dpkg-reconfigure --force moblock-control
```

Quoting [https://help.ubuntu.com/community/MoBlock#I%20tried%20to%20install%20MoBlock%20but%20I%27m%20stuck%20on%20a%20screen%20with%20a%20Moblock%20warning](https://help.ubuntu.com/community/MoBlock#I%20tried%20to%20install%20MoBlock%20but%20I%27m%20stuck%20on%20a%20screen%20with%20a%20Moblock%20warning)

```
*I tried to install MoBlock but I'm stuck on a screen with a Moblock warning*

This is a so called "debconf" question. Read the text and confirm by pressing "OK". If your debconf interface doesn't support your mouse, then you have to use your keyboard: hit the "TAB" key until "OK" is highlighted and then press "RETURN".

You may also do a "sudo dpkg-reconfigure debconf" and select "Gnome" as your interface. Then you can use your mouse for debconf questions.
```

---

