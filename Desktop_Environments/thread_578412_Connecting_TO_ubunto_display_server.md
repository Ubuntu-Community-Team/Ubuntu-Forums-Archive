---
title: "Connecting *TO* ubunto display server"
date: 2007-10-17
forum: Desktop Environments
---

### Post by BrooklineTom on 2007-10-17
I'm using ubuntu as a guest inside vmware on my WinXP box, so that I can use a local display server to run applications on a remote linux host. In this case, I want to run "wingIDE" -- a python development IDE -- on a remote host. The remote wingIDE attempts to tunnel through SSH back into my PC, where it will hopefully connect to the X-windows display server inside Ubuntu inside my vmware virtual machine. Whew.

I've already been able to make a similar connection work using a display server running within cygwin on the pc. In that configuration, the tunneling works fine and wingIDE (on the remote host) actually comes up within the xwindows desktop and runs. Well, walks. Crawls. The claim -- and hope -- is that vmware/ubuntu will offer greatly improved performance and usability.

My problem, now, is that it looks as though the ubuntu/vmware application isn't opening the port through the various firewalls. As nearly as I can tell, everything is running fine on the ubuntu desktop. I can use firefox within it, and I appear to have full net access from inside the ubuntu desktop.

I'm using secureCRT as my SSH client, and I have the "Forward XLL Packets" option enabled. When I attempt to start wing3.0 through the SSH connection -- the same connection that works using cygwin -- it complains as follows:

"The application 'wing.py' lost its connection to the display localhost:10.0;
most likely the X server was shut down or you killed/destroyed
the application."

I'm new to ubuntu (though not to linux/unix). I'm hoping that folks here can offer some help, specifically as to whether there's something I'm missing in my new ubuntu configuration, or whether this is perhaps a vmware problem, or whether I need to start digging around in WinXP (I hope not).

Again, the tunneling connection back to the pc worked under cygwin and fails under vmware/ubuntu.

Ideas?

Thanks,
Tom

---

### Post by BrooklineTom on 2007-10-17
Duh. I forgot that the vmware really DOES create a different machine. The "secureCRT" on the winXP desktop has no connection to the ubuntu guest running inside the vmware app. The solution is to connect to the remote system from inside ubuntu.

Here, for others who have to learn the same thing, is how:

1. Open a terminal on the ubuntu desktop.
2. Use "ssh" to create a connection w/ tunnel: "ssh -Y -lyourloginname yourserver.domain
3. Provide whatever password is required.
4. Run the executable. Any x-windows it opens will appear on your (local) ubuntu desktop.

This is really cool. And *much* faster than cygwin, as hoped.

---

