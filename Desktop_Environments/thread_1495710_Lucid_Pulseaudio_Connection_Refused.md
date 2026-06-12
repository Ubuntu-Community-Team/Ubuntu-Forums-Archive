---
title: "Lucid Pulseaudio Connection Refused"
date: 2010-05-28
forum: Desktop Environments
---

### Post by skaramanger on 2010-05-28
Greetings,

Last night I took the plunge. Flashed my bios with the latest firmware and then did an upgraded from Karmic to Lucid. I must say for the most part the smoothest cleanest upgrade yet. Now though my problem.
 
When I login. I have no sound. I open Pulsaudio applet and the message at the bottom of the applet is connection refused.  Clicking on connect of course got the same error message.  So I open a terminal and type:

```
pulseaudio --start
```

and wahla the is sound.  I then looked in preference->startup applications and found where pulse was being started and the command:

```
start-pulse-x11
```


I figured it out by changing the command in system->preferences->startup applications 
 
Pulseaudio Sound System from:

```
start-pulse-x11
``` to

```
/usr/bin/pulseaudio --start
```

Now it starts up with no problems.

I know that this is a minor annoyance, but it would be nice to have it startup upon login.  Any suggestion?

TIA,
Skaramanger

---

### Post by p_rynhart on 2010-06-08
Hi,

I have observed this issue also but with a *clean* install of Lucid.  (I know it is clean because I've been on XP for the past 5 years!)  Symptoms are the same, i.e. "start-pulse-x11" is a startup item rather than "pulseaudio --start".  Looks like a bug.

Patrick

---

### Post by p_rynhart on 2010-06-08
By chance, do you have an instance of vncserver configured ?  I think that this package may change the default pulseaudio command to "start-pulseaudio-x11".

Thanks,

---

### Post by afrodeity on 2010-07-01
neither command works for me after last round of updates.

```

pulseaudio --start
E: main.c: Daemon startup failed.
afrodeity@afrodeity-desktop:~$ start-pulse-x11
start-pulse-x11: command not found

```

---

### Post by skaramanger on 2010-07-02
> **p_rynhart said:**
> By chance, do you have an instance of vncserver configured ?  I think that this package may change the default pulseaudio command to "start-pulseaudio-x11".

Thanks,

Greetings,

Sorry I failed to notice any replies here. I don't have vncserver configured.  I do notice that as I have pulseaudio starting now, all I have to do to get sound is click on the applet in the task bar and right click (I'm left handed so I left click) and select the default server and sound works. Still annoying though. 

Thanks for your reply,

---

### Post by skaramanger on 2010-07-02
> **afrodeity said:**
> neither command works for me after last round of updates.

```

pulseaudio --start
E: main.c: Daemon startup failed.
afrodeity@afrodeity-desktop:~$ start-pulse-x11
start-pulse-x11: command not found

```

Afrodeity,

I don't know if I have any solutions for you and I don't know you level of experience but, try this:


```
sudo apt-get check
```

at the command prompt in a terminal window.  It will check and fix any dependency problems that you system might have. Other wise try in the same window:

```
aptitude search | grep pulseaudio
```

This will tell you what of pulseaudio's packages are installed on your system. Post your output.  I'll try to check back, but I have a certs test to study for.

Best wishes

---

### Post by Elango Mani on 2010-07-02
elango@Elango-laptop:~$ pulseaudio --start
E: core-util.c: Failed to stat runtime directory /home/elango/.pulse/bdd5c16b9f262a67021d7b4e4bee4cdf-runtime: Invalid argument
W: lock-autospawn.c: Cannot access autospawn lock.
E: main.c: Failed to acquire autospawn lock
elango@Elango-laptop:~$ 


can some one help ???

---

### Post by afrodeity on 2010-07-02
> **skaramanger said:**
> Afrodeity,

I don't know if I have any solutions for you and I don't know you level of experience but, try this:


```
sudo apt-get check
```

at the command prompt in a terminal window.  It will check and fix any dependency problems that you system might have. Other wise try in the same window:

```
aptitude search | grep pulseaudio
```

This will tell you what of pulseaudio's packages are installed on your system. Post your output.  I'll try to check back, but I have a certs test to study for.

Best wishes

thanks skaramanger

