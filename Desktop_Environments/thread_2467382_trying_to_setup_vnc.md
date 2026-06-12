---
title: "trying to setup vnc"
date: 2021-09-25
forum: Desktop Environments
---

### Post by Sandgoose on 2021-09-25
didn't know to post this in networking or desktop but figure the main issue is the desktop.

I apt-get install tightvncserver, I run vncserver set the passwords etc I can vnc into the machine but all I get is a grey screen and nothing else.

having a poke at the logs it says fonts were missing but ignores then it saying xrdb no such file or directory.

when I type xrdb it tells me command not found but it is in some x11 package, so I apt get install the pacakge and it tells me this package is already upto date.

I have googled and tried several different xstartup config files all of them end with the same result, I vnc into the machine and get an X cursor with a gray background and nothing more.

any suggestions ?

---

### Post by ActionParsnip on 2021-09-25
You can use this
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04)

But a better thing to ask is why do you want to use VNC? What are you doing on the remote system that needs the full desktop session? Why setup VNC at all?

---

### Post by TheFu on 2021-09-25
The gray screen is just the root window.  Did you start a window manager or DE?
If you have openbox or fvwm installed, run those. They are light and work well over vnc.

openbox & at the bottom of your vnc-startup script on the vnc server should do it.
then right-click anywhere on the desktop to see a menu and run programs.

Gnome3+ doesn't work to my knowledge.
Most other DEs should work, but you'll need to figure out which command to run.

Or


just use **x2go** which has better performance, easier setup, and 1000x better security than rdp or vnc solutions.  x2go is based on NX which embeds ssh for tunneled, secured, connections between the client and server.  x2go clients exist for linux, Windows, and OSX.  I know the Windows and Linux clients are very stable and work well, once ssh is setup.  A normal, standard, ssh connection needs to be working between the client and server for x2go to work.  ssh-keys work too and are automatically used when the client is linux, just like all other ssh-based tools (scp, sftp, sshfs, rsync, x2go, and most backup tools.)

---

### Post by Sandgoose on 2021-09-25
I have a mostly stock xubuntu 21.04 so its running xfce4

adding "startxfce4 &" to the bottom of the vnc startup script did nothing even if I typed the full path.

I saw someone else suggest x2go while searching for fixes, does it have the same range of support vnc has (can run on anything under the sun (arm + android support would be great) and being in the repositories would be great too)

@Actionparsnip

the is the exact guide I was using, the second line on their config file..

"
#!/bin/bash
xrdb $HOME/.Xresources
startxfce4 &
"

xrdb seems to be no longer included as part of the package it was originally in OR somehow my version does not have it ??

"why do you want to use VNC? What are you doing on the remote system that needs the full desktop session? Why setup VNC at all?"
I don't specifically need VNC, It's just what I know ? all I need is to be able to remotely control a mini tiny form factor pc on a shelf that I don't have the room to hook a monitor upto or run multiple cables into

---

### Post by TheFu on 2021-09-25
Well, x2go is 2-3x faster than vnc AND much more secure, does that help?
I've been using the PPA for years. Windows clients need the "fonts" package from the x2go site too and when setting up ssh, use the ssh tools included in x2go, not from non-standard solutions like putty.

With VNC, you probably need to manually set the DISPLAY correctly.  IDK - haven't used VNC in a very, very, long time after finding x2go.

---

### Post by Sandgoose on 2021-09-25
really is news to me! always thought vnc was the goto for remote desktop on linux! but thanks for the suggest! In process of giving x2go a shot.

---

### Post by ActionParsnip on 2021-09-25
> **Sandgoose said:**
> I have a mostly stock xubuntu 21.04 so its running xfce4

adding "startxfce4 &" to the bottom of the vnc startup script did nothing even if I typed the full path.

I saw someone else suggest x2go while searching for fixes, does it have the same range of support vnc has (can run on anything under the sun (arm + android support would be great) and being in the repositories would be great too)

