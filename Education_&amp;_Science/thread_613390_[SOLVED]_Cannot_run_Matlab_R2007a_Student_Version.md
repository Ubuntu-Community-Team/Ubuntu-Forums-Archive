---
title: "[SOLVED] Cannot run Matlab R2007a Student Version"
date: 2007-11-14
forum: Education &amp; Science
---

### Post by Eezyville on 2007-11-14
I cannot get the license manager to work! When I install it I get this error:
> SR_TMW_Archive license checkout failed
No such feature exist.
FLEXnet Licensing error: -5,357

I've look all over for a few days and haven't found a solution. I got the license information for my machine from MathWorks by entering in my MAC address. I don't understand what to do. :confused: I made my license.dat file like they told me to, namely I pasted my information right before the 
```
# END------cut here------CUT HERE-----END
```
line. Then I put that file in the directory where the install file is. It won't work.

halp](*,)

---

### Post by Eezyville on 2007-11-14
OK so I got the license manager thing to work and it installed but when I run matlab i get this error:
```
License checkout failed.
License Manager Error -9
The HostID of this machine does not match the HostID of the license file. 
Reinstalling may resolve this error.

Troubleshoot this issue by visiting: 
http://www.mathworks.com/support/lme9a

Diagnostic Information:
Feature: SR_MATLAB 
License path: /usr/local/matlab74_sv/etc/license.dat:/usr/local/matlab74_sv/etc/*.lic: 
FLEXnet Licensing error: -9,57. System Error: 19

```
](*,)

What happened. I used my MAC address like the guide said. I used the one for my wifi card which is my eth1, I don't have a eth0. Should it had been my LAN MAC address?

---

### Post by Eezyville on 2008-01-05
Ok I think I solved this problem. What I did was I copied the dvd into a folder in my home directory and called that folder matlab. In that folder I got my license information and made a license.dat file, I put that file in the folder. next I ran these commands:
```

chmod 755 -R /home/chris/matlab
sudo /home/chris/matlab/install_unix.sh &
```

The problem came when I tried to install matlab into a folder in my /usr/local directory. I needed to install it in my home directory for some reason.:confused: So I just made a new directory called .matlab so that its hidden. Now once i got it installed I needed to set it up to run in beryl and to run simulink because it will crash if you run simulink. I found threads in this forum to help, you basically add a few lines to the matlab calling code thing to run in beryl and you install sun java 6 to run simulink. But yeah its kinda solved, I'll install it again and update what I did. HP wiped my hdd when I sent it in for repairs.:(

---

