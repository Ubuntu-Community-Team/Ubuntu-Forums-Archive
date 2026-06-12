---
title: "SSH is not working"
date: 2009-03-04
forum: General Help
---

### Post by madman19 on 2009-03-04
I just got my new Dell Mini 9 and I attempted to ssh (from the terminal) into a school server for a project I have to do. Once it asked for my password, I put it in and hit enter and then it sits there. Any ideas on how to fix this?

---

### Post by brian_p on 2009-03-05
> **madman19 said:**
> 

Any ideas on how to fix this?

Using ssh with the -v option (man ssh) may give you a clue as to the problem.

---

### Post by autra on 2009-03-19
I have the same problem and was unable to fix it.
I typed ssh with the -vvv option.
I was asked for my password, and then i had the wollowing output:

> Password: 
debug3: packet_send2: adding 32 (len 23 padlen 9 extra_pad 64)
debug2: input_userauth_info_req
debug2: input_userauth_info_req: num_prompts 0
debug3: packet_send2: adding 48 (len 10 padlen 6 extra_pad 64)
debug1: Authentication succeeded (keyboard-interactive).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting [email]no-more-sessions@openssh.com[/email]
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug3: tty_make_modes: ospeed 38400
debug3: tty_make_modes: ispeed 38400
debug1: Sending environment.
debug3: Ignored env ORBIT_SOCKETDIR
debug3: Ignored env GPG_AGENT_INFO
debug3: Ignored env SHELL
debug3: Ignored env TERM
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env GTK_RC_FILES
debug3: Ignored env WINDOWID
debug3: Ignored env GTK_MODULES
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env LIBGL_DRIVERS_PATH
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env GNOME_KEYRING_SOCKET
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env USERNAME
debug3: Ignored env PATH
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env GDM_XSERVER_LOCATION
debug3: Ignored env PWD
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env GNOME_KEYRING_PID
debug3: Ignored env GDM_LANG
debug3: Ignored env GDMSESSION
debug3: Ignored env HISTCONTROL
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env WINDOWPATH
debug3: Ignored env DISPLAY
debug3: Ignored env LESSCLOSE
debug3: Ignored env COLORTERM
debug3: Ignored env XAUTHORITY
debug3: Ignored env _
debug2: channel 0: request shell confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768


And then it froze...

Any idea to solve this ? Thank you !

---

### Post by fieroboom on 2009-03-19
Let's see if my psychic powers are in operation today... ;)
Are you attempting to SSH from your wireless network, or is the school's computer on a wireless network?
Some routers (especially the wireless side) choke on the values SSH sets for the [IP TOS (Type Of Service)](http://en.wikipedia.org/wiki/Type_of_Service). There are a few ways around this... If you are connecting from your own wireless network, then try plugging in with a network cable if you can. If you already plugged in, or if you're unable to plug in, then it gets kinda ugly.

If the entire above paragraph doesn't apply to you, then the next best thing to try is a reverse SSH tunnel the next time you have physical (or internal) access to the school's machine you're currently attempting to connect to. A reverse SSH tunnel is super easy, and it makes short work of getting back into the network. Here's how you do it...

**Before you leave home:**
- On your own router, make sure you have port 22 forwarded to your computer's IP address in your router (if you're behind one).
- On your home computer, edit the /etc/ssh/sshd_config config file and add these two lines:
```
TCPKeepAlive yes
ClientAliveInterval 190
```(That will keep the reverse tunnel from dying before you get home)
- Navigate to [http://whatismyip.com/](http://whatismyip.com/)  and write down your IP address

**On the machine at school**:
-Run this command to initiate the reverse tunnel:
```
ssh -nNTR 2200:localhost:22 your.home.ip.address
```

The -nNT options mean:
     - Redirect STDIN from /dev/null  (ie, don't read from STDIN)
     - Do not execute a remote command (ie, just open the connection)
     - Disable pseudo-tty allocation.  (ie, don't open a terminal)

The 2200 can be any port you like, but needs to be one that your home computer isn't already listening on. The 22 needs to remain the same, because that's the default SSH port, and the IP address tells the school computer where to initiate the reverse tunnel to.

Now, when you get back home, the way to connect to the school machine is:
```
ssh -p 2200 localhost
```
In other words, you're connecting on port 2200 to your own computer, which is in turn forwarding that request back down the already-open reverse tunnel to the machine at school. SSH r teh awsum!
:D
-Paul

EDIT:
If you want to read more on why it's freezing, have a look [here](http://discussions.apple.com/message.jspa?messageID=7073359) and [here.](http://www.securityfocus.com/archive/121/474437/30/300/threaded)

---

