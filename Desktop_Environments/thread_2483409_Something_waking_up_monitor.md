---
title: "Something waking up monitor?"
date: 2023-01-29
forum: Desktop Environments
---

### Post by EricDP on 2023-01-29
I'm not sure exactly when this started, but my monitor no longer remains suspended after the screen blanker kicks in. To be clear, the screen is blank, but the backlight is lit, and the power light is solid. After trying to troubleshoot I've found that suspend still works, but something turns the screen back on. For example, if I do the command
```
vbetool dpms standby
```
The screen goes black, after a few seconds the backlight turns off, and the power light starts a slow-pulse indicating suspend mode. Then, after about 15 seconds, with no input from me, the screen turns back on (still black screen, but backlight is lit and power light is solid).
If I manually lock the screen, the same thing occurs.

I'm currently running Ubuntu 22.04.1. Display manager is gdm3.

I'm sure this was working at some point.

Any thoughts about where to look for what might be causing the screen to turn back on?

---

### Post by #&amp;thj^% on 2023-01-29
For now will you try this for a short time span:
```
bash -c 'sleep 0.1 && xset dpms force off'
```

---

### Post by EricDP on 2023-01-29
```
server does not have extension for dpms option
xset:  unknown option force


usage:  xset [-display host:dpy] option ...
```

---

### Post by #&amp;thj^% on 2023-01-29
Is this a Server then?
show this please:
```
apt policy libxcb-dpms0*

```
EDIT Also:
```
xset:  unknown option off

usage:  xset [-display host:dpy] option ...
    To turn bell off:
	-b                b off               b 0
    To set bell volume, pitch and duration:
	 b [vol [pitch [dur]]]          b on
    To disable bug compatibility mode:
	-bc
    To enable bug compatibility mode:
	bc
    To turn keyclick off:
	-c                c off               c 0
    To set keyclick volume:
	 c [0-100]        c on
    To control Energy Star (DPMS) features:
	-dpms      Energy Star features off
	+dpms      Energy Star features on
	 dpms [standby [suspend [off]]]     
	      force standby 
	      force suspend 
	      force off 
	      force on 
	      (also implicitly enables DPMS features) 
	      a timeout value of zero disables the mode 
    To set the font path:
	 fp= path[,path...]
    To restore the default font path:
	 fp default
    To have the server reread font databases:
	 fp rehash
    To remove elements from font path:
	-fp path[,path...]  fp- path[,path...]
    To prepend or append elements to font path:
	+fp path[,path...]  fp+ path[,path...]
    To set LED states off or on:
	-led [1-32]         led off
	 led [1-32]         led on
	-led named 'name'   led off
	 led named 'name'   led on
    To set mouse acceleration and threshold:
	 m [acc_mult[/acc_div] [thr]]    m default
    To set pixel colors:
	 p pixel_value color_name
    To turn auto-repeat off or on:
	-r [keycode]        r off
	 r [keycode]        r on
	 r rate [delay [rate]]
    For screen-saver control:
	 s [timeout [cycle]]  s default    s on
	 s blank              s noblank    s off
	 s expose             s noexpose
	 s activate           s reset
    For status information:  q
    To print version: -version


```
And:
```
xset q
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    on     02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  20
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0x0    WhitePixel:  0xffffff
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

```

---

### Post by EricDP on 2023-01-29
```
# apt policy libxcb-dpms0*
libxcb-dpms0-dev:
  Installed: (none)
  Candidate: 1.14-3ubuntu3
  Version table:
     1.14-3ubuntu3 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
libxcb-dpms0:
  Installed: (none)
  Candidate: 1.14-3ubuntu3
  Version table:
     1.14-3ubuntu3 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
```

---

### Post by #&amp;thj^% on 2023-01-29
can you show the code you ran? and you haven't answered my question.

---

### Post by EricDP on 2023-01-29
```
# xset q
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    on     02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  33
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x3a    BlackPixel:  0x0    WhitePixel:  0xffffff
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins
DPMS (Energy Star):
  Server does not have the DPMS Extension
```

---

