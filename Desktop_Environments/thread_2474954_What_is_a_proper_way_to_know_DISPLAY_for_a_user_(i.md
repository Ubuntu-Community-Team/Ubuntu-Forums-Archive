---
title: "What is a proper way to know DISPLAY for a user (if I'm in non GUI session)?"
date: 2022-05-12
forum: Desktop Environments
---

### Post by and-account on 2022-05-12
Hi!

When a script is running from cron or process launched on behalf of root,
what is a good way to know current DISPLAY values? (***There is no exported DISPLAY variable under certain conditions. When script is running from Cron, over SSH or process launched on behalf of root.***)

Or how do I show an interface of a GUI app for a regular logged-in GUI user, from a script to be launched as root or over SSH?

Need to do from a script:
```
root@host: ~ # DISPLAY=:0 sudo -u user -i zenity --info --text=ABCDEFG

```

Well known methods do not work any more in Jammy 22.04. Earlier asked question ([https://ubuntuforums.org/showthread.php?t=2473703](https://ubuntuforums.org/showthread.php?t=2473703) ) was not resolved.

**Background information:**

There is no exported DISPLAY variable when script is running from cron, over SSH or process launched on behalf of root.

In past utility '[FONT=courier new]who[/FONT]' had value of DISPLAY variable in last column. It was easy extract it from the column. Now days - it's not. In Jammy utilities '[FONT=courier new]loginctl[/FONT]' and '[FONT=courier new]w[/FONT]' today do not have the value too. Proof and example is here:
```

$ loginctl list-sessions
SESSION  UID USER SEAT  TTY  
     15 1000 user seat0 tty2

$ loginctl show-session -p Display
Display=

```

How may I launch a GUI app for a user at seat0 without a hardcoded values?

---

### Post by #&amp;thj^% on 2022-05-12
Without knowing what your really after.
When you become user2 you may need to set the environment variable $DISPLAY.
```

$ export DISPLAY=:0.0
```
Example:
```
( DISPLAY=:0 yourapp & )
```
Maybe this link will help: [https://unix.stackexchange.com/questions/108784/running-gui-application-as-another-non-root-user](https://unix.stackexchange.com/questions/108784/running-gui-application-as-another-non-root-user)

If you want the "X" connection forwarded over "SSH", you need to enable it on both the server side and the client side. (Depending on the distribution, it may be enabled or disabled by default.) On the server side, make sure that you have "X11Forwarding yes" in "/etc/sshd_config" (or /etc/ssh/sshd_config or wherever the configuration file is). On the client side, pass the -X option to the ssh command, or put ForwardX11 in your ~/.ssh/config.

---

### Post by and-account on 2022-05-13
This is the question. Where may I found value ":0" of DISPLAY variable for current GUI session(s)? If in advance I do not know that it is ":0" (it can jump to :1, for example, under certain conditions).

How is DISPLAY value created, by what a software at what a launch step?

What is a best way to evaluate the value for current GUI env. if there is no DISPLAY variable in current process environment???

---

### Post by #&amp;thj^% on 2022-05-13
> **and-account said:**
> This is the question. Where may I found value ":0" of DISPLAY variable for current GUI session(s)?
```
[echo $DISPLAY
:0.0

```
> **and-account said:**
> 
How is DISPLAY value created, by what a software at what a launch step?


The magic word in the X window system is DISPLAY. A display consists (simplified) of:
[list]

    [*]a keyboard,
    [*]a mouse
    [*]and a screen.
[/list]

A display is managed by a server program, known as an X server. The server serves displaying capabilities to other programs that connect to it.

The value of the display environment variable is:

hostname:D.S
where:

hostname is the name of the computer where the X server runs. An omitted hostname means the localhost.

Example of values
```

localhost:4
google.com:0
:0.00
```
If you are not using a graphical environment (i.e. you are logging in on the system console with no windows etc; or you are logging in remotely from a text-only terminal over SSH or similar, such as from a Windows computer running PuTTY) then no GUI is involved, and DISPLAY will typically be unset. Your only means of communicating with the computer is the command line (though there may be ways to pivot into a GUI session if you know how).

If you are logging in on the console with a graphical interface (on Ubuntu, typically the GDM greeter is used) or using a graphical terminal (such as from a Windows computer running eXceed or mobaX, or remote desktop software like a VNC client)** the DISPLAY variable is set up by the program which manages your graphical session to indicate to graphical clients which I/O**
 devices to connect to.

the [B][U]DISPLAY variable is determined by the Display Manager, i.e. GDM3, LightDM, etc. I also made the discovery that the :0 or :1 is determined by AutomaticLogin. In GDM or Lightdm etc.
[/U][/B]

Warning: localhost is a special name that binds to a loopback interface (lo0) on Linux it should never be bound to a real IP address. You can actually check the binding by running sudo netstat -apn | grep 6010 your SSH should be listening on that port for the display connection. As far as I can tell it's 127.0.0.1 only. 

```
sudo netstat -apn | grep 0.0.0.0
tcp        0      0 127.0.0.1:<Snip>        0.0.0.0:*               LISTEN      1155/expressvpn-age 
udp        0      0 0.0.0.0:,<Snip>.          0.0.0.0:*                           -                   
udp        0      0 0.0.0.0:<Snip>         0.0.0.0:*                           535/avahi-daemon: r 
udp        0      0 0.0.0.0:<Snip>         0.0.0.0:*                           535/avahi-daemon: r 

```
A good place to start: [https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)
Another source: [https://linuxize.com/post/how-to-set-and-list-environment-variables-in-linux/](https://linuxize.com/post/how-to-set-and-list-environment-variables-in-linux/)

Also X man page:
```


    From the user's perspective, every X server has a display name of the form:

    hostname:displaynumber.screennumber

    This information is used by the application to determine how it should connect to the server and which screen it should use by default
 (on displays with multiple monitors):

    hostname The hostname specifies the name of the machine to which the display is physically connected. If the hostname is not given, the most efficient way
 of communicating to a server on the same machine will be used. displaynumber The phrase "display" is usually used to refer to a collection of monitors that 
share a common keyboard and pointer (mouse, tablet, etc.). Most workstations tend to only have one keyboard, and therefore, only one display. Larger, multi-user systems, 
however, frequently have several displays so that more than one person can be doing graphics work at once. To avoid confusion, each display on a machine
 is assigned a display number (beginning at 0) when the X server for that display is started. The display number must always be given in a display name. screennumber 
Some displays share a single keyboard and pointer among two or more monitors. Since each monitor has its own set of windows, each screen is assigned a screen number
 (beginning at 0) when the X server for that display is started. If the screen number is not given, screen 0 will be used.

```
There is not a straight forward answer to your question, just information for you* to digest.

---

### Post by Holger_Gehrke on 2022-05-13
If you're running X, you might want to take a look at the command line with which Xorg was started:
```

ps h -C Xorg -o 'args'

```
The $DISPLAY for a specific X-Server is one of the parameters. If you're running Wayland, I can't help ... (running XUbuntu myself, which uses XFCE which can't run with Wayland yet, AFAIK).

Holger

---