```
aptitude search pulseaudio
i   gstreamer0.10-pulseaudio        - GStreamer plugin for PulseAudio           
i   libsdl1.2debian-pulseaudio      - Simple DirectMedia Layer (with X11 and Pul
i   pulseaudio                      - PulseAudio sound server                   
p   pulseaudio-dbg                  - PulseAudio sound server detached debugging
i   pulseaudio-equalizer            - PulseAudio Equalizer - LADSPA plugin graph
i   pulseaudio-esound-compat        - PulseAudio ESD compatibility layer        
p   pulseaudio-esound-compat-dbg    - PulseAudio ESD compatibility layer debuggi
i   pulseaudio-module-bluetooth     - Bluetooth module for PulseAudio sound serv
p   pulseaudio-module-bluetooth-dbg - Bluetooth module for PulseAudio sound serv
i   pulseaudio-module-gconf         - GConf module for PulseAudio sound server  
p   pulseaudio-module-gconf-dbg     - GConf module for PulseAudio sound server d
v   pulseaudio-module-hal           -                                           
p   pulseaudio-module-jack          - jackd modules for PulseAudio sound server 
p   pulseaudio-module-jack-dbg      - jackd modules for PulseAudio sound server 
p   pulseaudio-module-lirc          - lirc module for PulseAudio sound server   
p   pulseaudio-module-lirc-dbg      - lirc module for PulseAudio sound server de
p   pulseaudio-module-raop          - RAOP module for PulseAudio sound server   
p   pulseaudio-module-raop-dbg      - RAOP module for PulseAudio sound server   
v   pulseaudio-module-rygel-media-s -                                           
v   pulseaudio-module-udev          -                                           
i   pulseaudio-module-x11           - X11 module for PulseAudio sound server    
p   pulseaudio-module-x11-dbg       - X11 module for PulseAudio sound server deb
i A pulseaudio-module-zeroconf      - Zeroconf module for PulseAudio sound serve
p   pulseaudio-module-zeroconf-dbg  - Zeroconf module for PulseAudio sound serve
i   pulseaudio-utils                - Command line tools for the PulseAudio soun
p   pulseaudio-utils-dbg            - PulseAudio command line tools detached deb

```

If I aptitude search | grep pulseaudio
Then this message:
search: You must provide at least one search term

Grep is one of the tools I am still battling to get my head around, guess it stands for grab regular expression?

---

### Post by skaramanger on 2010-07-10
> **afrodeity said:**
> thanks skaramanger

```
aptitude search pulseaudio
i   gstreamer0.10-pulseaudio        - GStreamer plugin for PulseAudio           
i   libsdl1.2debian-pulseaudio      - Simple DirectMedia Layer (with X11 and Pul
i   pulseaudio                      - PulseAudio sound server                   
p   pulseaudio-dbg                  - PulseAudio sound server detached debugging
i   pulseaudio-equalizer            - PulseAudio Equalizer - LADSPA plugin graph
i   pulseaudio-esound-compat        - PulseAudio ESD compatibility layer        
p   pulseaudio-esound-compat-dbg    - PulseAudio ESD compatibility layer debuggi
i   pulseaudio-module-bluetooth     - Bluetooth module for PulseAudio sound serv
p   pulseaudio-module-bluetooth-dbg - Bluetooth module for PulseAudio sound serv
i   pulseaudio-module-gconf         - GConf module for PulseAudio sound server  
p   pulseaudio-module-gconf-dbg     - GConf module for PulseAudio sound server d
v   pulseaudio-module-hal           -                                           
p   pulseaudio-module-jack          - jackd modules for PulseAudio sound server 
p   pulseaudio-module-jack-dbg      - jackd modules for PulseAudio sound server 
p   pulseaudio-module-lirc          - lirc module for PulseAudio sound server   
p   pulseaudio-module-lirc-dbg      - lirc module for PulseAudio sound server de
p   pulseaudio-module-raop          - RAOP module for PulseAudio sound server   
p   pulseaudio-module-raop-dbg      - RAOP module for PulseAudio sound server   
v   pulseaudio-module-rygel-media-s -                                           
v   pulseaudio-module-udev          -                                           
i   pulseaudio-module-x11           - X11 module for PulseAudio sound server    
p   pulseaudio-module-x11-dbg       - X11 module for PulseAudio sound server deb
i A pulseaudio-module-zeroconf      - Zeroconf module for PulseAudio sound serve
p   pulseaudio-module-zeroconf-dbg  - Zeroconf module for PulseAudio sound serve
i   pulseaudio-utils                - Command line tools for the PulseAudio soun
p   pulseaudio-utils-dbg            - PulseAudio command line tools detached deb

```

If I aptitude search | grep pulseaudio
Then this message:
search: You must provide at least one search term

Grep is one of the tools I am still battling to get my head around, guess it stands for grab regular expression?

Sounds good I don't know. As for the command

try this :

aptutide search pulseaudio | grep ^i

the ^ says to grep match what follows at the begining of the line only. In this case i for whats installed.  You will get back a listing of pulseaudio packages installed on your system.  Sorry I didn't reply sooner. Had some cert testing to get out of the way.

skaramanger

---

### Post by afrodeity on 2010-07-11
Hello Skaramanger,

