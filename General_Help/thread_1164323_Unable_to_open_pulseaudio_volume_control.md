---
title: "Unable to open pulseaudio volume control"
date: 2009-05-19
forum: General Help
---

### Post by urosg3 on 2009-05-19
After fresh install of Ubuntu 9.04 and pulse audio, I was unable to open volume control, it appears to open, but somehow it crashes. 

Please, help I`m desperate for music;)

---

### Post by paradigm2 on 2009-05-19
Hmmm.  Any messages seen in the log file viewer?  

Perhaps try deleting ~/.pulse and rebooting?

---

### Post by urosg3 on 2009-05-19
this is pulseaudio -vv

urosh@urosh-desktop:~$ pulseaudio -vv 
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: PolicyKit refuses acquire-high-priority privilege.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: main.c: Can realtime: no, can high-priority: no
D: main.c: Can realtime: no, can high-priority: no
I: main.c: This is PulseAudio 0.9.14
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux i686 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is 6802301efbc8c2577c84fa2b4a12c0b1.
I: main.c: Using runtime directory /home/urosh/.pulse/6802301efbc8c2577c84fa2b4a12c0b1:runtime.
I: main.c: Using state directory /home/urosh/.pulse.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.


urosh@urosh-desktop:~$ pulseaudio & pavucontrol
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[1] 5390
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
pavucontrol: relocation error: pavucontrol: symbol pa_context_get_card_info_list, version PULSE_0 not defined in file libpulse.so.0 with link time reference
[1]+  Exit 1                  pulseaudio

---

### Post by paradigm2 on 2009-05-19
```

sudo rm -rf /home/urosh/.pulse

```

(The above deletes the entire directory which stores your pulse audio settings)

reboot.

Any change?

---

### Post by urosg3 on 2009-05-19
No, same as before

---

### Post by paradigm2 on 2009-05-19
The output indicates that pulseaudio is already running on your system as a daemon.  So there is no need to try to start it again.  That is why it exits with "E: pid.c: Daemon already running."  But this does not seem to explain the pavucontrol error.
 
If you go to System -> Preferences -> Sound what does it show as the options?

When doing just "pavucontrol" by itself I assume you still get:

```

pavucontrol: relocation error: pavucontrol: symbol pa_context_get_card_info_list, version PULSE_0 not defined in file libpulse.so.0 with link time reference

```

If nothing else and we can't get it, you might try reinstalling pulseaudio or perhaps upgrading to 9.0.15 using a PPA (I can get you instructions on that)

---

### Post by urosg3 on 2009-05-19
System -> Preferences -> Sound is set  to auto-detect. 
This is output of yours code:

urosh@urosh-desktop:~$ pavucontrol: relocation error: pavucontrol: symbol pa_context_get_card_info_list, version PULSE_0 not defined in file libpulse.so.0 with link time reference
bash: pavucontrol:: command not found

Sorry for bad English

---

### Post by paradigm2 on 2009-05-19
General instructions (for Jaunty) to upgrade to an unofficial version of alsa and pulseaudio (use only if willing and no one else can help) :

To install a much newer alsa and pulse audio (again this is unofficial) :

1. Add these unofficial PPA's to your sources list or else the "Third Party Repositories" in Synaptic Package Manager.

deb [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) jaunty main

2. Upgrade all the upgrades suggested from the repository..

---

### Post by urosg3 on 2009-05-19
yes, I did`it exactly as in tutorial, I`m confused, I`m almost sure i do not do anything wrong.

---

### Post by paradigm2 on 2009-05-19
> **urosg3 said:**
> yes, I did`it exactly as in tutorial, I`m confused, I`m almost sure i do not do anything wrong.

Hmmm.  It should have upgraded you to pulseaudio 9.0.15 then, but it shows that you have 9.0.14:

```

I: main.c: This is PulseAudio 0.9.14

```

Are you sure you added these repositories and upgraded as opposed to different repositories?

```

