---
title: "Need help with Muse music sequencer."
date: 2006-01-18
forum: Desktop Environments
---

### Post by Omnios on 2006-01-18
Hi I just installed Muse from synaptic and it ran once froze then would not start again, I tryed launching by the run command and the terminal as user and sudo. Sudo gives me a jack audio server error problabley because jack is not run as root.  Normal start up gives me this error.

 ```
tom@reboot:/usr/bin$ muse No superuser privileges, using system timer fallback
NO Config File </home/tom/.MusE> found
/usr/bin/mozilla-firefox
no locale <muse_en_CA.UTF-8>/</usr/share/muse/locale>
open projectfile: No such file or directory
starting with default template
  name2route: <alsa_pcm:playback_1> not found
  name2route: <alsa_pcm:playback_2> not found
set realtime scheduler: Operation not permitted
midi thread 18002 _NOT_ running SCHED_FIFO
Segmentation fault
tom@reboot:/usr/bin$

```

 Any help will be greatly apprecited.

---

### Post by christhemonkey on 2006-01-18
Have you launched jack prior to starting muse?

---

### Post by Omnios on 2006-01-19
I had jack d so anyways I tryed installing jack and still have errors.

 ```
tom@reboot:~$ muse
No superuser privileges, using system timer fallback
NO Config File </home/tom/.MusE> found
/usr/bin/mozilla-firefox
no locale <muse_en_CA.UTF-8>/</usr/share/muse/locale>
open projectfile: No such file or directory
starting with default template
  name2route: <alsa_pcm:playback_1> not found
  name2route: <alsa_pcm:playback_2> not found
set realtime scheduler: Operation not permitted
midi thread 17808 _NOT_ running SCHED_FIFO
Segmentation fault

```

 ```
tom@reboot:~$ sudo jack
This is jack 3.1.1 (C)2004 Arne Zellentin <zarne@users.sf.net>
*** glibc detected *** double free or corruption (!prev): 0x08173bc8 ***
Aborted
tom@reboot:~$

```

```
tom@reboot:~$ sudo muse
Password:
/usr/bin/mozilla-firefox
tom@reboot:~$ sudo jacklaunch muse
/usr/bin/mozilla-firefox

```

 I have firefox 1.5 im wondering if this makes any difference and no cd in the drive. I also do not have superuser passwd set up.

---

### Post by christhemonkey on 2006-01-20
try getting qjackctrl with synaptic, this gives a nice gui for getting jack working.  Then if jack starts working then mayhaps muse will?

---

### Post by Omnios on 2006-01-20
k got qjackctrl and still nota. As I tryed before and got a cant find jack error I installed jack so now I have jack and jackd. I think muse is trying to start with jack isntead of jackd, not shure on that though. 

 I realy want to get this program working and mentioned eirlier It started once and would not start again after that.

 K did a driver debug and got this

 ```
tom@reboot:~$ jack -d --debug
This is jack 3.1.1 (C)2004 Arne Zellentin <zarne@users.sf.net>
 *debug* global_cf: {'base_dir': {'val': '~/jack'}}
 *debug* user_cf: {'cd_device': {'val': '/media/cdrom1'}}
 *debug* argv_cf: {'debug': {'val': True}, 'dont_work': {'val': True}}
 *debug* username is tom
 *debug* hostname is reboot
 *debug* mail is tom@reboot, was default / @
 *debug* multi_mode:0
*** glibc detected *** double free or corruption (!prev): 0x08173bc8 ***
Aborted
tom@reboot:~$

```

---

