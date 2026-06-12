---
title: "VNC only on active display"
date: 2009-04-09
forum: General Help
---

### Post by MP3HiFi on 2009-04-09
Hi,

I have a question about VNC. I am using x11vnc. I have 2 xserver running. One for gdm (display 0 on terminal 7) and the other for xbmc (display 1 on terminal 9).

When xbmc is active I only get a black screen in my vnc viewer. When gdm is active I get the screen on my vnc viewer. 

Ho do I always get a screen for gdm, even when xbmc is the active screen?

Thanks
Martin

---

### Post by soltanis on 2009-04-09
Determine which display GDM is running on (say for example, :0), then modify the command that runs x11vnc.

Use:

```

# in this example, gdm is running on display :0
x11vnc -display :0

```

In general, programs that use X (or start with x, i.e. xterm) have the -display option allowing you to specify which display to use.

---

### Post by MP3HiFi on 2009-04-09
Hi,

I used exactly that parameter:

x11vnc -display :0

I only see the desktop if the diplay is shown on the monitor.
When switching to Display 2 via Alt + Ctrl + F9 the desktop in the vncviewer gets black.

---

### Post by krunge on 2009-04-09
> **MP3HiFi said:**
> 
I have a question about VNC. I am using x11vnc. I have 2 xserver running. One for gdm (display 0 on terminal 7) and the other for xbmc (display 1 on terminal 9).

When xbmc is active I only get a black screen in my vnc viewer. When gdm is active I get the screen on my vnc viewer. 

How do I always get a screen for gdm, even when xbmc is the active screen?


I believe this is impossible to do.  Applications running on the Linux Virtual terminals must (politely) share the graphics framebuffer memory.  

Only the application that is on the active VT can read and write to the framebuffer (and also read input from mouse/keyboard.)  The other app (on inactive VT) cannot and so you either get a garbage or unchanging screen or a black screen. 

Long ago I tried using the Option ShadowFB = "true" setting in xorg.conf in the hope that the screen would still be viewable for the inactive console.  That didn't work either.  Why don't you try it now with more modern Xorg to see if they implemented it since then?

More info here: [http://www.karlrunge.com/x11vnc/faq.html#faq-linuxvc](http://www.karlrunge.com/x11vnc/faq.html#faq-linuxvc)

---

### Post by MP3HiFi on 2009-04-10
Hi,

thanks for your answer, but that is exactly the answer I didn't want. Seems to be impossible doing this.

What I like to do is running xbmc on my tv for viewing videos etc. I the background I would like to run applications like torrent, wine etc. on the system controlling them with vnc. But this seems to be impossible.

Perhaps it works with a vm running ubuntu to and connect to that via vnc.

Has anybody an other solution or idea.

Martin

---

### Post by krunge on 2009-04-10
> **MP3HiFi said:**
> 
What I like to do is running xbmc on my tv for viewing videos etc. I the background I would like to run applications like torrent, wine etc. on the system controlling them with vnc. But this seems to be impossible.

Perhaps it works with a vm running ubuntu to and connect to that via vnc.

Has anybody an other solution or idea.


No need for a VM, simply run vncserver/Xvnc or NX or x11vnc+Xvfb: [http://www.karlrunge.com/x11vnc/faq.html#faq-xvfb](http://www.karlrunge.com/x11vnc/faq.html#faq-xvfb)

Then you have a virtual X session (living in RAM only, not using the framebuffer memory) you can connect to from anywhere.  You run those apps in the virtual X session.

---

### Post by MP3HiFi on 2009-04-10
Hi, seems to be a solution. Tried a quicky with Xvnc and it works. But now there are more questions than before. I have a running gnome-session startet by gdm. Hot to connect that session to the Xvnc or perhaps the solution with the dummy driver. Is that possible at all or do I have to put it all in the ~/.vnc/Xstartup

In hope there is an easy solution.

Martin

---

### Post by MP3HiFi on 2009-04-11
Hi,

I got it. I have a script that rund in init.d. It calls:


```
case "$1" in
start) echo -n "Starting VNCDesktop"
 setterm -blank 0
 sudo -H -u desktop vncserver :1 &
 esac
exit 0
```

In the home of user desktop ther is the file home/desktop/.vnc/xstartup

```
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#twm &
gnome-session
```

Don't forget setting a password for the vncserver.

---

### Post by drinktea on 2010-07-31
hi i got the same question
but i can't use xsession to solve it
because the xsession can't load graphic card driver as the X-window do
is there any new solution up to now
is it possible to create a new tty with independent graphic framebuffer?

---

