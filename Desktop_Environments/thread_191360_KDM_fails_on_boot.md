---
title: "KDM fails on boot"
date: 2006-06-07
forum: Desktop Environments
---

### Post by snaga on 2006-06-07
KDM fails to start when I boot up. I have turned off splash, so I just end up at a command line login. If I log in as root, kdm is running. If I then restart it, X starts and I can log in just fine. This started since my upgrade to Dapper a couple of days ago.

Other than turning off splash to I could log in and then restart KDE, I am at a loss as to what to try. I suppose I should try gdm. the the memory corruption noted in the syslog a hardware problem?

Here is a portion of syslog:

```

Jun  7 11:00:30 localhost kdm: :0[4998]: IO Error in XOpenDisplay
Jun  7 11:00:30 localhost kdm[4986]: X server for display :0 terminated unexpectedly
Jun  7 11:00:30 localhost kdm[4986]: Display :0 cannot be opened
Jun  7 11:00:30 localhost kdm[4986]: Unable to fire up local display :0; disabling.
Jun  7 11:00:33 localhost kernel: [4294708.123000] eth0: no IPv6 routers present
Jun  7 11:01:31 localhost kdm_greet[5304]: Can't open default user face
Jun  7 11:01:36 localhost kdm_greet[5304]: Internal error: memory corruption detected

```

---

### Post by shugie on 2006-06-07
I have a problem much like yours I think. My linux boots and will show the mouse for a small time, then crashes before KDE will allow me to logon. The system goes back to a text screen and keeps repeating something about how fxx_microcode.fw or something like that will not load. Is there anyway I can try to repair through the command line easily. Is there a way to do apt-get make-it-all-better?

---

### Post by shugie on 2006-06-07
Sorry, I read that "KDE fails on boot." My bad.

---

### Post by Kebabji on 2006-07-02
i have the same problem, did anyone come up with a solution?

---

### Post by geek.de.nz on 2006-07-07
I have the same problem. My work-around for now is that I installed gdm and started kde with that:

```

sudo apt-get install gdm

```

Hope someone finds a solution if I don't. Otherwise I will post the solution here. :-)

---