### Post by EricDP on 2023-01-29
The cut&paste removed a linefeed between what I ran and the response. I've updated.

Also, I'll add the full response from the original request.

---

### Post by EricDP on 2023-01-29
```
# bash -c 'sleep 0.1 && xset dpms force off'
server does not have extension for dpms option
xset:  unknown option force


usage:  xset [-display host:dpy] option ...
    To turn bell off:
    -b                b off               b 0
    To set bell volume, pitch and duration:
     b [vol [pitch [dur]]]          b on
    To disable bug compatibility mode:
    -bc
    To enable bug compatibility mode:
    bc
    To turn keyclick off:
    -c                c off               c 0
    To set keyclick volume:
     c [0-100]        c on
    To control Energy Star (DPMS) features:
    -dpms      Energy Star features off
    +dpms      Energy Star features on
     dpms [standby [suspend [off]]]     
          force standby 
          force suspend 
          force off 
          force on 
          (also implicitly enables DPMS features) 
          a timeout value of zero disables the mode 
    To set the font path:
     fp= path[,path...]
    To restore the default font path:
     fp default
    To have the server reread font databases:
     fp rehash
    To remove elements from font path:
    -fp path[,path...]  fp- path[,path...]
    To prepend or append elements to font path:
    +fp path[,path...]  fp+ path[,path...]
    To set LED states off or on:
    -led [1-32]         led off
     led [1-32]         led on
    -led named 'name'   led off
     led named 'name'   led on
    To set mouse acceleration and threshold:
     m [acc_mult[/acc_div] [thr]]    m default
    To set pixel colors:
     p pixel_value color_name
    To turn auto-repeat off or on:
    -r [keycode]        r off
     r [keycode]        r on
     r rate [delay [rate]]
    For screen-saver control:
     s [timeout [cycle]]  s default    s on
     s blank              s noblank    s off
     s expose             s noexpose
     s activate           s reset
    For status information:  q
    To print version: -version
```

---

### Post by EricDP on 2023-01-29
> **1fallen said:**
> Is this a Server then?
This is a desktop.

---

### Post by #&amp;thj^% on 2023-01-29
Ah Ok don't run it as root just user:
```
$ bash -c 'sleep 0.1 && xset dpms off'

```
and Not
```
#bash -c 'sleep 0.1 && xset dpms off'
```

---

### Post by EricDP on 2023-01-29
```
$ bash -c 'sleep 0.1 && xset dpms off'
server does not have extension for dpms option
xset:  unknown option off


usage:  xset [-display host:dpy] option ...
    To turn bell off:
    -b                b off               b 0
    To set bell volume, pitch and duration:
     b [vol [pitch [dur]]]          b on
    To disable bug compatibility mode:
    -bc
    To enable bug compatibility mode:
    bc
    To turn keyclick off:
    -c                c off               c 0
    To set keyclick volume:
     c [0-100]        c on
    To control Energy Star (DPMS) features:
    -dpms      Energy Star features off
    +dpms      Energy Star features on
     dpms [standby [suspend [off]]]     
          force standby 
          force suspend 
          force off 
          force on 
          (also implicitly enables DPMS features) 
          a timeout value of zero disables the mode 
    To set the font path:
     fp= path[,path...]
    To restore the default font path:
     fp default
    To have the server reread font databases:
     fp rehash
    To remove elements from font path:
    -fp path[,path...]  fp- path[,path...]
    To prepend or append elements to font path:
    +fp path[,path...]  fp+ path[,path...]
    To set LED states off or on:
    -led [1-32]         led off
     led [1-32]         led on
    -led named 'name'   led off
     led named 'name'   led on
    To set mouse acceleration and threshold:
     m [acc_mult[/acc_div] [thr]]    m default
    To set pixel colors:
     p pixel_value color_name
    To turn auto-repeat off or on:
    -r [keycode]        r off
     r [keycode]        r on
     r rate [delay [rate]]
    For screen-saver control:
     s [timeout [cycle]]  s default    s on
     s blank              s noblank    s off
     s expose             s noexpose
     s activate           s reset
    For status information:  q
    To print version: -version
```

