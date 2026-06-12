---
title: "Use VNC as a second monitor"
date: 2009-11-15
forum: Desktop Environments
---

### Post by Woek on 2009-11-15
Hi
I was wondering if the following is possible:
I have two computers sitting side by side, each with a monitor. One has ubuntu, with four desktops. I would like to have the other computer sometimes display the contents of one of the desktops of the ubuntu machine via VNC, so that I can use the extra monitor as an extended desktop. I could also connect the second monitor to the ubuntu machine, but that is a bit of a hassle, as I also use the other computer quite a bit. I'm looking for an easy, quick, cheap software solution.
Is it possible to configure a vnc server to only display the content of one of the desktops, not always the one currently visible? Or maybe I can run Xvnc and make existing windows appear there?
Thanks in advance!

---

### Post by uval on 2011-07-19
I'm also interested in this.
Anyone?

---

### Post by scorp123 on 2011-07-25
> **Woek said:**
>  One has ubuntu, with four desktops. I would like to have the other computer sometimes display the contents of one of the desktops of the ubuntu machine via VNC This isn't possible. VNC if it were configured like that would always display the same content as your Ubuntu system. You'd get 2 x screens with the same content.

> **Woek said:**
>  Is it possible to configure a vnc server to only display the content of one of the desktops, not always the one currently visible? Your question should be:

"... Is it possible to configure a vnc server to display the content of a different desktop environment and not the one that is visible on the main screen?"

YES. This is possible.

Example from one of my own systems:

The main desktop environment is GNOME. That's what you see when you turn the screen on. But I also have a 2nd desktop environment that is NOT visible on any screen unless you connect a VNC session to it.

For this I installed the LXDE desktop environment (can easily be found in the "Synaptic" package manager) and its tools and the "vnc4server" package.

Once the packages are installed you need to execute this command:
**vncpasswd**

Please choose a good and hard-to-guess password with letters, numbers, extra signs, and so on.


