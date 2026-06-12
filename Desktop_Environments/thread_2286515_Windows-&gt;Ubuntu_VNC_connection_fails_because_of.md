---
title: "Windows-&gt;Ubuntu VNC connection fails because of no .xsession file"
date: 2015-07-12
forum: Desktop Environments
---

### Post by David_M._Karr on 2015-07-12
I've been working with a remote Ubuntu box for a bit, with only ssh shell access.

I'm now trying to set up a VNC connection from my Win7 box to this Ubuntu box.  I installed "tightvncserver" on the Ubuntu box and started it.  I ran TightVNCViewer on my Win7 box.  I connected to the VNC port and I got a display with a grey background, black "X" cursor, and an error dialog basically saying that a "~/.xsession" file was not found.  I verified that  ~/.xsession-errors on the remote box said the same thing.

The error message is accurate.  I don't have a ~/.xsession file.  What should I have in this file to get me a working desktop environment?

---

### Post by TheFu on 2015-07-13
Not the answer you want, but I think it is a better solution.

For remote access, most people I know are switching to x2go. It uses ssh tunnels for all traffic by default and the performance is 2-3x faster than either RDP or VNC options.  There is a PPA, install the "server" on the remote system and the "client" on the local machine. On Windows, you may want to install some fonts too.  People say x2go is like night and day compared to VNC.  It uses ssh ports and credentials and completely honors the ~/.ssh/config settings (easy way to use non-standard ports or change userids).

The only negative for some people is that 3D accel desktops like Unity are NOT supported. That means XFCE4 or LXDE or a plain WM need to be installed on the remote box. Those are just 2-3 min, so not a big deal.

I don't have a .xsession - either. Did you startup the vnc-server process with appropriate settings? [https://www.howtoforge.com/how-to-install-vnc-server-on-ubuntu-14.04](https://www.howtoforge.com/how-to-install-vnc-server-on-ubuntu-14.04) might help.