---

### Post by #&amp;thj^% on 2023-01-29
one final question, are you now using Wayland Session?
This is strange to me, and you could try:
```
bash -c 'sleep 0.1 && xset -dpms' 
```
I'm curious though what shows here:
```
xset -q | awk '/DPMS is/ {print $NF}'

```

---

### Post by EricDP on 2023-01-29
How do I determine if I'm using Wayland Session?

```
$ bash -c 'sleep 0.1 && xset -dpms'
server does not have extension for -dpms option
$ xset -q | awk '/DPMS is/ {print $NF}'
$ xset -q
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    on     02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  33
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x3a    BlackPixel:  0x0    WhitePixel:  0xffffff
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins
DPMS (Energy Star):
  Server does not have the DPMS Extension
$ 
```

---

### Post by #&amp;thj^% on 2023-01-29
Like this:
```
echo $XDG_SESSION_TYPE
```
EDIT I would like to see this as well:
```
xset -q | awk '/DPMS is/ {print $NF}'
```

---

### Post by EricDP on 2023-01-29
```
$ echo $XDG_SESSION_TYPE
wayland
$ xset -q | awk '/DPMS is/ {print $NF}'
$ 
```

---

### Post by #&amp;thj^% on 2023-01-29
Yep Wayland
You won't have xset during that session.
If you want to login under X11 you might have better results for this matter.

---

### Post by EricDP on 2023-01-29
OK... still have the issue, but maybe this is progress?

```
$ echo $XDG_SESSION_TYPE
x11
$ xset -q | awk '/DPMS is/ {print $NF}'
Enabled
```

This now makes the screen blank and turn off for a few seconds, then it turns back on:

```
bash -c 'sleep 0.1 && xset dpms force off'
```

---

### Post by EricDP on 2023-01-29
This, when run as root, actually put it into standby and it stayed there. Only problem is I couldn't wake it, even with keyboard/mouse input. Had to force a reboot with reset button.

```
[COLOR=#000000][FONT=&amp]vbetool dpms standby[/FONT][/COLOR]
```

---

### Post by EricDP on 2023-01-29
```
$ xset q
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    on     02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  33
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0x0    WhitePixel:  0xffffff
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On
```

---

### Post by #&amp;thj^% on 2023-01-29
try this for me, run this first
```
xset +dpms

```
then again
```
bash -c 'sleep 0.1 && xset dpms force off'
```
FTR It's been behaving as expected on my end.

---

### Post by EricDP on 2023-01-29
It turns off, then, about 10 seconds later, turns back on. Similar to what happens if I hit OS Key + L.

I would say this is all as expected, except it shouldn't turn back on until I move the mouse or hit a key, no?

---

### Post by exploder on 2023-01-30
I have the identical problem in Linux Mint. Running the 2 commands 1fallen provided, the monitor actually stay asleep! Thank you! Not trying to hijack this thread, just wanted to say thanks!

---

### Post by enricobe on 2023-01-30
> **1fallen said:**
> try this for me, run this first
```
xset +dpms

```
then again
```
bash -c 'sleep 0.1 && xset dpms force off'
```
FTR It's been behaving as expected on my end.

Similar problem here: on Wayland the monitor stay always on and it never goes in standby. On X11 the standby works fine

---

### Post by EricDP on 2023-01-30
I'm glad it's working for others. Still not working for me. It goes into standby, then wakes up again after a few seconds. The screen stays black, but backlight is lit and power light is on solid, not pulsing. :(

---

### Post by #&amp;thj^% on 2023-01-30
Have you got anything running in a loop?
And thanks for the feedback from enricobe and exploder, feedback is always encouraged for me. ;)

---

### Post by enricobe on 2023-01-30
I've just installed Kubuntu and nothing strange running here. TBH I've also re-installed it because the first time I had manually installed the Intel driver and I thought this could be the reason of this bug. Anyway, also after reinstalling it I still have the problem.

If I remove the Plasma flag to keep the system up while reproducing some media, the screen goes in standby for a second and then wake up again.

