---
title: "issue launching apps from fluxbox menu"
date: 2008-03-23
forum: Desktop Environments
---

### Post by guko1111 on 2008-03-23
I added the program 'wifi-radar' to my fluxbox menu and can't get it to start when selecting it. Here is my ~/.fluxbox/menu

[PHP][begin] (Fluxbox)

   [submenu] (Applications) {}
      [submenu] (Accessibility) {}
         [exec] (Xmag) {xmag} <>
      [end]
      [submenu] (Editors) {}
         [exec] (Nano) { x-terminal-emulator -T "Nano" -e /bin/nano} </usr/share/nano/nano-menu.xpm>
         [exec] (Xedit) {xedit} <>
      [end]
      [submenu] (File Management) {}
         [exec] (Thunar) {/usr/bin/thunar} <>
      [end]
      [submenu] (Graphics) {}
         [exec] (X Window Snapshot) {xwd | xwud} <>
      [end]
      [submenu] (Network) {}
         [submenu] (Communication) {}
            [exec] (Xbiff) {xbiff} <>
         [end]
	 [exec] (wifi radar) {wifi-radar} </usr/share/pixmaps/wifi-radar.png>
         [exec] (Telnet) { x-terminal-emulator -T "Telnet" -e /usr/bin/telnet} <>
         [exec] (w3m) { x-terminal-emulator -T "w3m" -e /usr/bin/w3m /usr/share/doc/w3m/MANUAL.html} <>
         [submenu] (Web Browsing) {}
            [exec] (Firefox 3 Browser) {/usr/bin/firefox-3.0} </usr/share/pixmaps/firefox-3.0.png>
         [end]
      [end]
      [submenu] (Programming) {}
         [exec] (Python (v2.5\)) { x-terminal-emulator -T "Python (v2.5)" -e /usr/bin/python2.5} </usr/share/pixmaps/python2.5.xpm>
      [end]
      [submenu] (Science) {}
         [submenu] (Mathematics) {}
            [exec] (Xcalc) {xcalc} <>
         [end]
      [end]
      [submenu] (Shells) {}
         [exec] (Bash) { x-terminal-emulator -T "Bash" -e /bin/bash --login} <>
         [exec] (Dash) { x-terminal-emulator -T "Dash" -e /bin/dash -i} <>
         [exec] (Sh) { x-terminal-emulator -T "Sh" -e /bin/sh --login} <>
      [end]
      [submenu] (System) {}
         [submenu] (Administration) {}
            [exec] (alsaconf) { x-terminal-emulator -T "alsaconf" -e su-to-root -p root -c /usr/sbin/alsaconf} <>
            [exec] (Aptitude) { x-terminal-emulator -T "Aptitude" -e /usr/bin/aptitude} <>
            [exec] (Debian Task selector) { x-terminal-emulator -T "Debian Task selector" -e su-to-root -c tasksel} <>
            [exec] (DSL/PPPoE configuration tool) { x-terminal-emulator -T "DSL/PPPoE configuration tool" -e /usr/sbin/pppoeconf} </usr/share/pixmaps/pppoeconf.xpm>
            [exec] (Editres) {editres} <>
            [exec] (pppconfig) { x-terminal-emulator -T "pppconfig" -e su-to-root -p root -c /usr/sbin/pppconfig} <>
            [exec] (Xclipboard) {xclipboard} <>
            [exec] (Xfontsel) {xfontsel} <>
            [exec] (Xkill) {xkill} <>
            [exec] (Xrefresh) {xrefresh} <>
         [end]
         [submenu] (Hardware) {}
            [exec] (Xvidtune) {xvidtune} <>
         [end]
         [submenu] (Monitoring) {}
            [exec] (Pstree) { x-terminal-emulator -T "Pstree" -e /usr/bin/pstree.x11} </usr/share/pixmaps/pstree16.xpm>
            [exec] (Top) { x-terminal-emulator -T "Top" -e /usr/bin/top} <>
            [exec] (Xconsole) {xconsole -file /dev/xconsole} <>
            [exec] (Xev) {x-terminal-emulator -e xev} <>
            [exec] (Xload) {xload} <>
         [end]
      [end]
      [submenu] (Terminal Emulators) {}
         [exec] (XTerm) {xterm} </usr/share/pixmaps/xterm-color_32x32.xpm>
         [exec] (X-Terminal as root (GKsu\)) {/usr/bin/gksu -u root /usr/bin/x-terminal-emulator} </usr/share/pixmaps/gksu-debian.xpm>
         [exec] (XTerm (Unicode\)) {uxterm} </usr/share/pixmaps/xterm-color_32x32.xpm>
      [end]
      [submenu] (Tools) {}
         [exec] (fluxconf) {/usr/bin/fluxconf} <>
         [exec] (fluxkeys) {/usr/bin/fluxkeys} <>
         [exec] (fluxmenu) {/usr/bin/fluxmenu} <>
      [end]
      [submenu] (Viewers) {}
         [exec] (Xditview) {xditview} <>
      [end]
   [end]
   [submenu] (Games) {}
      [submenu] (Toys) {}
         [exec] (Oclock) {oclock} <>
         [exec] (Xclock (analog\)) {xclock -analog} <>
         [exec] (Xclock (digital\)) {xclock -digital -update 1} <>
         [exec] (Xeyes) {xeyes} <>
         [exec] (Xlogo) {xlogo} <>
      [end]

   [end]
   [submenu] (Help) {}
      [exec] (Info) { x-terminal-emulator -T "Info" -e info} <>
      [exec] (Xman) {xman} <>
   [end]
   [submenu] (Window Managers) {}
      [restart] (FluxBox)  {/usr/bin/startfluxbox}
   [end]

   [config] (Configuration)
   [submenu] (Styles) {}
      [stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
   [end]
   [workspaces] (Workspaces)
   [reconfig] (Reconfigure)
   [restart] (Restart)
   [exit] (Exit)

[end]
[/PHP]
The entry I added is under the applications/network menus. I can still run wifi-radar from terminal using the command "sudo wifi-radar" but it won't launch from the menu. Any help would be great, thanks.

---

### Post by kerry_s on 2008-03-23
does it need to be started as root?
if so->
[exec] (wifi radar) {gksudo wifi-radar} </usr/share/pixmaps/wifi-radar.png> 

you should add wifi-radar to your sudoers with no password so you don't have to type in a password.

sudo visudo
user    ALL=NOPASSWD: /usr/bin/wifi-radar

"user" is your name

then you could
[exec] (wifi radar) {sudo wifi-radar} </usr/share/pixmaps/wifi-radar.png>

i run a few things with sudo and no password, here's what mine looks like.

---

### Post by guko1111 on 2008-03-24
kerry_s,
   Adding "gk" made it launch. To get it to not ask for the password I ended up editing the file a bit differently. I had to use "nano" and it still needed "gk" but it's launching now without the need to enter the password. I wouldn't have been able to figure that out without your help, Thank you!

---

### Post by guko1111 on 2008-03-24
I guess it was launching without the need for the password in that session only. It will only launch with the "gk" in the menu file. I tried editing my sudoers file like you mentioned so I wouldn't need the password but it isn't working for some reason. This is what I added to the sudoers file

myusername ALL=NOPASSWD: /usr/sbin/wifi-radar  
 
I have also tried variations of this like,

myusername ALL=(ALL) NOPASSWD: /usr/sbin/wifi-radar

after editing the sudoer file in one of those ways I edit the menu file and get rid of the GK to launch wifi radar and it won't launch anymore. Any ideas?:confused:

---

### Post by Patb on 2008-03-25
> **guko1111 said:**
> after editing the sudoer file in one of those ways I edit the menu file and get rid of the GK to launch wifi radar and it won't launch anymore. Any ideas?:confused:
Guko, leave the command in your menu as [COLOR="Sienna"]gksudo[/COLOR] not [COLOR="Sienna"]sudo[/COLOR].  I have had the same issue with Fluxbox menu in that admin graphical commands have to be started with gksudo (or gksu) not sudo.  

But maybe that's a good thing because gksudo is preferable.  See [this thread]("http://ubuntuforums.org/showthread.php?t=730277") and [this link]("http://www.psychocats.net/ubuntu/graphicalsudo").

Cheers, Pat.

---

### Post by kerry_s on 2008-03-25
use> myusername ALL=NOPASSWD: /usr/sbin/wifi-radar 
but leave the gksudo, it should not ask for your password, because it's still a sudo command.

---

### Post by guko1111 on 2008-03-25
I made sure to use 
"myusername ALL=NOPASSWD: /usr/sbin/wifi-radar" for sudoers and left "gksudo" for the menu file but it still asks for the password. Odd.

---

### Post by Patb on 2008-03-26
Guko, could you post the output of:
```
sudo tail /etc/sudoers
```
Cheers, Pat

---

### Post by kerry_s on 2008-03-26
make sure you leave 1 blank line under your entry to close it out.

---

### Post by guko1111 on 2008-03-26
# User privilege specification
root     ALL=(ALL) ALL
user    ALL=NOPASSWD: /usr/sbin/wifi-radar

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
# Passwordless shutdown and reboot
user ALL=(ALL) NOPASSWD: /sbin/shutdown -h now, /sbin/reboot, /usr/sbin/synaptic

---

### Post by kerry_s on 2008-03-27
just add it to the end of your "shurtdown and reboot" line, if those work.

---

### Post by guko1111 on 2008-03-27
kerry_s and Patb I switched to wicd for my network manager and it's working great(wifi-radar would struggle to find an IP address and I couldn't get WPA2 to work anyway). I was able to learn how to edit sudoers and that I may need the gksudo command sometimes so it wasn't all for nothing! Thanks

---

### Post by guko1111 on 2008-03-27
kerry_s I actually did try adding it to the shutdown and reboot lines and it still wouldn't work so I decided then to just try something new. :)

---

