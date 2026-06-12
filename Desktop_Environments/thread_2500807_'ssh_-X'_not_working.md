---
title: "'ssh -X' not working"
date: 2024-09-12
forum: Desktop Environments
---

### Post by john163 on 2024-09-12
I can't actually get X sessions forwarded.  /etc/ssh/sshd_config does have 


X11Forwarding yes
X11DisplayOffset 10


ssh does seem to be working:


debug1: Remote: /home/joliver/.ssh/authorized_keys:1: key options: agent-forwarding port-forwarding pty user-rc x11-forwarding
debug1: Remote: /home/joliver/.ssh/authorized_keys:1: key options: agent-forwarding port-forwarding pty user-rc x11-forwarding
debug1: Requesting X11 forwarding with authentication spoofing.


but DISPLAY is still localhost:10.0


What do I need to do to get X forwarded?

---

### Post by ActionParsnip on 2024-09-12
[https://bbs.archlinux.org/viewtopic.php?id=202098](https://bbs.archlinux.org/viewtopic.php?id=202098)
May help

---

### Post by ActionParsnip on 2024-09-12
[https://forums.freebsd.org/threads/x11-forwarding-in-ssh-not-working-on-one-machine.88672/](https://forums.freebsd.org/threads/x11-forwarding-in-ssh-not-working-on-one-machine.88672/)

---

### Post by john163 on 2024-09-12
So this is weird... when I connect, firefox and another application that I care about are launched on the remote host, but xclock is launched on the local host!

---

### Post by john163 on 2024-09-12
debug1: Entering interactive session.
debug1: pledge: exec
debug1: client_input_global_request: rtype [email]hostkeys-00@openssh.com[/email] want_reply 0
debug1: client_input_hostkeys: searching /home/joliver/.ssh/known_hosts for 192.168.0.32 / (none)
debug1: client_input_hostkeys: searching /home/joliver/.ssh/known_hosts2 for 192.168.0.32 / (none)
debug1: client_input_hostkeys: hostkeys file /home/joliver/.ssh/known_hosts2 does not exist
debug1: client_input_hostkeys: host key found matching a different name/address, skipping UserKnownHostsFile update
debug1: Remote: /home/joliver/.ssh/authorized_keys:1: key options: agent-forwarding port-forwarding pty user-rc x11-forwarding
debug1: Remote: /home/joliver/.ssh/authorized_keys:1: key options: agent-forwarding port-forwarding pty user-rc x11-forwarding
debug2: channel_input_open_confirmation: channel 0: callback start
debug2: x11_get_proto: /usr/bin/xauth  list :0 2>/dev/null
debug1: Requesting X11 forwarding with authentication spoofing.
debug2: channel 0: request x11-req confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug1: Sending environment.
debug1: channel 0: setting env LANG = "en_US.UTF-8"
debug2: channel 0: request env confirm 0
debug2: channel 0: request shell confirm 1
debug2: channel_input_open_confirmation: channel 0: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_status_confirm: type 99 id 0
debug2: X11 forwarding request accepted on channel 0
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Welcome to Ubuntu 22.04.4 LTS (GNU/Linux 5.15.0-119-generic x86_64)

---

### Post by john163 on 2024-09-12
joliver@blinky:~$ firefox &
[1] 188881
joliver@blinky:~$ debug1: client_input_channel_open: ctype x11 rchan 3 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 46020
debug2: fd 7 setting O_NONBLOCK
debug1: channel 1: new [x11]
debug1: confirm x11
debug2: channel 1: rcvd eof
debug2: channel 1: output open -> drain
debug2: channel 1: obuf empty
debug2: chan_shutdown_write: channel 1: (i0 o1 sock 7 wfd 7 efd -1 [closed])
debug2: channel 1: output drain -> closed
debug1: channel 1: FORCE input drain
debug2: channel 1: ibuf empty
debug2: channel 1: send eof
debug2: channel 1: input drain -> closed
debug2: channel 1: send close
debug2: channel 1: rcvd close
debug2: channel 1: is dead
debug2: channel 1: garbage collecting
debug1: channel 1: free: x11, nchannels 2

---

### Post by john163 on 2024-09-12
That results in the firefox window opening locally on the remote host.

But...

joliver@blinky:~$ xclock &
[1] 188961
joliver@blinky:~$ debug1: client_input_channel_open: ctype x11 rchan 3 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 49278
debug2: fd 7 setting O_NONBLOCK
debug1: channel 1: new [x11]
debug1: confirm x11

results in xclock opening locally on the host I'm initiating the connection from.

---

### Post by ActionParsnip on 2024-09-12
Does the client system not have a Web browser installed? Why launch Firefox using X forwarding?

---

### Post by john163 on 2024-09-12
> **ActionParsnip said:**
> Does the client system not have a Web browser installed? Why launch Firefox using X forwarding?

Because I want to use Firefox on the remote machine on this local machine, so I don't have to switch between the two.

---

### Post by ActionParsnip on 2024-09-12
> **john163 said:**
> Because I want to use Firefox on the remote machine on this local machine, so I don't have to switch between the two.

Oh. I mean you could set up an SSH tunnel then set the proxy in the local browser to go through the tunnel then out to the network / Internet from there. Is that the desired goal here?

---

### Post by john163 on 2024-09-12
> **ActionParsnip said:**
> Oh. I mean you could set up an SSH tunnel then set the proxy in the local browser to go through the tunnel then out to the network / Internet from there. Is that the desired goal here?

These two laptops are on the same network.  They sit right next to each other.  I just want to be able to use apps on my personal laptop while sitting on my work laptop.  No need to overcomplicate things!

---

### Post by TheFu on 2024-09-12
I've been running lots of remote apps on other systems here using ssh -X for decades, including firefox, thunderbird, EasyTag, and probably 30 other GUI programs.
With firefox and thunderbird, I have to add the **-no-remote** option to ensure the remote binary is actually used.

I don't use Wayland on any of my systems, so I don't know if that matters.

This firefox window I'm typing into now is running on a Mint 21.3 system. I'm sitting behind a minimal Ubuntu 20.04 box.  Same for thunderbird.  I just got tired of fighting with Canonical about snap packages.  I have yet to find any desktop snap that works as well as the normal repo, debian package for my needs, so when that has been removed as an option - thanks Canonical, NOT! - time to work around it.  There are a few complexities with integrations between local and remote running programs, but not having a GUI, bloated, web browser on my local workstation is a good start to prevent all sorts of security risks.

Anyway, ensure both sides aren't using Wayland. That's my first suggestion, but I know absolutely nothing about what actually should be supported by Wayland or not.

---

### Post by cainesaj on 2024-09-16
> **john163 said:**
> So this is weird... when I connect, firefox and another application that I care about are launched on the remote host, but xclock is launched on the local host!

The good news is that you have X11 forwarding correctly over your ssh tunnel. X11 clients such as *xclock* and *xeyes* will appear on your local X11 server.

What won't work as easily or at all are clients which either aren't X11 clients or which depend on (what I will broadly categorise as) desktop integrations. You may be able to get them tunneled by divorcing them from their local display, using tools such as *dbus-launch*, or other tricks, but with the migration from X11 to Wayland, the deeper integration of applications into desktop environments, and applications moving to container-like environments such as Flatpak and snap, the network transparency feature of the X11 client-server model (which is effectively reproduced through the tunnel) will continue to decrease in usability; and the effort involved in testing, making, and keeping it working will become excessive [much like this sentence].

Options using VNC and RDP remain, but only as a replacement for [XDMCP]("https://wiki.ubuntu.com/xdmcp") rather than a network-transparent client-server model. These, too, are increasingly integrated into desktop environments.

```
$ ssh user@desktop 'xwd -display :0 -root -silent -out /tmp/x.xwd && xwud -in /tmp/x.xwd -noclick -display :0'
```

---

### Post by TheFu on 2024-09-16
```
$ ssh -X deneb firefox -no-remote &
```
working here.  Just started a new firefox instance with that exact command.
My usename is the same on both systems.
"deneb" is the LM 21.3 system.
Don't know what else to say.  Using this sort of remote application running is a way of life for me.  I have about 10 windows displayed on my workstation that are all running on other systems.  That includes my main firefox, thunderbird, and a number of terminal ssh sessions into non-desktop systems.

Be certain you are using the Xorg server on the local workstation, not Wayland.  That's my only guess for a possible problem and I have doubts that would actually be an issue at this point, but I don't know. I don't use Wayland.

---

