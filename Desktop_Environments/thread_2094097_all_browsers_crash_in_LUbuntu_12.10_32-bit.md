---
title: "all browsers crash in LUbuntu 12.10 32-bit"
date: 2012-12-12
forum: Desktop Environments
---

### Post by Oh-la-la on 2012-12-12
Hi,

I'm using LUbuntu at home and can't get any browser to work - crashes within few seconds. It started after i've tried to install google voice plugin thru .deb packet.

What i've already tried:
- reinstalled firefox and chrome
- reinstalled flash (tried nspluginwrapper too)
- removed google plugin (```
sudo apt-get --purge remove google-talkplugin
```)

Thanks

---

### Post by DukeOfMixture on 2012-12-13
> **ceshiwuhao said:**
> I am pleased  to this forum, join discussion will not bother everyone?

That sentence doesn't make any sense.

---

### Post by Rex Bouwense on 2012-12-13
> **Oh-la-la said:**
> Hi,

I'm using LUbuntu at home and can't get any browser to work - crashes within few seconds.



Pehaps it is a RAM problem.  When you boot, hit ESC at the GRUB screen and call up memtest86. If that doesn't run clear, you may have bad RAM.

---

### Post by acuel on 2012-12-13
Hey,

Have a very similar problem, with Lubuntu 12.10 on Toshiba AC100.  After performing several upgrades every browser has become very unstable, namely:

[1] Chromium and xxxterm work partially: I can search on google or write this post  but going to youtube or most websites crashes immediately.

[2] Firefox crashes when immediatly when starting.

First thought it was an AC100 related issue, but Oh-la-la post makes me think it could be more general.  Don't think it has to do with RAM since everything was okay before I made the upgrades. Thanks for your help, and please ask for any precision.

A.

---

### Post by acuel on 2012-12-13
When adding "enable_scripts=0" to /home/myhome/.xxxterm.conf I experience no crash anymore in xxxterm browser.  

Don't know how to go further, that is 1) disable scripts in Firefox or Chromium (no use for me), 2) understand where the problem comes from, and 3) have scripts  working in any browser. 

A.

---

### Post by nonFelix on 2012-12-21
Try Midori - it works fast and is very stable on Toshiba AC100.
 
nF

---

### Post by maxpro4u on 2013-01-15
I have a simular issue. Chromium works fine using 12.04 but I get errors "he's dead jim" using 12.10 or 13.04.

---

### Post by Gaygerbil on 2013-01-16
You guys should post RAM specs, this is a very unusual problem never dealt with it. I was running Lubuntu 12.04 32 bit before running 12.10 64 bit now browsers work fine for me. The fact that Midori works for you leads me to believe that you have very low RAM as Chromium especially takes a good bit of RAM to run.

---

### Post by acuel on 2013-02-10
In my case Midori crashes too; it shuts down whenever I try to access a page, let's say just google. My RAM usage is low so I don't believe that's the issue.  In summary, neither Firefox, Chrome nor Midori work at all. xxxterm work decently but is very unstable. Please let me know any further information I could provide in order to identify the problem.

---

### Post by zombifier25 on 2013-02-10
Running the browsers in a terminal will spawn some outputs that can help.


Also, I don't know about Chromium, but try launching Firefox in safe mode and see if it helps:
```
firefox -safe-mode
```

---

### Post by acuel on 2013-02-11
Thanks for your answer. Please see terminal copy below: every browser crashes before showing anything. 

ae@ae:~$ firefox
ae@ae:~$ firefox -safe-mode
ae@ae:~$ chromium-browser 
[1:1:56061534:ERROR:nss_util.cc(692)] Failed to load NSS libraries.
Aborted (core dumped)
ae@ae:~$ midori
(midori:1498): GLib-ERROR **: creating thread 'dconf worker': Error creating thread: Resource temporarily unavailable
Trace/breakpoint trap (core dumped)
ae@ae:~$ xxxterm 
WARNING: gnome-keyring:: couldn't connect to: /run/user/ae/keyring-ejavNL/pkcs11: No such file or directory
(xxxterm:1513): GLib-ERROR **: creating thread 'dconf worker': Error creating thread: Resource temporarily unavailable
Trace/breakpoint trap (core dumped)

The weird point is that when I launch them from the menu the behavior is different. For example I am presently on xxxterm and it works. Firefox would show a restore page and crash whatever I do. Chromium would show that "he's dead Jim" whatever I do. Midori never shows anything.

---