While you were gone, I found a workaround, but not sure exactly why it is working and sound stability still not 100% because alsa wineserver sound is still quitting a lot when I play wine games but at least I can listen to music, and all my audio players work.

I made an /etc/asound.conf file and put this in:

```


pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```

Here is the information you requested:

```

aptitude search pulseaudio | grep ^i
i   gstreamer0.10-pulseaudio        - GStreamer plugin for PulseAudio           
i   libsdl1.2debian-pulseaudio      - Simple DirectMedia Layer (with X11 and Pul
i   pulseaudio                      - PulseAudio sound server                   
i   pulseaudio-equalizer            - PulseAudio Equalizer - LADSPA plugin graph
i   pulseaudio-esound-compat        - PulseAudio ESD compatibility layer        
i   pulseaudio-module-bluetooth     - Bluetooth module for PulseAudio sound serv
i   pulseaudio-module-gconf         - GConf module for PulseAudio sound server  
i   pulseaudio-module-x11           - X11 module for PulseAudio sound server    
i A pulseaudio-module-zeroconf      - Zeroconf module for PulseAudio sound serve
i   pulseaudio-utils                - Command line tools for the PulseAudio soun

```

---

### Post by skaramanger on 2010-07-12
> **afrodeity said:**
> Hello Skaramanger,

While you were gone, I found a workaround, but not sure exactly why it is working and sound stability still not 100% because alsa wineserver 

Sorry can't help with wineserver.

sound is still quitting a lot when I play wine games but at least I can listen to music, and all my audio players work.

I made an /etc/asound.conf file and put this in:

```


pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```

I have the same except I have commented mine out.  Could that I have USB sound. 

Here is the information you requested:

```

aptitude search pulseaudio | grep ^i
i   gstreamer0.10-pulseaudio        - GStreamer plugin for PulseAudio           
i   libsdl1.2debian-pulseaudio      - Simple DirectMedia Layer (with X11 and Pul
i   pulseaudio                      - PulseAudio sound server                   
i   pulseaudio-equalizer            - PulseAudio Equalizer - LADSPA plugin graph
i   pulseaudio-esound-compat        - PulseAudio ESD compatibility layer        
i   pulseaudio-module-bluetooth     - Bluetooth module for PulseAudio sound serv
i   pulseaudio-module-gconf         - GConf module for PulseAudio sound server  
i   pulseaudio-module-x11           - X11 module for PulseAudio sound server    
i A pulseaudio-module-zeroconf      - Zeroconf module for PulseAudio sound serve
i   pulseaudio-utils                - Command line tools for the PulseAudio soun

```

I have exactly what you have installed except for the pulsasudio-equalizer - for LADSPA.  You may want to try and adjust the equalizer. Otherwise I don't know if I can much help. Just post here if you find an answer.

Skaramanger

---

### Post by anttir on 2012-02-28
> **afrodeity said:**
> neither command works for me after last round of updates.

```

pulseaudio --start
E: main.c: Daemon startup failed.
afrodeity@afrodeity-desktop:~$ start-pulse-x11
start-pulse-x11: command not found

```

I had a problem like this.

mplayer *.mp3*
-- cut --
shm_open() failed: Permission denied
AO: [pulse] Init failed: Connection refused
Failed to initialize audio driver 'pulse'
shm_open() failed: Permission denied
shm_open() failed: Permission denied
-- cut --

$ pulseaudio --start
E: main.c: Daemon startup failed.

$ pulseaudio
E: shm.c: shm_open() failed: Permission denied
W: core.c: failed to allocate shared memory pool. Falling back to a normal memory pool.
E: module-console-kit.c: GetSessionsForUnixUser() call failed: org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program /lib/dbus-1.0/dbus-daemon-launch-helper: Success
E: module.c: Failed to load  module "module-console-kit" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialise daemon.
$ 

$ ls -al /lib/dbus-1.0/dbus-daemon-launch-helper 
-rwsr-xr-- 1 root scanner 47528 2011-07-22 20:05 /lib/dbus-1.0/dbus-daemon-launch-helper
$  /lib/dbus-1.0/dbus-daemon-launch-helper 
bash: /lib/dbus-1.0/dbus-daemon-launch-helper: Permission denied
$ sudo chmod a+x  /lib/dbus-1.0/dbus-daemon-launch-helper 
$ /lib/dbus-1.0/dbus-daemon-launch-helper 
dbus-daemon-activation-helper service.to.activate
$ 
$mplayer *.mp3*
Starting playback...
A: 224.8 (03:44.8) of 225.0 (03:45.0)  0.4% 

:popcorn:

---

### Post by Gallando on 2012-08-22
Remove .pulse folder in your home directory and let PulseAudio recreate it by running:

pulseaudio --start

This fixed it 100% for me

---