@Actionparsnip

the is the exact guide I was using, the second line on their config file..

"
#!/bin/bash
xrdb $HOME/.Xresources
startxfce4 &
"

xrdb seems to be no longer included as part of the package it was originally in OR somehow my version does not have it ??

"why do you want to use VNC? What are you doing on the remote system that needs the full desktop session? Why setup VNC at all?"
I don't specifically need VNC, It's just what I know ? all I need is to be able to remotely control a mini tiny form factor pc on a shelf that I don't have the room to hook a monitor upto or run multiple cables into

Yes but what will you do once connected to the VNC session? What do you want to "remotely control" that needs VNC? What activities will you be doing on the remote system? There may be a sleeker solution to what you want to achieve

---

### Post by TheFu on 2021-09-25
> **Sandgoose said:**
> really is news to me! always thought vnc was the goto for remote desktop on linux! but thanks for the suggest! In process of giving x2go a shot.

There's lots of old junk out there with less-than-great recommendations.
On the LAN, I'd use straight X11 forwarding that is built-into X11 w/ ssh, not any massive "remote connection desktop" junk.
It is only over the internet when x2go is needed because it is so efficient compared to all free options.  If the client is Windows, then X11-forwarding is a little harder, but I understand that with a Linux GUI running under Windows, it can be done.  In the old days, we'd run a VM with a light Linux and an X/Server to achieve the same result over a $150 commercial X/Server that ran on Windows.

Remote X11 is:
```
$ ssh -X remote-user@remote-IP "command to be run with options"
```
Easy stuff.  I run libreoffice, thunderbird, firefox, and a number of other things that way.  If the local and remote usernames are the same, that isn't needed.  If you have DNS or /etc/hosts for the remote system lookups, then user the machine name.  The command becomes 
```
$ ssh -X regulus "firejail thunderbird"
```
That will connect to regulus, run thunderbird inside a firejail sandbox and display the window for it on the machine I'm sitting on.  Not a full desktop, just another windows that seems like every other window - full copy/paste with the rest of the system.  A terminal can be used too .... 
```
$ ssh -X regulus "xterm -sb "
```
Simple. Easy. Select/paste integration.  Right now, I have 8 terminals open. 6 on other systems, only 2 are local, for example.

---

### Post by Sandgoose on 2021-09-25
"What activities will you be doing on the remote system?"

off the top of my head, file management, very light web browsing (though not essential) and transmission

the idea is for downloading linux iso distributions and helping seed because I don't want to leave the main noisy powerhungry pc on overnight, it would be useful to have a machine that I can just login to start a task and forget about whiling letting it do its thing.

I do get that I could probably achieve a similar thing using ssh, samba and transmission but feel i would rather have the full graphical experience, partly because I am trying to setup this machine by switching monitors and its becoming tedious to switch back and forth trying to get it to work.

"If the client is Windows, then X11-forwarding is a little harder,"
the client is windows but I thought possibly may use android at some point too

---

### Post by TheFu on 2021-09-25
File manager ... that would be caja on a Mate system
```
ssh -X regulus caja
``` would be the command.
After you setup ssh-keys ... which is 2 commands first time, then just 1 command to push the public key from that client to any number of servers, all this ssh stuff becomes extremely convenient and you don't think anything about running programs on other systems.

Some ubuntu systems use pcman-fm, thunar, and nautilus.  All of them should be able to use sftp ... which honors ssh credentials (those key pairs you setup), so really you could to file management from your local Linux workstation to the one in the basement that way.  Just use sftp://regulus/ in the URL.