---

### Post by #&amp;thj^% on 2023-01-30
> **enricobe said:**
> I've just installed Kubuntu and nothing strange running here. TBH I've also re-installed it because the first time I had manually installed the Intel driver and I thought this could be the reason of this bug. Anyway, also after reinstalling it I still have the problem.

If I remove the Plasma flag to keep the system up while reproducing some media, the screen goes in standby for a second and then wake up again.

This has been a problem for many then, also has anyone filed a bug yet?
@enricobe how about a swap?
```
cat /proc/swaps
```
I use this system for heavy lifting so mine is huge:
```
cat /proc/swaps
Filename				Type		Size		Used	Priority
/dev/nvme0n1p2                          partition	8196092		643072	-2
/dev/dm-0                               partition	7999484		0	-3


```
If your ok with a small test then, and no pressure, but create a swap partition and recheck. (Moral of the story ubuntu swap files are quirky)

---

### Post by EricDP on 2023-01-30
> **1fallen said:**
> Have you got anything running in a loop?
Nothing that I'm aware of. I just tried reboot, login, lock screen. Same behaviour. After that I ran top to see what was running. See anything odd?

```
Tasks: 340 total,   1 running, 339 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni, 99.9 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :  15867.8 total,  12865.2 free,    995.6 used,   2007.0 buff/cache
MiB Swap:   2048.0 total,   2048.0 free,      0.0 used.  14367.5 avail Mem 


    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                    
   4189 eric      20   0   15260   5040   4004 R   0.3   0.0   0:00.07 top                                        
      1 root      20   0  167264  12128   7960 S   0.0   0.1   0:01.29 systemd                                    
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kthreadd                                   
      3 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_gp                                     
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_par_gp                                 
      5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 slub_flushwq                               
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 netns                                      
      7 root      20   0       0      0      0 I   0.0   0.0   0:00.00 kworker/0:0-events                         
      8 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/0:0H-events_highpri                
      9 root      20   0       0      0      0 I   0.0   0.0   0:00.49 kworker/u24:0-events_unbound               
     10 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 mm_percpu_wq                               
     11 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_tasks_rude_                            
     12 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_tasks_trace                            
     13 root      20   0       0      0      0 S   0.0   0.0   0:00.02 ksoftirqd/0                                
     14 root      20   0       0      0      0 I   0.0   0.0   0:00.06 rcu_sched                                  
     15 root      rt   0       0      0      0 S   0.0   0.0   0:00.00 migration/0                                
     16 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0                              
     17 root      20   0       0      0      0 I   0.0   0.0   0:00.04 kworker/0:1-events                         
     18 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0                                    
     19 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/1                                    
     20 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/1                              
     21 root      rt   0       0      0      0 S   0.0   0.0   0:00.15 migration/1                                
     22 root      20   0       0      0      0 S   0.0   0.0   0:00.00 ksoftirqd/1                                
     23 root      20   0       0      0      0 I   0.0   0.0   0:00.00 kworker/1:0-events                         
     24 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/1:0H-events_highpri                
     25 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/2                                    
     26 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/2                              
     27 root      rt   0       0      0      0 S   0.0   0.0   0:00.16 migration/2                                
     28 root      20   0       0      0      0 S   0.0   0.0   0:00.01 ksoftirqd/2                                
     29 root      20   0       0      0      0 I   0.0   0.0   0:00.00 kworker/2:0-cgroup_destroy                 
     30 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/2:0H-events_highpri                
     31 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/3                                    
     32 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/3                              
     33 root      rt   0       0      0      0 S   0.0   0.0   0:00.15 migration/3                                
     34 root      20   0       0      0      0 S   0.0   0.0   0:00.01 ksoftirqd/3                                
     35 root      20   0       0      0      0 I   0.0   0.0   0:00.00 kworker/3:0-events                         
     36 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/3:0H-events_highpri                
     37 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/4                                    
     38 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/4                              
     39 root      rt   0       0      0      0 S   0.0   0.0   0:00.16 migration/4                                
     40 root      20   0       0      0      0 S   0.0   0.0   0:00.00 ksoftirqd/4                                
     41 root      20   0       0      0      0 I   0.0   0.0   0:00.00 kworker/4:0-events                         
```

