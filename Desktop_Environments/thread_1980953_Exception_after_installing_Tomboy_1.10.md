---
title: "Exception after installing Tomboy 1.10"
date: 2012-05-16
forum: Desktop Environments
---

### Post by lads on 2012-05-16
Dear all,

I use Tomboy Notes synchronised with Ubuntu One so that I can access my notes from every where, office, home, etc. Some weeks ago synchronisation stopped working at home and at the advice of the folks at the Tomboy IRC channel, I removed the version I had (1.8) and installed the latest (1.10). Unfortunately, with this new version I'm getting the exception listed below. This is on Ubuntu 11.10 32 bit.

I have seek help at the IRC but answers there are intermittent. I also [posted a message to the mailing list]("http://gnome-tomboy.1788872.n4.nabble.com/Exception-after-installing-Tomboy-1-10-tp4622737.html") but no answer there either. So, knowing that this is isn't the exact place to ask for help, I recur once again to the Ubuntu Forum. Any information on how to overcome the issue is very welcome.

Thank you.

```
$ mono Tomboy.exe
Missing method System.Threading.Monitor::Enter(object,bool&) in assembly /usr/lib/mono/2.0/mscorlib.dll, referenced in assembly /usr/lib/mono/gac/dbus-sharp/1.0.0.0__5675b0c3093115b5/dbus-sharp.dll

Unhandled Exception: System.Exception: Unable to open the system message bus. ---> System.MissingMethodException: Method not found: 'System.Threading.Monitor.Enter'.
  at DBus.BusObject.GetObject (DBus.Connection conn, System.String bus_name, DBus.ObjectPath object_path, System.Type declType) [0x00000] in <filename unknown>:0 
  at DBus.Connection.GetObject (System.Type type, System.String bus_name, DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at DBus.Connection.GetObject[IBus] (System.String bus_name, DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at DBus.Bus..ctor (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  at DBus.BusG.Init () [0x00000] in <filename unknown>:0 
  at Tomboy.GnomeApplication.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] in <filename unknown>:0 
  at Tomboy.Application.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] in <filename unknown>:0 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.Exception: Unable to open the system message bus. ---> System.MissingMethodException: Method not found: 'System.Threading.Monitor.Enter'.
  at DBus.BusObject.GetObject (DBus.Connection conn, System.String bus_name, DBus.ObjectPath object_path, System.Type declType) [0x00000] in <filename unknown>:0 
  at DBus.Connection.GetObject (System.Type type, System.String bus_name, DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at DBus.Connection.GetObject[IBus] (System.String bus_name, DBus.ObjectPath path) [0x00000] in <filename unknown>:0 
  at DBus.Bus..ctor (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at DBus.Bus.get_System () [0x00000] in <filename unknown>:0 
  at DBus.BusG.Init () [0x00000] in <filename unknown>:0 
  at Tomboy.GnomeApplication.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] in <filename unknown>:0 
  at Tomboy.Application.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] in <filename unknown>:0 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] in <filename unknown>:0
```

---

### Post by lads on 2012-05-17
Dear all,

The Tomboy folks remain silent. Today I found [this bug report]("https://bugzilla.gnome.org/process_bug.cgi"), that essentially says that Tomboy 1.10 by default doesn't run on Ubuntu 11.10. The fix suggested there is to include the "--runtime=v4.0" argument in the tomboy script. Hence I changed my script to:

```
MONO_OPTIONS="$TOMBOY_DEBUG $TOMBOY_TRACE $TOMBOY_PROFILE $MONO_EXTRA_ARGS --runtime=v4.0"
```

Still I get the exception reported initially. In the bug report there's a link to [a page detailing the issue]("http://orangesquash.org.uk/~laney/blog/posts/2011/10/mono-gotcha/"). Here the suggestion is to include this argument when invoking mono. I did so, but there's no reaction, the application simply freezes:

```
$ mono --runtime=v4.0 Tomboy.exe
[INFO 11:31:36.484] Initializing Mono.Addins
```

If I understand it correctly, I have to recompile Tomboy, but against the mono-csc compiler. Could someone explain how to do this?

Thank you.

---

### Post by directhex on 2012-05-17
> **lads said:**
> ```
$ mono Tomboy.exe
Missing method System.Threading.Monitor::Enter(object,bool&) in assembly /usr/lib/mono/2.0/mscorlib.dll, referenced in assembly /usr/lib/mono/gac/dbus-sharp/1.0.0.0__5675b0c3093115b5/dbus-sharp.dll
```

Looks like your Tomboy, or one of its dependencies, is not compiled for Ubuntu 11.10+

As of Oneiric, all Mono apps need to be compiled for .NET 4.0, regardless of what the app's build system uses.

All packages in the archive have been updated to deal with this, but your Tomboy, whatever non-Ubuntu place it comes from, has not.

---

### Post by directhex on 2012-05-17
> **lads said:**
> If I understand it correctly, I have to recompile Tomboy, but against the mono-csc compiler. Could someone explain how to do this?

Thank you.

So you compiled this Tomboy yourself?

Pass GMCS=/usr/bin/mono-csc to ./configure. That should be enough to force a 4.0 build.

---

### Post by lads on 2012-05-18
Thank you directhex. The developers have finally chimed in at the mail list and they are providing the same advice as you. Will report back as soon as I can try it out.

---

### Post by lads on 2012-05-24
Just to close this thread. The advice provided by directhex allowed me to install Tomboy 1.10 on Ubuntu 11.10. Now everything works as it should.

---