Or you can setup NFS between the systems. NFS makes remote storage (on the LAN) look and feel like local storage. It uses real mounts and all user permissions are suppored just like on local storage.
and per
```
$ df -Th
Filesystem                        Type  Size  Used Avail Use% Mounted on
istar:/d/D1                       nfs4  3.5T  3.5T   34G 100% /d/D1

```
I can use any programs (that aren't snaps) to access, manage, delete, whatever my permissions allow on /d/D1.  cd /d/D1 ... caja works and thinks it is local storage.  So do all normal packages.  It is just snap programs that have issues - flatpaks and AppImages and .deb packaged stuff have NO issues with NFS.  Canonical has been aware of the NFS bug for about 4 yrs.

---

### Post by ActionParsnip on 2021-09-26
If you want file management you can do this using SFTP that you get when you install openssh-server. You can also Web browse using the system if you setup an SSH tunnel or you can even install squid and set the pi as your web proxy in the system you are using's browser. You don't need VNC.

---

### Post by ActionParsnip on 2021-09-26
[https://www.digitalocean.com/community/tutorials/how-to-route-web-traffic-securely-without-a-vpn-using-a-socks-tunnel](https://www.digitalocean.com/community/tutorials/how-to-route-web-traffic-securely-without-a-vpn-using-a-socks-tunnel)

---

### Post by TheFu on 2021-09-26
> **ActionParsnip said:**
> [https://www.digitalocean.com/community/tutorials/how-to-route-web-traffic-securely-without-a-vpn-using-a-socks-tunnel](https://www.digitalocean.com/community/tutorials/how-to-route-web-traffic-securely-without-a-vpn-using-a-socks-tunnel)

+1.  I use a SOCKS5 tunnel (via ssh) all the time when traveling to have my web traffic appear to originate from my HOME network. I've posted a script here just for that a few times.  I'd post it again (Linux workstation/laptop to any ssh-server), but my laptop isn't powered on and I can't ssh into it right now. ;)  

Hummmm ... but I have backups online somewhere.

```
#!/bin/bash

PORT=64001   # ssh port, best not to use 22/tcp from the internet
SSH_SRV=my-ssh-server.example.com   # could be an IP

# Only start SOCKS proxy if necessary
if  [ $(/bin/ps -eaf |/bin/grep ssh |/bin/grep -c $PORT ) = 0 ] ; then
   # Setup SOCKS proxy through home server
   echo "Starting ssh SOCKS Proxy"
   /usr/bin/ssh  -f -C -D $PORT  $SSH_SRV  -NT &
fi 

# Star private firejail with chromium, going through 
# just setup SOCKS proxy
sleep 3;
echo "Starting Firejail chromium with private & proxy "
export http_proxy="socks5://localhost:$PORT "; 
/usr/bin/firejail  --private chromium-browser \
         --proxy-server="socks5://localhost:$PORT " &

exit;
```

I use firejail in a private mode.  Chromium allows specifying the proxy-server on the command line. Firefox does not, so I use chromium for this purpose.  Chromium runs on my local machine and all HTTP/HTTPS traffic is sent to $SSH_SRV before going to the final address. That address can be local, on the same LAN or on the internet.

It is also possible to use X11 to run chromium on the remote system and have the window displayed on my workstation.
Easy ... 
```
$ ssh -X regulus /usr/bin/firejail  --private chromium-browser
panic: permission denied

goroutine 1 [running]:
github.com/snapcore/snapd/snapdtool.ExecInSnapdOrCoreSnap()
   /build/snapd-xa84xt/snapd-2.51.1+20.04ubuntu2/_build/src/github.com/snapcore/snapd/snapdtool/tool_linux.go:205 +0x59e
main.main()
   /build/snapd-xa84xt/snapd-2.51.1+20.04ubuntu2/_build/src/github.com/snapcore/snapd/cmd/snap/main.go:452 +0x39

```
 ... unless there is a snap package involved.  snaps just want to get in the way.  I think it is that chromium has their own sandbox which conflicts with firejail. Let's try that again, without firejail:
```
$ ssh -X regulus chromium-browser
```
Yep. That worked, through running a full browser on a raspberry-pi won't set any speed records.  Also, X11 forwarding doesn't do audio, but video is fast on most LANs.

---