---

### Post by #&amp;thj^% on 2023-01-30
There is more noise from kworker, than I care to see:
```

    0[||       1.3%]   3[||       3.3%]   6[|         0.7%]  9[|         1.3%]
    1[||       4.5%]   4[||       2.6%]   7[||        2.0%] 10[||        2.0%]
    2[||       3.9%]   5[||       2.0%]   8[||        3.2%] 11[||        1.3%]
  Mem[|||||||||||||||||||||2.62G/7.63G] Tasks: 126, 549 thr, 301 kthr; 1 runni
  Swp[|||                   524M/15.4G] Load average: 0.12 0.12 0.21 
                                        Uptime: 07:12:36

  [Main] [I/O]
    PID USER       PRI  NI  VIRT   RES   SHR S  CPU%&#9661;MEM%   TIME+  Command
   1449 root        20   0  252M 13100  9540 S   0.0  0.2  0:00.41 /usr/sbin/Net
   1450 root        20   0  252M 13100  9540 S   0.0  0.2  0:00.02 /usr/sbin/Net
   1512 root        20   0  227M  6704  2416 S   0.7  0.1  0:18.12 /usr/lib/eddi
   1517 root        20   0  301M  4608  3972 S   0.0  0.1  0:00.04 /usr/sbin/lig
   1518 ntpsec      RT   0 84432 18792  8532 S   0.0  0.2  0:02.38 /usr/sbin/ntp
   1522 root        20   0  301M  4608  3972 S   0.0  0.1  0:00.00 /usr/sbin/lig
   1525 root        20   0  301M  4608  3972 S   0.0  0.1  0:00.01 /usr/sbin/lig
   1545 root        20   0  5872  1032   940 S   0.0  0.0  0:00.00 /sbin/agetty
   1581 root        20   0  135M  9620  9620 S   0.0  0.1  0:00.00 /usr/bin/pyth
   1648 root        20   0 25.3G  114M 98196 S   0.0  1.5  0:21.74 /usr/lib/xorg
   1677 rtkit       21   1 22684   612   372 S   0.0  0.0  0:00.36 /usr/libexec/
   1678 rtkit       20   0 22684   612   372 S   0.0  0.0  0:00.18 /usr/libexec/
   1679 rtkit       RT   1 22684   612   372 S   0.0  0.0  0:00.17 /usr/libexec/
   1789 root        20   0  228M  4676  3828 S   0.0  0.1  0:02.50 /usr/libexec/
   1791 root        20   0  228M  4676  3828 S   0.0  0.1  0:00.00 /usr/libexec/
   1792 root        20   0  228M  4676  3828 S   0.0  0.1  0:00.65 /usr/libexec/
   1839 root        20   0 2546M 49052 11244 S   0.0  0.6  0:11.18 /usr/sbin/nor
   1915 root        20   0 2546M 49052 11244 S   0.0  0.6  0:00.72 /usr/sbin/nor
   1916 root        20   0 2546M 49052 11244 S   0.0  0.6  0:00.71 /usr/sbin/nor
   1917 root        20   0 2546M 49052 11244 S   0.0  0.6  0:00.30 /usr/sbin/nor
   1919 root        20   0 2546M 49052 11244 S   0.0  0.6  0:00.36 /usr/sbin/nor
   1920 root        20   0 2546M 49052 11244 S   0.0  0.6  0:00.00 /usr/sbin/nor
   1997 root        20   0 2546M 49052 11244 S   0.0  0.6  0:01.03 /usr/sbin/nor
   2125 root        20   0 2546M 49052 11244 S   0.0  0.6  0:00.54 /usr/sbin/nor
   2126 root        20   0 2546M 49052 11244 S   0.0  0.6  0:00.54 /usr/sbin/nor
   2131 root        20   0 2546M 49052 11244 S   0.0  0.6  0:00.45 /usr/sbin/nor
   2134 Debian-exi  20   0 27204 12532  3808 S   0.0  0.2  0:01.69 /usr/sbin/exi
   2136 root        20   0 2546M 49052 11244 S   0.0  0.6  0:00.00 /usr/sbin/nor
   2137 root        20   0 2546M 49052 11244 S   0.0  0.6  0:00.00 /usr/sbin/nor
   2138 root        20   0 2546M 49052 11244 S   0.0  0.6  0:01.24 /usr/sbin/nor
   2139 root        20   0 2546M 49052 11244 S   0.0  0.6  0:00.00 /usr/sbin/nor
F1Help  F2Setup F3SearchF4FilterF5Tree  F6SortByF7Nice -F8Nice +F9Kill  F10Quit

```
A muliti purpose thread, I don't mind that here, as long as we quote to who ever we're talking to.
Eric I need to see your swap used as well here for consistency.
```
cat /proc/swaps
```

