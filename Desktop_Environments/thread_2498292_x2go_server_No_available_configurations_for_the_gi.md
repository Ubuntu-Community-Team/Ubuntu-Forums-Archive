---
title: "x2go server: No available configurations for the given pixel format"
date: 2024-06-07
forum: Desktop Environments
---

### Post by linuxlion2 on 2024-06-07
On a Ubuntu Linux 22.04.4 is 'x2goserver' (4.1.0.6-0~202308180209~ubuntu22.04.1) installed.

A connection with the x2goclient is made with the parameters 'UNITY' and '1280x1024'.
The connection succeeds at first.
A new windows is opened on the client system.
But the new window disappears and the connection is broken.

On the x2go server, in the logfile /var/log/syslog, the error message is written:

Jun  7 15:27:46  gnome-session[2508986]: gnome-session-check-accelerated: Failed to get GTK GLES renderer: No available configurations for the given pixel format
Jun  7 15:27:46  gnome-session[2508769]: gnome-session-binary[2508769]: WARNING: software acceleration check failed: Child process exited with code 1
Jun  7 15:27:46  gnome-session-binary[2508769]: WARNING: software acceleration check failed: Child process exited with code 1

How can I generate, copy or download the right configuration for the given pixel format?

---

### Post by TheFu on 2024-06-09
Use XFCE, Mate, Openbox, or some other DE - not Gnome 3or newer and not any that demand direct GPU access.  That isn't how remote desktops work.

This assumes I understand the issue.  Looks like it is trying to use a Gnome 3/4 session which will never work.

---

### Post by linuxlion2 on 2024-06-10
With XFCE I get a remote desktop windows from the remote system.
But the response time is very long.
It behaves like a very slow system.
With sftp the speed between client and server system is +/- 33MB/s .
In the x2goclient the speed is set on "LAN".
The command 'top' shows that the process 'x2goagent' takes 95% of CPU.
How can increase the speed?

---

### Post by ActionParsnip on 2024-06-10
What are you wanting to do on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to do

---

### Post by TheFu on 2024-06-10
Always change the bandwidth setting to be 1-less than what you really have. 2-less if you use WIFI.  
Also, you can change the image compression to 4Kb-png with little impact. I run this way by default.
Disable local file sharing and printing too.

As for network speed, use iperf3 between the 2 systems to see what you really get, not other protocols with lots of overhead.  Sure, all protocols have overhead, but when troubleshooting, 
1. Simplify
2. Test
3. Repeat
are the steps. Keep simplifying until you isolate the issue or cannot go any "smaller"/"simpler".  That is usually 3-4 times smaller than that starting point.

---

### Post by linuxlion2 on 2024-06-10
The x2go server is located on my work office.
During my work, in the office, I start, in the desktop, several xterm sessions, a web-browser and other x application.
The next day I work from home, and I will connect to the desktop to continue my work in the same xterm sessions, web-browser etc.
With Windows I do the same with remote-desktop and that works satisfactorily.

---

### Post by linuxlion2 on 2024-06-10
The internal network speed in our office is 1Gbits/sec
The output of iperf3 shows that we almost reach that network speed.

$ iperf3 -p 4875 -c 192.168.0.65
Connecting to host 192.168.0.65, port 4875
[  5] local 192.168.7.101 port 52356 connected to 192.168.0.65 port 4875
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec   113 MBytes   945 Mbits/sec    0    407 KBytes       
[  5]   1.00-2.00   sec   112 MBytes   938 Mbits/sec    0    469 KBytes       
[  5]   2.00-3.00   sec   112 MBytes   937 Mbits/sec    0    492 KBytes       
[  5]   3.00-4.00   sec   111 MBytes   934 Mbits/sec    0    516 KBytes       
[  5]   4.00-5.00   sec   111 MBytes   932 Mbits/sec    0    516 KBytes       
[  5]   5.00-6.00   sec   111 MBytes   932 Mbits/sec    0    516 KBytes       
[  5]   6.00-7.00   sec   112 MBytes   938 Mbits/sec    0    539 KBytes       
[  5]   7.00-8.00   sec   111 MBytes   935 Mbits/sec    0    587 KBytes       
[  5]   8.00-9.00   sec   111 MBytes   932 Mbits/sec    0    612 KBytes       
[  5]   9.00-10.00  sec   112 MBytes   940 Mbits/sec    0    642 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  1.09 GBytes   936 Mbits/sec    0             sender
[  5]   0.00-10.00  sec  1.09 GBytes   934 Mbits/sec                  receiver