Some places only allow localhost connections to VNC, so people are forced to use ssh tunnels to make a connection.  [https://superuser.com/questions/715604/vncserver-localhost-and-ssh-tunneling](https://superuser.com/questions/715604/vncserver-localhost-and-ssh-tunneling) explains the ssh/vnc options.

I really hope you'll consider x2go. There are clients for Windows, OSX and Linux. It really does work well and faster than other alternatives for internet remote desktops.  For LAN remote desktops, people are switching to Spice, but I think that required using KVM and virtualization.

---

### Post by steeldriver on 2015-07-13
What are the contents of your ~/.vnc/xstartup file on the remote machine? I don't recall tightvnc looking for a ~/.xsession... unless ~/.vnc/xstartup tells it to do so?

---

### Post by David_M._Karr on 2015-07-13
Here's my ~/.vnc/xstartup file:
> #!/bin/sh
xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession

Looks like it has "placeholders" for a terminal window and window manager.

---

### Post by David_M._Karr on 2015-07-13
> **TheFu said:**
> Not the answer you want, but I think it is a better solution.

For remote access, most people I know are switching to x2go. It uses ssh tunnels for all traffic by default and the performance is 2-3x faster than either RDP or VNC options.  There is a PPA, install the "server" on the remote system and the "client" on the local machine. On Windows, you may want to install some fonts too.  People say x2go is like night and day compared to VNC.  It uses ssh ports and credentials and completely honors the ~/.ssh/config settings (easy way to use non-standard ports or change userids).

...

I really hope you'll consider x2go. There are clients for Windows, OSX and Linux. It really does work well and faster than other alternatives for internet remote desktops.  For LAN remote desktops, people are switching to Spice, but I think that required using KVM and virtualization.

Thanks, but I can't really justify looking for an alternate solution for increased performance when I haven't even gotten the first solution to run yet. I need to walk before I can run.  Nevertheless, I'll look at some info on this just so I know something about it.

---

### Post by TheFu on 2015-07-13
Completely understand - x2go really is 10x easier to get working, however.

You don't want that /etc/X11/Xsession in the xstartup - call a WM that is installed there instead. I use 
**/usr/bin/fvwm &** or **/usr/bin/openbox &** at the end. Bet it will work - provided the program(s) is/are installed.

Good luck!

---

### Post by steeldriver on 2015-07-13
That looks like the kind of xstartup you'd want if you were running it in a old school configuration where you logged into local sessions with just a console and then manually started a GUI session using startx, and you want VNC to start the same GUI session remotely as locally

In a more typical modern setup, the local GUI session is determined at login time via a display manager such as  lightdm or gdm, and users typically don't have a ~/.xsession file. In that case, it's more usual to initiate a session directly in the xstartup file. There is an example of a custom xstartup file in the community wiki that you can use and modify [B]NB the ubuntu-2d session is probably no longer a valid session type post 12.04, you will need to choose a session type that is actually installed on your remote system
[/B]
[https://help.ubuntu.com/community/VNC/Servers#Customising_your_session](https://help.ubuntu.com/community/VNC/Servers#Customising_your_session)

FYI here is one that I use (avoiding Ubuntu/gnome sessions altogether - I find that lighter desktops work better for me): it tries for an XFCE4 session, dropping through to LXDE then plain OpenBox if necessary and finally to a default terminal emulator / window manager as an absolute last fallback

```

#!/bin/sh

MODE="xfce4"

#Uncommment this line if using Gnome and your keyboard mappings are incorrect.
#export XKL_XMODMAP_DISABLE=1

# Load X resources (if any)
if [ -r "$HOME/.Xresources" ]; then
  xrdb "$HOME/.Xresources"
fi

case $MODE in

xfce4)
        if which startxfce4 > /dev/null; then
                exec startxfce4
        fi
        ;;

lxde)
        if which startlxde > /dev/null; then
                exec startlxde
        fi
        ;;

openbox)
        if which openbox-session > /dev/null; then
                exec openbox-session
        fi
        ;;

*)
        echo "Falling back to default minimal X session"
    ;;

esac

xsetroot -solid "#DAB082"
x-terminal-emulator -geometry "80x24+10+10" -ls -title " Desktop" &
x-window-manager &

```

Of course if you do want to do the oldschool setup, you could just leave your ~/.vnc/xstartup as-is, and create a minimal ~/.xsession file: one that I've used in the past for a plain Lubuntu session is simply

```

lxsession -e LXDE -s Lubuntu

```

TBH I don't know the difference between running startlxde versus simply invoking an lxsession - don't rely on what I've done as "best practice"

---

### Post by David_M._Karr on 2015-07-13
Shouldn't that be "exec /usr/bin/fvwm" or "exec /usr/bin/openbox"?

---

### Post by David_M._Karr on 2015-07-13
steeldriver, I'm not sure how to interpret much of that information.  It's not clear to me that I need something more complex than what I have.  I thought what I'd come up with so far was working fine, although there is one big problem with it, which I'll describe here.

My current "xstartup" looks like this:
> #!/bin/sh
xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
#/etc/X11/Xsession
exec /usr/bin/fvwm
#exec /usr/bin/openbox


I installed xterm and fvwm, and now when this starts up, I can select xterm from the context menu and then run the GUI application I've been trying to get to all this time (virt-manager).  I suppose I could put "/usr/bin/xterm &" in the xstartup, but that's not a problem.

After working with this for a while, I discovered a very annoying symptom.  I moved away from my Windows TightVNCViewer client to do other things for a minute, and when I returned to the TightVNCViewer window again, it was just a grey screen.  The applications are still running, their windows have just disappeared.  In fact, I saw this happen just now when I created another xterm and then moved my cursor to another app on my Windows desktop.  I saw the xterm window disappear.  I then went back to it and created another xterm and did "ps -elf | grep xterm", and I saw the other xterm process there (several, now).

is this a fvwm problem, or a TightVNCViewer problem?

---

### Post by David_M._Karr on 2015-07-13
Note that when I select the "Restart fvwm" option from the context menu, I briefly see all the windows that I had created, but most of them go away after a fraction of a second.

---

### Post by TheFu on 2015-07-13
fvwm is a virtual window manager. There are probably 4 or 9 desktops. I suspect you did something to switch to a different desktop.  if you don't already know fvwm, it probably isn't worth trying to learn it. Use openbox instead or steeldriver's script. I like it better, but would rather set the full path to each program and would test those for execute, not just existence.

But .... 

x2go is much easier.  5 min is all it takes to get x2go working.
[http://wiki.x2go.org/doku.php/wiki:repositories:ubuntu](http://wiki.x2go.org/doku.php/wiki:repositories:ubuntu) has instructions.

---

### Post by David_M._Karr on 2015-07-15
Thanks, but it only took a little more effort to get fvwm working, by enabling a few more options (and disabling "EdgeScroll").  I imagine both x2go and openbox will be better than VNC and fvwm, but for now this is all I need.

---

