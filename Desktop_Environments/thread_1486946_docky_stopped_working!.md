---
title: "docky stopped working!"
date: 2010-05-18
forum: Desktop Environments
---

### Post by craig6b on 2010-05-18
I have been using docky happily and had no problems after updating to 10.04, but then suddenly docky crashed and would not restart. I am getting the following output when I try to run docky from the command line (not sudo):

> [Info  08:18:41.221] Docky version: 2.1.0 bzr docky r1357 ppa
[Info  08:18:41.235] Kernel version: 2.6.32.22
[Info  08:18:41.236] CLR version: 2.0.50727.1433

Unhandled Exception: System.Exception: Unable to open the session message bus. ---> System.Exception: Error 32: Broken pipe
  at NDesk.Unix.UnixSocket.Write (System.Byte* bufP, Int32 count) [0x00000] 
  at NDesk.Unix.UnixSocket.Write (System.Byte[] buf, Int32 offset, Int32 count) [0x00000] 
  at NDesk.Unix.UnixStream.Write (System.Byte[] buffer, Int32 offset, Int32 count) [0x00000] 
  at System.IO.MemoryStream.WriteTo (System.IO.Stream stream) [0x00000] 
  at NDesk.DBus.MessageWriter.ToStream (System.IO.Stream dest) [0x00000] 
  at NDesk.DBus.Message.GetHeaderDataToStream (System.IO.Stream stream) [0x00000] 
  at NDesk.DBus.Transports.Transport.WriteMessage (NDesk.DBus.Message msg) [0x00000] 
  at NDesk.DBus.Connection.Send (NDesk.DBus.Message msg) [0x00000] 
  at NDesk.DBus.Connection.SendWithReply (NDesk.DBus.Message msg) [0x00000] 
  at NDesk.DBus.Connection.SendWithReplyAndBlock (NDesk.DBus.Message msg) [0x00000] 
  at NDesk.DBus.BusObject.SendMethodCall (System.String iface, System.String member, System.String inSigStr, NDesk.DBus.MessageWriter writer, System.Type retType, System.Exception& exception) [0x00000] 
  at org.freedesktop.DBus.IBusProxy.Hello () [0x00000] 
  at NDesk.DBus.Bus.Register () [0x00000] 
  at NDesk.DBus.Bus..ctor (System.String address) [0x00000] 
  at NDesk.DBus.Bus.Open (System.String address) [0x00000] 
  at NDesk.DBus.Bus.get_Session () [0x00000] 
  --- End of inner exception stack trace ---
  at NDesk.DBus.Bus.get_Session () [0x00000] 
  at NDesk.DBus.BusG.Init () [0x00000] 
  at Docky.Docky.Main (System.String[] args) [0x00000] 

Please help!

---

### Post by pepsifx357 on 2010-12-01
I just tried a minute ago, still the same problem.

---

### Post by craig6b on 2010-12-01
> **pepsifx357 said:**
> I just tried a minute ago, still the same problem.
Have you tried updating docky to the newest version? The docky developers have corrected the error that I was getting.

What is your use case that led to your error? I was trying to remotely restart the docky application (over ssh). After the developers made changes, I am able to restart docky overnight with cron such that docky does not balloon and take up all of my system memory overnight.

---

### Post by pepsifx357 on 2010-12-01
I was running docky on an Ubuntu 10.04 install.  I'm not sure if that is up-to-date enough.

---

### Post by craig6b on 2010-12-01
> **pepsifx357 said:**
> I was running docky on an Ubuntu 10.04 install.  I'm not sure if that is up-to-date enough.
is docky up to the latest version though? please see the docky bug reports at [http://bugs.launchpad.net/docky/+bug/582663]("http://bugs.launchpad.net/docky/+bug/582663")

---

