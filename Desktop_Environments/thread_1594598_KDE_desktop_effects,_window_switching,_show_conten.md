---
title: "KDE desktop effects, window switching, show content in moving windows"
date: 2010-10-12
forum: Desktop Environments
---

### Post by barna on 2010-10-12
Hi,
with 10.04 and the xserver-org-video-radeon driver, I had first problems with window switching. It turned out that one needs to enable desktop effects, which were disabled by default. Even if I enabled it, it got disabled at every boot. I had to check the 'Disable compatility checks' in order to use it.

Now I upgraded to 10.10, and things do not work anymore. Even if I disable compatibility checks, and enable desktop effects, two things happen:
- I get a message 'The following desktop effects could not be activated: Box Switch, Cover Switch, etc''''
Indeed, window switching does not work as expected.
- If I quit system setting and start it again, desktop effects are indicated as disabled.

Another problem: I have unchecked 'Show content in moving windows', but still, content in moving windows is shown. After a move, the windows have stripes close to their edges.

Getting tired ...

---

### Post by barna on 2010-10-12
System Settings show:  Desktop effects are not available on this system due to the following technical issues: and then nothing is listed.

With /bin/sh --> /bin/bash, I had an error in .xsession-errors, referring to this line of /usr/bin/x-session-manager:
```

 if `laptop-detect` && [ $HEIGHT -lt 700 ] && [ $HEIGHT -gt 0 ] && [ -z $CDROM ] || [ $1 == "netbook" ]; then    

```
I could eliminate this by quoting $1: 
```

... [ "$1" == "netbook" ] ; then

```

With /bin/sh --> /bin/dash (default), there is another error in .xsession-errors:
```

Xsession: X session started for barna at Tue Oct 12 21:14:39 CEST 2010
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
[: 225: unexpected operator

```
It doesn't report the filename. Line 225 of /usr/bin/x-session-manager is the last 'fi' in this this code:
```

# In Kubuntu start plasma-netbook if the screen is small or if "netbook" parameter were passed to startkde.                                                                                    
# Starting plasma-mobile if "mobile" parameter were passed to startkde                                                                                                                         
if [ -e /usr/share/kubuntu-netbook-default-settings/share/autostart/plasma-netbook.desktop ] ; then                                                                                            
  HEIGHT=`xdpyinfo | grep dimensions | awk '{print $2}' | sed s,.*x,,`                                                                                                                         
  CDROM=`lshal | grep "storage.drive_type = 'cdrom'" | awk '{print $3}' | sed "s,',," | sed "s,',,"`                                                                                           
  if `laptop-detect` && [ $HEIGHT -lt 700 ] && [ $HEIGHT -gt 0 ] && [ -z $CDROM ] || [ "$1" == "netbook" ]; then                                                                               
    if [ ! -e ~/.config/autostart/plasma-netbook.desktop ] || `grep -q Hidden=false ~/.config/autostart/plasma-netbook.desktop`; then                                                          
      echo Small screen resolution detected, using plasma-netbook;                                                                                                                             
      export KDEDIRS=/usr/share/kubuntu-netbook-default-settings/:/usr/share/kubuntu-default-settings/kde4-profile/default/                                                                    
    fi
  fi
fi                   

```

I attached /var/log/Xorg.0.log and .xsession-errors (/bin/sh pointing to /bin/bash, therefore no error messages in this file)

---

### Post by barna on 2010-10-12
exactly the same problems if I use the fglrx driver instead of xserver-xorg-video-radeon.

---

### Post by barna on 2010-10-13
Hi, the reason was somewhere in the ~/.kde settings (inherited from kubuntu 10.04). When I removed it, I still had problems (an errormessage claiming that these effects could not be enabled, I should check my X configuration). Then I removed the fglrx proprietary driver from ATI, and then these effects work. 

However there is still a bug, if I deselect 'Show content in moving windows', then content is still shown in moving windows, but underlying windows develop stripes. I consider this as a bug...
So I kept this option checked.

---

### Post by barna on 2010-10-13
Unfortunately this was only true for a few hours. After that these effects were gone again, without any action from my side.

```

Failed to activate desktop effects using the given configuration options. Settings will be reverted to their previous values.

Check your X configuration. You may also consider changing advanced options, especially changing the compositing type

```

---

### Post by barna on 2011-02-10
These settings are needed in ~/.kde/share/config/kwinrc (in case kde would write something else, change it manually):
```
 
  [Compositing]
  CheckIsSafe=false
  DisableChecks=true
  Enabled=true
  OpenGLIsUnsafe=false

```

---

### Post by hen770 on 2011-07-05
> **barna said:**
> These settings are needed in ~/.kde/share/config/kwinrc (in case kde would write something else, change it manually):
```
 
  [Compositing]
  CheckIsSafe=false
  DisableChecks=true
  Enabled=true
  OpenGLIsUnsafe=false

```

that has worked for me !
Thank you !

---