---

### Post by EricDP on 2023-01-30
Don't hit swap much... got lots of RAM.

```
$ cat /proc/swaps
Filename                Type        Size        Used        Priority
/swapfile               file        2097148        0        -2
```

---

### Post by #&amp;thj^% on 2023-01-30
> **EricDP said:**
> Don't hit swap much... got lots of RAM.

```
$ cat /proc/swaps
Filename                Type        Size        Used        Priority
/swapfile               file        2097148        0        -2
```

That's what I thought swap file, as time rolls on, you'll find a swap partition just works better.
BTW You use swap more now that you ever had before, maybe just not aware of that yet.
It would be nice if exploder would add his findings for swap.
This is the only thing I see different  at a short look at whats been reported here.

---

### Post by EricDP on 2023-01-30
Are you suggesting I create a swap partition to solve this? Or is that just general advice to create a swap partition and delete the file?

---

### Post by EricDP on 2023-01-30
Just for kicks I went ahead and did it... still have the same problem though.
```
$ cat /proc/swaps
Filename                Type        Size        Used    Priority
/dev/sda2               partition    40959996    0    -2
```

---

### Post by philhughes on 2023-01-31
What GPU do you have? There is a long-standing bug that affects some older AMD GPUs:

[https://gitlab.freedesktop.org/drm/amd/-/issues/662](https://gitlab.freedesktop.org/drm/amd/-/issues/662)

---

### Post by #&amp;thj^% on 2023-01-31
> **philhughes said:**
> What GPU do you have? There is a long-standing bug that affects some older AMD GPUs:

[https://gitlab.freedesktop.org/drm/amd/-/issues/662](https://gitlab.freedesktop.org/drm/amd/-/issues/662)
+1 Long standing is a correct term...I wish I could help them but.....
@EricDP
```
inxi -G
Graphics:
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Ti Mobile] driver: nvidia
    v: 525.85.05
  Device-2: Syntek Integrated Camera type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.6 driver: N/A resolution:
    1: 1920x1080~120Hz 2: 4096x2160~60Hz
  API: OpenGL v: 4.6.0 NVIDIA 525.85.05 renderer: NVIDIA GeForce GTX 1650
    Ti/PCIe/SSE2


```
I show different results when I'm on my AMD GPU

---

### Post by enricobe on 2023-01-31
Hello,
I don't have a swap partition as per Ubuntu installer default settings.

```
[FONT=monospace][COLOR=#54ff54]**enrico@enrico-kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /proc/swaps [/COLOR]
Filename                                Type            Size           U
sed             Priority
[/FONT]
```

I'm not expert so I would prefer not to mess with partitions, but do you think the swap file can cause this problem? It seems strange that this problem affect only the Wayland session, doesn't it?

---

### Post by #&amp;thj^% on 2023-01-31
> **enricobe said:**
>  but do you think the swap file can cause this problem? It seems strange that this problem affect only the Wayland session, doesn't it?
Also look at 
```
cat /sys/power/mem_sleep
```
And boot logs:
```
journalctl -b-1 -p4 --no-pager
```
Well Its still up for grabs here EricDP created a swap partition and no joy there.
And AMD GPU's come into play here as well..hummm
EricDP this may be the best offerings I have left:
Traditionally Ubuntu supported a fairly blunt method of suspend and hibernate. Neither would integrate well with other apps and sometimes not even work on some machines. This new method doesn't require root and notifies all applications listening for power events.
```

systemctl suspend
```

and, **CAUTION** for
```

systemctl hibernate
```

---

### Post by EricDP on 2023-01-31
GPU is Intel
```
$ inxi -G
Graphics:
  Device-1: Intel CoffeeLake-S GT2 [UHD Graphics 630] driver: i915 v: kernel
  Display: x11 server: X.Org v: 1.21.1.3 driver: X: loaded: modesetting
    gpu: i915 resolution: 1920x1080~60Hz
  OpenGL: renderer: Mesa Intel UHD Graphics 630 (CFL GT2)
    v: 4.6 Mesa 22.0.5

```

And...
```
$ cat /sys/power/mem_sleep
s2idle [deep]
```

This next one generated hundreds of lines... is there something specific I should be parsing for?
```
[COLOR=#000000][FONT=&amp]journalctl -b-1 -p4 --no-pager[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]

BTW, system level suspend works just fine -- never had a problem with that. It's having the monitor shut off when idle that I can't get to work right.[/FONT][/COLOR]

---

### Post by EricDP on 2023-01-31
And as for hibernate, the system went down, but failed to resume. It treated it as a fresh boot when I powered back up. But like system-level suspend, I'm not that interested in hibernate. I just want the monitor to shut off when I've been away for a while...

---

### Post by #&amp;thj^% on 2023-02-01
> **EricDP said:**
> I just want the monitor to shut off when I've been away for a while...
Ok that clears my miss-conception you can change the value using gsettings in the terminal:

```
org.gnome.desktop.session idle-delay <time in seconds>
```
EDIT: that might be a bit vuage, so something like:
```
gsettings set org.gnome.desktop.session idle-delay 1800
```
will or should blank monitor in 30 mins.

---

### Post by enricobe on 2023-02-01
I've tested a Fedora KDE Live disc (Fedora uses Wayland by default) and I have the same issue. So in my case it doesn't seem to be an ubuntu bug, but something related to KDE Plasma

---

### Post by EricDP on 2023-02-01
> **1fallen said:**
> Ok that clears my miss-conception you can change the value using gsettings in the terminal:

```
org.gnome.desktop.session idle-delay <time in seconds>
```
EDIT: that might be a bit vuage, so something like:
```
gsettings set org.gnome.desktop.session idle-delay 1800
```
will or should blank monitor in 30 mins.

So that seems to have pretty much the same effect as locking the screen manually or setting the screen timeout via the GUI: after the time elapses, the screen fades, turns off, then 10 seconds later, turns back on. I feel like we're going in circles here. :(

---

### Post by enricobe on 2023-02-02
Hello,
I've solved the problem in a "hardware way".
I have an iiyama monitor with an "Auto" mode which automatically detects the input video source. I always used this mode because I have 2 PCs and it's useful to have a DP/HDMI automatic switch.
Anyway, this AUTO mode seems to cause the problem. If I set the monitor on "HDMI" source, disabling the Auto mode, it works fine and the monitor goes in standby as expected.

I hope this problem can be fixed someway, but it seems a problem due to some kind of incompatibility between wayland and the hardware.

---

### Post by EricDP on 2023-02-02
Interesting find. I switched off auto mode, and now mine will *sometimes* go to sleep... not always, but sometimes. I guess this is an improvement? I wonder if the screen probing for connections was triggering something in the OS, which caused the OS to turn the signal back on?

---

### Post by enricobe on 2023-02-04
It seems something related to Wayland.
I've tested on
- Fedora (Wayland GNOME) and it's the same behaviour, so it's not an Ubuntu issue.
- Kubuntu (X11 Plasma) and it works fine, so it's knot a Plasma issue.
- Windows 11 and it works fine

Maybe we should report it to Wayland developers as this is the only common cause for my understanding

---

