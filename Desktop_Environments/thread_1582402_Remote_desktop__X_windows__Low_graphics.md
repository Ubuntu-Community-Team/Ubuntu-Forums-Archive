---
title: "Remote desktop / X windows / Low graphics"
date: 2010-09-26
forum: Desktop Environments
---

### Post by spmurphy on 2010-09-26
Hi,

I'm trying to set up a machine without a monitor. It has a video card in it but it won't have a monitor connected.

Basically I want to press the button on the front, it boots up and I can remote desktop onto it from my main machine. I'm assuming this means it needs X.

The problem I have is that with no monitor attached, it boots but complains about "low graphics". I only see this complaint after I re-connect the monitor cable. My remote desktop from the other machine works fine until I come to shut it down whereupon it just sits there presumably waiting on the display that's not connected for someone to fix the low graphics "problem."

Is there a way to stop it moaning about low graphics? Or, better yet, have a machine without a video card at all yet still be able to remote desktop onto it? Is there some kind of virtual framebuffer version of X I could use that would allow this?

---

### Post by tom4everitt on 2010-09-26
If I understand X correctly, you shouldn't need a graphics card in the monitor-less computer. 

The graphics will be dealt with by the X server, which, confusingly enough, resides on the computer with a monitor. The monitor-less computer should have an X-client installed. So generally the server should have an X-client installed, and the client connecting to the server should have an X-server. 

So install Ubuntu Server on the monitor-less computer, and make sure it has an X-client installed. You may even remove the graphics card from that computer, since you'll probably have better use for it elsewhere.

---

### Post by Chesamo on 2010-09-27
I think tom4everitt is a little mistaken about what you want, but they did touch on what you needed.

The short answer is: no. I've been trying to do this very same thing for a long time, and I stopped being able to do it in 9.10 because of the X11 update. X now configures itself intrinsically by detecting the attached monitor and video card. Something you really need would be X forwarding over SSH, performed via ```
ssh username@host -X
``` Note that the flag is *capital* X, not lowercase. You can install the command-line Ubuntu system, then install graphical utilities, without installing X (or, more specifically, installing xinit). Then the display information is forwarded to your local machine from the remote machine. It's a bit slow and buggy at times, but that's dependent on your connection.

---

### Post by spmurphy on 2010-09-27
Hi, and thank you for your replies.

Do you know if there's any way to turn off the auto-config? Or pin the one I can't see to low graphics?

Maybe if I could do that, it would stop complaining. My guess was that because the one I can't see was busy complaining and no-one had acknowledged it, that's why I couldn't shut it down from my remote connection. I may faff with that.

We used to have "real" X-terms at work but it was a long time ago. I relate a little of what you're saying (tom) to that so I kinda see what you mean.

---

### Post by macanudo on 2010-09-28
> **spmurphy said:**
> Hi, and thank you for your replies.

Do you know if there's any way to turn off the auto-config? Or pin the one I can't see to low graphics?

Maybe if I could do that, it would stop complaining. My guess was that because the one I can't see was busy complaining and no-one had acknowledged it, that's why I couldn't shut it down from my remote connection. I may faff with that.

We used to have "real" X-terms at work but it was a long time ago. I relate a little of what you're saying (tom) to that so I kinda see what you mean.


No expert here.. but shouldnt you just be able to generate an /etc/X11/xorg.conf ? try
```
sudo Xorg -configure
```
& copy the created file to /etc/X11

---

### Post by ruucaa on 2011-09-17
Hi,

I realize this is an old thread, but i think i should describe the way i got it to work for me, since there is a lot of questioning regarding this matter.

On ubuntu server:

Using

ruucaa@server:$ uname -a
Linux marishka 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux
ruucaa@server:$

 ruucaa@server:$ ps aux | grep vnc
cipher    1093  0.0  0.4  16888  9524 ?        S    15:49   0:00 Xvnc4 :1 -desktop marishka-vnc-server -auth /home/cipher/.Xauthority -geometry 1280x800 -depth 24 -rfbwait 30000 -rfbauth /home/cipher/.vnc/passwd -rfbport 5901 -pn -fp /usr/X11R6/lib/X11/fonts/Type1/,/usr/X11R6/lib/X11/fonts/Speedo/,/usr/X11R6/lib/X11/fonts/misc/,/usr/X11R6/lib/X11/fonts/75dpi/,/usr/X11R6/lib/X11/fonts/100dpi/,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/75dpi/,/usr/share/fonts/X11/100dpi/ -co /etc/X11/rgb


Initiated at boot by this script:

#################################################################
#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          vncserver
# Required-Start:    networking
# Default-Start:     3 4 5
# Default-Stop:      0 6
### END INIT INFO

PATH="$PATH:/usr/X11R6/bin/"

# The Username:Group that will run VNC
export USER="ruucaa"
#${RUNAS}

# The display that VNC will use
DISPLAY="1"

# Color depth (between 8 and 32)
DEPTH="24"

# The Desktop geometry to use.
#GEOMETRY="<WIDTH>x<HEIGHT>"
#GEOMETRY="800x600"
GEOMETRY="1280x800" ---> this is my laptop's screen resolution. because i want it to fit on my laptop's monitor i use the laptop's monitor definition.
#GEOMETRY="1280x1024"

# The name that the VNC Desktop will have.
NAME="server-vnc-server"

OPTIONS="-name ${NAME} -depth ${DEPTH} -geometry ${GEOMETRY} :${DISPLAY}"

. /lib/lsb/init-functions

case "$1" in
start)
log_action_begin_msg "Starting vncserver for user '${USER}' on localhost:${DISPLAY}"
su ${USER} -c "/usr/bin/vncserver ${OPTIONS}"
;;

stop)
log_action_begin_msg "Stoping vncserver for user '${USER}' on localhost:${DISPLAY}"
su ${USER} -c "/usr/bin/vncserver -kill :${DISPLAY}"
;;

restart)
$0 stop
$0 start
;;
esac

exit 0

#################################################################

Still on the server there are the following files:

ruucaa@server:~$ cat .vnc/xstartup 
/usr/bin/gnome-session &


ruucaa@server:~$ cat /etc/X11/xorg.conf
Section "Device"
Identifier "VNC Device"
Driver "vesa"
EndSection

Section "Screen"
Identifier "VNC Screen"
Device "VNC Device"
Monitor "VNC Monitor"
SubSection "Display"
#Modes "1280x1024"
EndSubSection
EndSection

Section "Monitor"
Identifier "VNC Monitor"
HorizSync 30-70
VertRefresh 50-75
EndSection


On the client machine:

xvnc4viewer 192.168.1.132:1 -fullscreen

And I can access my desktop in fullscreen mode as if i was using a monitor attached to it directly.

Anyone as any questions regarding this matter, i'll be happy to help,

Regards

:)

---

### Post by pavi_elex on 2011-11-08
type 
xterm
in both systems
and try to access through ssh (sftp).
or
places --> connect to server

---

### Post by nothingspecial on 2011-11-08
Thank you for your input.

But old threads should not be brought back to life.

Closed.

---

