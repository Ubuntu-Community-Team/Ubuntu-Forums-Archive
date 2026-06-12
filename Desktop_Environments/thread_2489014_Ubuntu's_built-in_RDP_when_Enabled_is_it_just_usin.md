---
title: "Ubuntu's built-in RDP when Enabled is it just using XRDP?"
date: 2023-07-15
forum: Desktop Environments
---

### Post by bmullan2 on 2023-07-15
I just learned Ubuntu has "built-in" RDP support !

        *Instructions to Enable Remote Desktop on Ubuntu* _assumes_ you are already on an Ubuntu Desktop because the instructions tell you
        to Click on Settings, Remote Desktop to Enable Remote Desktop.

        When "enabled" is Ubuntu just using XRDP or some other RDP Server built-in to Ubuntu?

            Also, [I]is there an Ubuntu CLI command that **enables** Remote Desktop
        [/I]

        thanks

---

### Post by deadflowr on 2023-07-15
It uses freerdp. Depending on which version of Ubuntu probably freerdp2.
I'm not sure what the differences are between xrdp and freerdp, and I don't really care.

There are dconf/gsettings commands to enable and disable it.

However, as far as I know, it's a desktop sharing system, so it's designed to share an existing desktop session,
and not designed to set up a headless desktop, or something like that.
(Meaning when you connect to it it's an already running desktop session,
as oppose to a remote desktop that you log into and create as new desktop session when you make a connection.)
or something like that.

---

### Post by deadflowr on 2023-07-15
It's both. 
Provides a client and a server.
I have this on a default ubuntu desktop install
```
apt policy libfreerdp-server2-2:
  Installed: 2.6.1+dfsg1-3ubuntu2.3
  Candidate: 2.6.1+dfsg1-3ubuntu2.3
  Version table:
 *** 2.6.1+dfsg1-3ubuntu2.3 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.6.1+dfsg1-3ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
```
More

```
Package: libfreerdp-server2-2
Architecture: amd64
Version: 2.6.1+dfsg1-3ubuntu1
Multi-Arch: same
Priority: optional
Section: libs
**Source: freerdp2**
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 361
Depends: libc6 (>= 2.14), libfreerdp2-2 (= 2.6.1+dfsg1-3ubuntu1), libwinpr2-2 (>= 2.1.0+dfsg1)
Breaks: libfreerdp-server2 (<< 2.0.0~git20170725.1.1648deb+dfsg1-1~)
Replaces: libfreerdp-server2 (<< 2.0.0~git20170725.1.1648deb+dfsg1-1~)
Filename: pool/main/f/freerdp2/libfreerdp-server2-2_2.6.1+dfsg1-3ubuntu1_amd64.deb
Size: 99868
MD5sum: 2609b317b2637f799d820624d8ebcbff
SHA1: 0e0e8f3d04cdd761bcab5d686f13f73a61eca6e5
SHA256: 9bc13eb6653ca69ae804a6c11cb9e02398da1a1a0eb1d57d6beb1cda805c6249
SHA512: 9158ddde8ce1d55aae475fc43661044dd0fd616f9b8017cb0eb0e2dac554f1aaa8a06cf9843cfda28cf7f46a17321dd7f8f1e66a1256d641c04f43ac7b7273e7
Homepage: https://www.freerdp.com/
[B]Description-en: Free Remote Desktop Protocol library (server library)
 FreeRDP is a libre client/server implementation of the Remote
 Desktop Protocol (RDP).
 .[/B]
 This package contains the shared library with common server functionality.
Description-md5: 8eae4cc5c48d3ea95d5754b2bf1c90ea
Task: ubuntu-desktop-minimal, ubuntu-desktop, ubuntu-budgie-desktop, ubuntu-budgie-desktop-raspi
```

I have no xrpd installed. so, there.

Edit: Sorry, to add I don't know what other flavors have as the rdp package they use.
I never installed it or any other remote desktop software, so it comes with Ubuntu.
I guess it's part of the gnome-remote-desktop package Ubuntu desktop uses.

---

### Post by bmullan2 on 2023-07-15
Jeez thanks I didn't know freedesktop had added freerdp-server capability.

So I just created an Ubuntu 22.04 LXD Container, install ubuntu-desktop in it, Normally in the past I would install xrdp also and then use xfreerdp from the LXD Host to get the LXD Container's "remote desktop"

But on the host if I do a quick test:

$ xfreerdp /v:IP-of-Desktop-Container

No Ubuntu Remote Desktop comes up?

If I install xrdp in that same Desktop Container then from the Host

$ xfreerdp /v:IP-of-Desktop-Container
[I][B]
does work[/B][/I] and presents the LXD Container's Desktop.

Why do you think XRDP works but FreeRDP ***does not*** as an ***RDP server***?

---

### Post by ActionParsnip on 2023-07-18
What are you wanting to do on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to achieve

---

### Post by bmullan2 on 2023-07-18
@ActionParsnip..

Thanks! I've been working with linux & remote desktops for many years.

From just using: ssh -X, to VNC to NX to x2go, xrdp, guacamole & xrdp, freerdp2-x11 & xrdp.

There are a variety of other's I've experimented with in the past too though. Some lacked
features or capabilities, some were difficult to configure/update, some just buggy.

Out of the above I thought x2go, xrdp/freerdp2 (on server, on client) and guacamole/xrdp all worked great.

I use "remote desktops" quite often in LXD containers & LXD VMs *on both local & remote* Ubuntu instances (Digital Ocean & Hetzner clouds).
The cloud instances are usually temporary for use in a test/project.

There are lots of *perhaps* "*sleeker*" solutions (xpra et al) but ease of configuration & use, being open source, supported, secure and reliable,
are all key-value drivers.

So are capabilities such as *remote printing* to local printer, *remote audio/video* played locally and *remote/local* file-sharing.

There are a lot of use-cases for this that I've been involved with.

Let me know what "sleeker solutions" you have come across?
There's always something new appearing

---

### Post by ActionParsnip on 2023-07-18
You didn't say what activities you want to do on the system...you just reeled off a lot of alternative remote desktop technologies which I didn't ask for.

Why are you connecting to the system? What do you want to do once connected? Why connect to the system in the first place, by any protocol?

---