cat /etc/apt/sources.list

```

---

### Post by urosg3 on 2009-05-19
I think this is important part of output

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://archive.ubuntu.com.ba/ubuntu/](http://archive.ubuntu.com.ba/ubuntu/) jaunty-security main restricted
deb-src [http://archive.ubuntu.com.ba/ubuntu/](http://archive.ubuntu.com.ba/ubuntu/) jaunty-security main restricted
deb [http://archive.ubuntu.com.ba/ubuntu/](http://archive.ubuntu.com.ba/ubuntu/) jaunty-security universe
deb-src [http://archive.ubuntu.com.ba/ubuntu/](http://archive.ubuntu.com.ba/ubuntu/) jaunty-security universe
deb [http://archive.ubuntu.com.ba/ubuntu/](http://archive.ubuntu.com.ba/ubuntu/) jaunty-security multiverse
deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) jaunty main #gnome-do
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #wine
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free #medibuntu
deb-src [http://archive.ubuntu.com.ba/ubuntu/](http://archive.ubuntu.com.ba/ubuntu/) jaunty-security multiverse
deb [http://ppa.launchpad.net/medigeek/ppa/ubuntu](http://ppa.launchpad.net/medigeek/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) jaunty main

---

### Post by paradigm2 on 2009-05-19
> **urosg3 said:**
> I think this is important part of output

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://archive.ubuntu.com.ba/ubuntu/](http://archive.ubuntu.com.ba/ubuntu/) jaunty-security main restricted
deb-src [http://archive.ubuntu.com.ba/ubuntu/](http://archive.ubuntu.com.ba/ubuntu/) jaunty-security main restricted
deb [http://archive.ubuntu.com.ba/ubuntu/](http://archive.ubuntu.com.ba/ubuntu/) jaunty-security universe
deb-src [http://archive.ubuntu.com.ba/ubuntu/](http://archive.ubuntu.com.ba/ubuntu/) jaunty-security universe
deb [http://archive.ubuntu.com.ba/ubuntu/](http://archive.ubuntu.com.ba/ubuntu/) jaunty-security multiverse
deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) jaunty main #gnome-do
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #wine
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free #medibuntu
deb-src [http://archive.ubuntu.com.ba/ubuntu/](http://archive.ubuntu.com.ba/ubuntu/) jaunty-security multiverse
deb [http://ppa.launchpad.net/medigeek/ppa/ubuntu](http://ppa.launchpad.net/medigeek/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) jaunty main

Looks okay....

What happens now when you go to System -> Administration -> Upgrade manager and then hit CHECK ?

---

### Post by urosg3 on 2009-05-19
Wow, there is a list of pulseaudio something, i fire it! But I run sudo apt-get update in terminal, there is nothing for me waiting. Strange... Update manager running... wish me luck

---

### Post by urosg3 on 2009-05-19
Now is even worst, i lose sound completely, when i open volume control dialog window pop up and say Connection failed: Connection refused

---

### Post by paradigm2 on 2009-05-19
> **urosg3 said:**
> Now is even worst, i lose sound completely, when i open volume control dialog window pop up and say Connection failed: Connection refused

Hmm.

Try deleting ~/.pulse again and rebooting (especially if you have not yet done so after the upgrade)

---

### Post by urosg3 on 2009-05-19
Yes! Working! You are the MAN! I can enjoy Johnny Cash, now. Working as a dream. I connected old soviet amplifier an paar of old DDR speakres with total of 250 WATT, this is something.

Thanks Man, i wish you can heard-it

---

### Post by paradigm2 on 2009-05-19
> **urosg3 said:**
> Yes! Working! You are the MAN! I can enjoy Johnny Cash, now. Working as a dream. I connected old soviet amplifier an paar of old DDR speakres with total of 250 WATT, this is something.

Thanks Man, i wish you can heard-it

Awesome!  Thank also thermuso for his work and the PPA as well as the developers. :)  Take care.

---