iperf Done.


The output of the command 'top' shows that the process 'x2goagent' use +/- 94 of a CPU.
It seems that that the process 'x2goagent' is 'looping'.

Tasks: 367 total,   2 running, 365 sleeping,   0 stopped,   0 zombie
%Cpu(s): 47,8 us,  1,5 sy,  0,0 ni, 50,0 id,  0,0 wa,  0,0 hi,  0,7 si,  0,0 st
MiB Mem :   1958,9 total,    242,5 free,    954,9 used,    761,5 buff/cache
MiB Swap:   6046,0 total,   5894,6 free,    151,4 used.    839,7 avail Mem 

    PID USER         PR  NI      VIRT     RES     SHR S  %CPU  %MEM      TIME+ COMMAND    
   2930 hans         20   0  167704  89876  18800 R    94,7       4,5  52:23.35 x2goagent  
   3469 hans         20   0  409196  42480  32300 S      2,3       2,1    2:33.22 xfwm4      
   4395 hans         20   0    17568    7868   5504 S      1,3       0,4    0:05.68 sshd       
    702 systemd+  20   0    14836    6272   6016 S      0,3       0,3    0:05.18 systemd-o+

---

### Post by linuxlion2 on 2024-06-10
In the log file /var/log/syslog, every 5 seconds the messages below are added:

Jun 10 15:57:41 john-mid-linux x2gocleansessions: executing external command ,,/usr/lib/x2go/x2golistsessions_sql'' with args: john-mid-linux
Jun 10 15:57:41 john-mid-linux x2golistsessions_sql: executing external command ,,x2gopath'' with args: libexec
Jun 10 15:57:41 john-mid-linux x2golistsessions_sql: executing external command ,,/usr/lib/x2go/libx2go-server-db-sqlite3-wrapper'' with args: listsessionsroot,john-mid-linux
Jun 10 15:57:41 john-mid-linux x2gocleansessions: executing external command ,,/usr/lib/x2go/x2gogetstatus'' with args: john-50-1718019116_stDXFCE_dp24
Jun 10 15:57:41 john-mid-linux x2gogetstatus: executing external command ,,x2gopath'' with args: libexec
Jun 10 15:57:41 john-mid-linux x2gogetstatus: executing external command ,,/usr/lib/x2go/libx2go-server-db-sqlite3-wrapper'' with args: getstatus,john-50-1718019116_stDXFCE_dp24
Jun 10 15:57:42 john-mid-linux x2gogetstatus: db_getstatus called, session ID: john-50-1718019116_stDXFCE_dp24, return value: R

---

### Post by TheFu on 2024-06-10
I don't see **any** messages related to x2go in syslog on the client side.
On the server, I'm seeing:

```
$ grep x2go /var/log/syslog
Jun 10 13:25:29 deneb /usr/bin/x2gostartagent: successfully started X2Go Agent session with ID tf-50-1718040328_stDfvwm_dp24
Jun 10 13:25:30 deneb /usr/bin/x2goruncommand: launching session with Xsession-x2go mechanism, using STARTUP="/usr/bin/fvwm"
Jun 10 13:25:30 deneb /usr/bin/x2goruncommand: dbus wrapper available as /usr/bin/dbus-run-session

```