I then edited the file **/etc/rc.local** (needs to be done as root, so you'd use e.g. "gksu gedit /etc/rc.local" to do that) and added these lines at the bottom but before the last 2 x lines:

```
 #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#

# Launch VNC session for sysadm
/bin/su - sysadm -c "/usr/bin/vnc4server :1 -depth 16 -geometry 1200x768"

# By default this script does nothing.
exit 0

```

What that line does:

It launches a virtual VNC desktop session on a second, non-existing virtual screen ":1" (your real screen with e.g. GNOME is ":0" in Linux lingo ... but that's not the one we want) under the user "sysadm" and it sets that virtual screen to a fancy screen resolution of 1200 x 768 pixels (yeap, you can make up what you want, that screen resolution doesn't neet to correspond to real screen resolutions!).

To make really really sure we really get LXDE desktop environment when VNC gets auto-launched you need to edit a few more files.

After executing "vncpasswd" above there should now be a **".vnc"** directory in your home. In there there should be a file called **"xstartup"**. This file controls which programs and desktop environments the standalone VNC server will start. So we need to edit that one.

My file looks like this ( ~/.vnc/xstartup):

```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey

vncconfig -nowin &
/opt/teamviewer/teamviewer/6/bin/teamviewer &
lxterminal &
transmission &
lxsession &

```

What happens here is that when VNC auto-launches I first define that the screen background color should be grey, that a little VNC helper tool should be launched (it enables copy & paste of text between connected systems), that teamviewer, a terminal emulator and my favourite BitTorrent program should be launched, and that I want it all managed by the LXDE session. The ampersand "&" after each line makes sure that the programs are executed in the background and that the script continues regardless whether or not the programs that were launched are finished executing or not (without the "&" the script would get stuck after each line and wait for the programs to finish before triggering the next program on the following line ... )


Sorry for the long text but it's really easy. With above trick I can use my normal GNOME desktop and plus I can use the VNC connection as additional desktop. And if I lock the physical screen it doesn't affect the programs that I launched in my VNC session, they will continue to work regardless whether I am connected or not.

So yes, this is a good way to leave programs running in the background without leaving your physical screen unlocked.

However: please be aware that VNC is very very *INSECURE* as protocol. Do not open your firewall/router for VNC access to the outside world, only use this within your own LAN, OK? For secure remote access there are better solutions than VNC. I for example use Teamviewer ([www.teamviewer.com](www.teamviewer.com)) for this.

Hope this helped?

---

### Post by onecsguy on 2012-03-06
> **scorp123 said:**
> This isn't possible. VNC if it were configured like that would always display the same content as your Ubuntu system. You'd get 2 x screens with the same content.


Uhmmmm!!!, this is VERY possible ... Simply configure a multiscreen desktop with the main computer but set the virtual screen of monitor 2 to a large size 4096x1080 with PA=anning.  Then simply VNC into the computer from the other computer, disconnect monitor 2 (so you dont actually have annoying panning) and connect it to the laptop or w/e other device, scroll to where you want the virtual screen to be in the VNC client, make the virtual monitor 2 screen as large as your computer can handle and scroll to various positions using various computers, wala, multi-nscreen Ubuntu desktop without seperate X sessions, drag windows between the computers etc ... you would want Gigabit Networking or Wireless N, and enable JPEG compression to get best performance.  I have an Android Tablet and Ubuntu laptop as seperate screens for my desktop + the 2nd monitor from my desktop ... 4 screens one Desktop Environment!!!

Some of you open source guys cough "scorp123", dont be too quick to shoot down solutions (btw, this should be implemented Nativity they should call it VND Virtual Network Display, guess I have a source forge project to start =D)

---

### Post by markbl on 2012-03-06
Look at x11vnc to remote a desktop (or part of) to another pc. Look at quick-synergy to multiplex your keyboard and mouse across pc's.

---

### Post by Bobswell on 2012-09-14
I'm a total noob and was wondering if anyone could tell me if there's a way to use my android tablet as a second monitor.   I'm using Ubuntu 12.04 on my laptop.
Thanks,

---

### Post by RichardUK on 2012-09-14
Have you looked a Synergy?
[http://synergy-foss.org/](http://synergy-foss.org/)

Virtual KVM. Not quite the same as you want as the app's running on one PC will not show on the other but if the other PC is just for displaying docs / email / playing music then this will do. Will be faster.

---

### Post by kjans123 on 2012-12-22
It **is** possible. I have done it once. As it was many years ago, so I do not remember the exact commands, but the I try to list the steps.
First, let's assume the primary machine does have a screen resolution of 1280x800 and the secondary machine that you want to extend your desktop to over VNC has screen resolution of 1280x1024 and you want the extended screen to be right of your primary screen.

At least that was my configuration. Also, in my case the primary machine had an Intel video card, so it might not work with any other graphics drivers, I do not know, haven't tested.

Anyway, here are the steps:
[LIST]
[*] First, I used xrandr to make a bigger virtual screen with size of 1280x800 + 1280x1024 = 2560x1024 (we extend it horizontally, the vertical resolution is the vertical resolution of the monitor with the biggest vertical resolution (yeah, I know, this is not one the best sentences I have written, but hope you get the idea :D))

[*] Now, that the screen is bigger than your primary monitor, you have to make sure there is no panning or any other unwanted "feature" activated and also that the  coordinates of your primary monitor's top left corner are 0x0.

[*] Now you can start the Xvnc vnc server. Configure it to have the screen resolution of your secondary monitor (in our case 1280x1024) and position it so that it covers the unused portion of your screen (in this case that will be 1281x0)

[*] Configure your firewall and try to connect. If everything is working like it should, you are now able to use any device with a  VNC client software as your secondary monitor. The speed of this link depends on the network you are using and the size of the remote screen. For example, using an Ethernet connection you should get a decent enough speed for writing a text file or surfing the Internet. Don't expect to watch any videos on your secondary monitor though. :P
[/LIST]

Again, I do not guarantee that it will work for everyone and with every graphics driver (especially the proprietary drivers) or with any newer drivers at all, as I have not tested it for years.

Also, if you get it to work, it should not be too hard to write a shell script that does (and undoes) it for you. In this case, do not forget to post it. :P

Hope this is useful to someone.

EDIT: Just tried it on my laptop. The magic command for making your virtual screen bigger than your monitor is
```
xrandr --fb <width>x<height>
```
My laptop has a nVidia graphics card and whenever I make the virtual screen bigger than my monitor, the nVidia proprietary driver seems to automatically enable panning and I can find no way to turn it off.

---

### Post by chx1975 on 2013-01-12
> **kjans123 said:**
> [*] Now you can start the Xvnc vnc server. Configure it to have the screen resolution of your secondary monitor (in our case 1280x1024) and position it so that it covers the unused portion of your screen (in this case that will be 1281x0)


Your trick is really nice but I think it worths mentioning this step needs the x11vnc server and the clip option. There are other vnc servers but I doubt you can do this with them.

---

### Post by kjans123 on 2013-01-13
> **chx1975 said:**
> Your trick is really nice but I think it worths mentioning this step needs the x11vnc server and the clip option. There are other vnc servers but I doubt you can do this with them.

Sorry, my bad. :oops:
x11vnc it is.

---

### Post by saou on 2013-01-27
This "xrandr --fb" and "x11vnc -clip" combo almost works:   I can extend my ubuntu desktop to the android tablet and drag a window from ubuntu to the tablet, until the mouse cursor hits the right edge of the laptop screen, at which point the cursor stops and I can't drag the window any further.   As I move my laptop cursor along the right side, the tablet cursor matches the vertical motion but not the horizontal motion; in particular, the tablet cursor stays on the left edge of the tablet.

Just to be clear:  I am running a vnc viewer on the tablet, as such it has a cursor (for the remote desktop) and a pointer (for the tablet).  I can move the tablet pointer, but not the remote desktop cursor.

Any suggestions for extending the movement of the cursor from ubuntu to the tablet?   THANKS!

---

### Post by henyojess on 2013-04-30
Saou, have you had any success with this? Am using ubuntu 12.04LTS and the standard Unity window manager and am experiencing the same thing even after extending the screen with xrandr --fb 3968x1080

---

### Post by henyojess on 2013-04-30
another approach could be to run an lxc container + Xvnc + synergys but it seems overcomplicated?

---

### Post by jiehanzheng on 2013-06-12
Any news on this?  Is there a way to get ANY window manager to draw windows beyond usual boundaries?

---

### Post by Bachi on 2013-06-19
Just a theory (I'm a noob when it comes to X11 configuration): 

- I can configure a second display just as in a dual monitor setup. Windows sharing etc works perfectly fine that way.
- I could connect to the second display using VNC client from the remote machine (I assume)
- When removing the second monitor, I should have a perfect remote display setup?

I assume this should work without having to connect a real second monitor in the first place. 

I might be completely wrong, but it sounds at least reasonable and easier than combining x sessions and the like...

---

