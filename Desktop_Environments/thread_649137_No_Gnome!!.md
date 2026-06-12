---
title: "No Gnome!!"
date: 2007-12-24
forum: Desktop Environments
---

### Post by Tomlin on 2007-12-24
I returned home after a few days away and turned on my computer. At the point where I should have seen my GUI login screen, I see a colored text screen (white, blue and red - like when you install dapper) with the message in a box:

Failed to start the X server (your graphical
interface). It is likely that it is not set
up correctly. Would you like to view the X
server output to diagnose the problem?

        <Yes>                  <No>

However, I'm popped back to text-only mode with a login prompt. I tried to log in as root, since I was planning on having to change, maybe my xorg.conf file, but it wouldn't take my password. It's the password I've used for years. Anyway, I logged in successfully as my normal user and typed "startx". It booted up in xfce!

Before I left, I had been trying to install Compiz (unsuccessfully) and must have messed something up that didn't show up until I restarted.

Everything seems to be here, I can access my email w/evolution for instance, it's just that I can't figure out how to get Gnome back.

I realize this is Christmas eve, but I know there are geeks like me who can't seem to get off their computers even for the holidays.

Thanks in advance and Happy holidays!

Tomlin

---

### Post by taurus on 2007-12-24
Log in with your username and password (not root UNLESS you have created an actual password for root), then reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```
Now, see if X can start again with the new version of /etc/X11/xorg.conf.

```
startx
```

---

### Post by Tomlin on 2007-12-24
Thanks for the reply.

No dice. I have ALL my apps, emails, firefox bookmarks, etc. Just no Gnome. Before all this happened, when the GUI login appeared, I could choose whick desktop I wanted, but now I boot directly into xfce. If I start a terminal and type gnome-session, of course it tells me I'm already running a session manager.

I went to Applications > Settings > Sessions and Startup settings and checked the box for :Display chooser on login" and checked "Launch Gnome services on startup". It didn't make any difference.

Thanks again.

Tomlin

---

### Post by adam.tropics on 2007-12-24
erm, you're not running gnome, that's xfce (xubuntu) by the sounds of it. You can run gnome stuff in there, as you have discovered. Have you got ubuntu-desktop actually installed?

---

### Post by Tomlin on 2007-12-25
Yes, I know I'm running xfce. That's my problem. I'm trying to figure out how to get my gnome desktop back.

I ran synaptic and these are shown to be installed:

gnome-desktop-data
gnome-desktop-environment
libgnome-desktop-2

How do I get the gnome desktop when I boot up? As I said earlier, my login screen used to give me the option of Gnome, KDE or xfce. I marked Gnome as the default and it always came up that way. I need to know how to get back to that login screen.

Thanks.

Tomlin

---

### Post by adam.tropics on 2007-12-25
try

```
sudo dpkg-reconfigure gdm
```

---

### Post by Hairy_Palms on 2007-12-25
if you drop to a terminal and do 
sudo /etc/init.d/gdm restart
does it give any error messages ?

---

### Post by Tomlin on 2007-12-25
Sorry for the delay...Santa stopped in :)

Adam,

"sudo dpkg-reconfigure gdm" gave me a configuration screen for gdm and kdm. I chose gdm. The terminal screen responded with:

Reloading GNOME Display Manager Configuration
Changes will take affect when all current X sessions have ended.

Approx. 5 seconds later, the screen blanked out, then popped me back to:

Failed to start the X server (your graphical
interface). It is likely that it is not set
up correctly. Would you like to view the X
server output to diagnose the problem?

<Yes> <No>

I highlited <Yes> and hit enter, which gave me:

GDM: X server not found: /usr/bin/Xgl :0 :0 -fullscreen -ac -accel
glx: pbuffer -accel xv:fbo -kb -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
Error: Command could not be executed!
Please install the X server or correct GDM configuration and restart GDM

<OK>

I hit the ENTER key and got:

The X server is now disabled. Restart GDM when it is configured correctly.

Hairy,

"sudo /etc/init.d/gdm restart" gave me:

Stopping GNOME Display Manager...     [ok]
Starting GNOME Display Manager...     [ok]

Then after 4 or 5 seconds gave me the same series of screens:

Failed to start the X server (your graphical
interface). It is likely that it is not set
up correctly. Would you like to view the X
server output to diagnose the problem?

<Yes> <No>

I highlited <Yes> and hit enter, which gave me:

GDM: X server not found: /usr/bin/Xgl :0 :0 -fullscreen -ac -accel
glx: pbuffer -accel xv:fbo -kb -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
Error: Command could not be executed!
Please install the X server or correct GDM configuration and restart GDM

<OK>

I hit the ENTER key and got:

The X server is now disabled. Restart GDM when it is configured correctly.

In BOTH cases, typing "startx" fired up xfce - right back where I started...NO gnome :confused:

Thanks again. I can't beieve this all happened when I was showing my brother-in-law how much better (Ubuntu) Linux is than M$ Vista :(

Happy holidays.

Tomlin

---

### Post by smartboyathome on 2007-12-26
For now, you can start GNOME with start-gnome (I think that is the command).

---

### Post by Tomlin on 2007-12-26
Thanks for all your help guys.

I started poking around and searched for any files containing the string "/usr/bin/Xgl" and up popped:

/etc/gdm/gdm.conf-custom which contained:

[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx: pbuffer -accel xv:fbo -kb
flexible=true

I removed EVERYTHING under [servers] and rebooted.

I'M BACK TO GNOME!!!!!

Again, thanks to all.

Tomlin

---