Inside the little debug window inside the x2go-client window, this is shown:
```
NXPROXY - Version 3.5.99.26

Copyright (c) 2001, 2011 NoMachine (http://www.nomachine.com)
Copyright (c) 2008-2014 Oleksandr Shneyder <o.shneyder@phoca-gmbh.de>
Copyright (c) 2014-2016 Ulrich Sibiller <uli42@gmx.de>
Copyright (c) 2014-2016 Mihai Moldovan <ionic@ionic.de>
Copyright (c) 2011-2016 Mike Gabriel <mike.gabriel@das-netzwerkteam.de>
Copyright (c) 2015-2016 Qindel Group (http://www.qindel.com)

NXCOMP, NX protocol compression and NX extensions to this software
are copyright of the aforementioned persons and companies.

Redistribution and use of the present software is allowed according
to terms specified in the file LICENSE.nxcomp which comes in the
source distribution.

All rights reserved.

NOTE: This software has received contributions from various other
contributors, only the core maintainers and supporters are listed as
copyright holders. Please contact us, if you feel you should be listed
as copyright holder, as well.

NX protocol compression is derived from DXPC project.

Copyright (c) 1995,1996 Brian Pane
Copyright (c) 1996,1997 Zachary Vonler and Brian Pane
Copyright (c) 1999 Kevin Vigor and Brian Pane
Copyright (c) 2000,2003 Gian Filippo Pinzari and Brian Pane

All rights reserved.

See https://github.com/ArcticaProject/nx-libs for more information.

Info: Proxy running in server mode with pid '3332871'.
Session: Starting session at 'Mon Jun 10 13:25:29 2024'.
Info: Using errors file '/home/tf/.x2go/S-tf-50-1718040328_stDfvwm_dp24/sessions'.
Info: Using stats file '/home/tf/.x2go/S-50/stats'.
Loop: WARNING! Overriding auxiliary X11 port with new value '1'.
Warning: Overriding auxiliary X11 port with new value '1'.
Info: Using abstract X11 socket in kernel namespace for accessing DISPLAY=:0.
Info: Connecting to remote host 'localhost:56434'.
Info: Connected to remote proxy on FD#5.
Info: Connection with remote proxy completed.
Loop: WARNING! Unrecognized session type 'unix-kde-depth_24'. Assuming agent session.
Warning: Unrecognized session type 'unix-kde-depth_24'. Assuming agent session.
Info: Using WAN link parameters 1408/24/1/0.
Info: Using cache parameters 4/4096KB/8192KB/8192KB.
Info: Using pack method '4k-png-9' with session 'unix-kde-depth_24'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 1/1.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':0.0'.
Info: Forwarding auxiliary X11 connections to display ':0.0'.
Session: Session started at 'Mon Jun 10 13:25:29 2024'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.

```
I tell it to run fvwm and provide the exact path.  Both the client system and the server use Xorg/X11 for the display server.  I have no Wayland anywhere and don't use any DE, though I have used XFCE, Mate, LXDE, and LXQt before just fine.

When posting terminal/log output, please use code tags so things line up. Really would be helpful if you edited all prior posts to wrap in code tags those parts to reduce important things from being missed.

top shows this on the client system:
```

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                         
 259627 tf        20   0   80532  28400   8356 S   0.7   0.5   0:00.59 x2goagent                       
   1696 root      20   0   28328  17660   2932 S   0.3   0.3   0:45.02 x2gocleansessio                 

```
Hardly any CPU or RAM needed with x2go.

The TOP output on your system shows it only has 2GB of RAM.  That isn't much for a computer today.  No way should you attempt to run Gnome or KDE DEs ... er ... ever on a system like that.

I assume the network performance results are at work, not over the internet.  The settings need to be for the slowest connection used.  Try the "DSL" setting and please confirm you made the other 3 changes already suggested.

---

### Post by linuxlion2 on 2024-06-12
Thanks for your help.
In a couple of weeks, I will continue with this problem.

---

