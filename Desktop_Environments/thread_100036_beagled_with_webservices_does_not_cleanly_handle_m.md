---
title: "beagled with webservices does not cleanly handle multiple instances / --replace"
date: 2005-12-06
forum: Desktop Environments
---

### Post by bkanuka on 2005-12-06
I can't start beagled.  Even beagled --replace.

My problem is perfectly described here:  [http://bugzilla.gnome.org/show_bug.cgi?id=317622]("http://bugzilla.gnome.org/show_bug.cgi?id=317622")

My exact output is:
```
Unhandled Exception: System.Net.Sockets.SocketException: Address already in use
in <0x000cb> System.Net.Sockets.Socket:Bind (System.Net.EndPoint)
in <0x00022> System.Net.Sockets.TcpListener:Start ()
in <0x00056> System.Runtime.Remoting.Channels.Tcp.TcpServerChannel:StartListening (object)
in <0x0001c> System.Runtime.Remoting.Channels.Tcp.TcpChannel:StartListening (object)
in <0x002bc> System.Runtime.Remoting.Channels.ChannelServices:RegisterChannel (System.Runtime.Remoting.Channels.IChannel)
in <0x00053> Beagle.WebService.WebBackEnd:init ()
in <0x0025b> Beagle.WebService.WebServiceBackEnd:Start ()
in <0x0018a> Beagle.Daemon.BeagleDaemon:StartupProcess ()
in <0x00048> (wrapper delegate-invoke) System.MulticastDelegate:invoke_bool ()
in <0x0002a> IdleProxy:Handler ()
in <0x00036> (wrapper native-to-managed) IdleProxy:Handler ()
in (unmanaged) 0xb7ede74f
in <0x00004> (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x0057b> Beagle.Daemon.BeagleDaemon:Main (string[])

```

The bugzilla says that it's fixed but it's obviously not for me.  Am I missing something?

---

