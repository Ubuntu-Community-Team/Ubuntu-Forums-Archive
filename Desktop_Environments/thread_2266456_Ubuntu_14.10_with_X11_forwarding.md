---
title: "Ubuntu 14.10 with X11 forwarding"
date: 2015-02-23
forum: Desktop Environments
---

### Post by akela68 on 2015-02-23
Hi,

i use a small installation without graphical interface on the remote-machine. The windows open on the X-Server on my local Windows-desktop.
Now i update to 14.10 and the X11-forwarding doesn't work. Ubuntu use now the mir-Server (bad idea for server).
How can i configure my remote machine to use the X11-forward-mechanism?

Bye Andreas

---

### Post by grahammechanical on 2015-02-23
> [COLOR=#000000] Ubuntu use now the mir-Server (bad idea for server).[/COLOR]

I do not understand. The Mir display server that is intended to replace the Xserver is not default even in Vivid Vervet (the development branch of Ubuntu 15.04). It has been said that Mir will not be default even on 16.04 but as a user login option.

I am running 15.04 (Vivid Vervet) and it is still using the Xserver. I do not see how things could be different for Ubuntu Server. Both server and desktop editions of Ubuntu are developed in parallel and on the same code base.

To get Mir on an install of Vivid Vervet I have to install unity8-desktop-session-mir. And then I have to select the Unity 8 session at login. The Xserver is still being used up to the login screen.

I have also installed Unity Desktop Next which is where Ubuntu convergence experiments are done. It still uses the Xserver to get to a login screen. It is only after logging in that the switch is made to the Mir display server.

This I why I do not understand why you say that the Ubuntu 14.10 server edition is running on the Mir display server.

---

### Post by tgalati4 on 2015-02-23
Here's a similar thread, but no answer.  [http://ubuntuforums.org/showthread.php?t=2256737](http://ubuntuforums.org/showthread.php?t=2256737)

It's possible there is an X-Windows authentication error that shows up in a process called *gdk_mir_display_open*, even though MIR is not installed.  It could simply be a hook that was added to support MIR in the future, even though MIR is not normally installed by default in 14.10 or the server version for that matter.

Upgrading a working server should be weighed against the pain of fixing regressions.

---

### Post by akela68 on 2015-02-24
Hi,

i installed the system as 14.04 and made a dist-upgrade. In  result of this i cannot forwarding a x11-session. When i will run a  graphical application it is results in the following error:

```
gdk_mir_display_open
Failed to connect to Mir: Failed to connect to server socket: Datei oder Verzeichnis nicht gefunden
```

The Link from tgalati4 describes not my problem. I have not an auth-error.

When i show my installation-list the unity8 was installed by the dist-upgrade. Is this the reason for the mir-installation?
How  can i go back to a mir-free installation? When i remove unity8 and the  mir-libs and re-install a prog (i.e. synaptic) the mir-libs always re-installed.

Bye Andreas

---

### Post by tgalati4 on 2015-02-24
An in-place distribution upgrade is risky--as you have seen.  Further, adding a desktop environment to a server is probably not what you had in mind.  Point #3, you added [Unity8]("https://wiki.ubuntu.com/Unity8Desktop") which is a desktop preview (beta software) that does indeed run using the mir display server.  Mir does not support X-forwarding.

I'm not sure how to remove mir cleanly.  Perhaps now is the time to back up your data and perform a clean installation of 14.04 server.

---

### Post by akela68 on 2015-02-27
Hi tgalati4,

i doesn't added this packages manually. I install a base-system and add synaptic to the system. This works fine for me in the past.

This server is only a development-server for embedded-systems and not really important. I setup an new server with a debian-system.

Thanks for the support!

Bye Andreas

---

