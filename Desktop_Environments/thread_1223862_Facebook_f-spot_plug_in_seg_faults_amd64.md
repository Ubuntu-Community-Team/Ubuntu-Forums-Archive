---
title: "Facebook f-spot plug in seg faults amd64"
date: 2009-07-26
forum: Desktop Environments
---

### Post by misha680 on 2009-07-26
Using hardy. This is when log in to facebook from F-spot.

[http://bugzilla.gnome.org/show_activity.cgi?id=589816](http://bugzilla.gnome.org/show_activity.cgi?id=589816)

maybe same as?
[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/363067](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/363067)

```

Starting new FSpot server
Reloading
item changed

(f-spot:9800): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.InvalidOperationException: There is an error in XML document. ---> System.InvalidOperationException: <friends_get_response xmlns='http://api.facebook.com/1.0/'> was not expected
  at System.Xml.Serialization.XmlSerializationReaderInterpreter.ReadRoot (System.Xml.Serialization.XmlTypeMapping rootMap) [0x00000] 
  at System.Xml.Serialization.XmlSerializationReaderInterpreter.ReadRoot () [0x00000] 
  at System.Xml.Serialization.XmlSerializer.Deserialize (System.Xml.Serialization.XmlSerializationReader reader) [0x00000] --- End of inner exception stack trace ---

  at System.Xml.Serialization.XmlSerializer.Deserialize (System.Xml.Serialization.XmlSerializationReader reader) [0x00000] 
  at System.Xml.Serialization.XmlSerializer.Deserialize (System.Xml.XmlReader xmlReader) [0x00000] 
  at System.Xml.Serialization.XmlSerializer.Deserialize (System.IO.Stream stream) [0x00000] 
  at Mono.Facebook.Util.GetResponse[FriendsResponse] (System.String method_name, Mono.Facebook.FacebookParam[] parameters) [0x00000] 
  at Mono.Facebook.FacebookSession.GetFriends () [0x00000] 
  at FSpot.Exporter.Facebook.FacebookExport.HandleLoginClicked (System.Object sender, System.EventArgs args) [0x00000] 
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Signal.voidObjectCallback(IntPtr handle, IntPtr data)
   at GLib.Signal.voidObjectCallback(IntPtr , IntPtr )
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at FSpot.Driver.Main(System.String[] args)
Segmentation fault (core dumped)

```

Misha

p.s.

```

misha@misha-d630:~$ dpkg -l | grep mono
ii  libmono-addins-gui0.2-cil                  0.3.1-4                                                    GTK# frontend library for Mono.Addins
ii  libmono-addins0.2-cil                      0.3.1-4                                                    addin framework for extensible CLI applicati
ii  libmono-cairo1.0-cil                       1.2.6+dfsg-6ubuntu3                                        Mono Cairo library
ii  libmono-cairo2.0-cil                       1.2.6+dfsg-6ubuntu3                                        Mono Cairo library
ii  libmono-corlib1.0-cil                      1.2.6+dfsg-6ubuntu3                                        Mono core library (1.0)
ii  libmono-corlib2.0-cil                      1.2.6+dfsg-6ubuntu3                                        Mono core library (2.0)
ii  libmono-data-tds1.0-cil                    1.2.6+dfsg-6ubuntu3                                        Mono Data library
ii  libmono-data-tds2.0-cil                    1.2.6+dfsg-6ubuntu3                                        Mono Data Library
ii  libmono-dev                                1.2.6+dfsg-6ubuntu3                                        libraries for the Mono JIT - Development fil
ii  libmono-peapi1.0-cil                       1.2.6+dfsg-6ubuntu3                                        Mono PEAPI library
ii  libmono-relaxng1.0-cil                     1.2.6+dfsg-6ubuntu3                                        Mono Relaxng library
ii  libmono-security1.0-cil                    1.2.6+dfsg-6ubuntu3                                        Mono Security library
ii  libmono-security2.0-cil                    1.2.6+dfsg-6ubuntu3                                        Mono Security library
ii  libmono-sharpzip0.84-cil                   1.2.6+dfsg-6ubuntu3                                        Mono SharpZipLib library
ii  libmono-sharpzip2.84-cil                   1.2.6+dfsg-6ubuntu3                                        Mono SharpZipLib library
ii  libmono-sqlite2.0-cil                      1.2.6+dfsg-6ubuntu3                                        Mono Sqlite library
ii  libmono-system-data1.0-cil                 1.2.6+dfsg-6ubuntu3                                        Mono System.Data library
ii  libmono-system-data2.0-cil                 1.2.6+dfsg-6ubuntu3                                        Mono System.Data Library
ii  libmono-system-runtime1.0-cil              1.2.6+dfsg-6ubuntu3                                        Mono System.Runtime library
ii  libmono-system-web1.0-cil                  1.2.6+dfsg-6ubuntu3                                        Mono System.Web library
ii  libmono-system-web2.0-cil                  1.2.6+dfsg-6ubuntu3                                        Mono System.Web Library
ii  libmono-system1.0-cil                      1.2.6+dfsg-6ubuntu3                                        Mono System libraries (1.0)
ii  libmono-system2.0-cil                      1.2.6+dfsg-6ubuntu3                                        Mono System libraries (2.0)
ii  libmono0                                   1.2.6+dfsg-6ubuntu3                                        libraries for the Mono JIT
ii  libmono1.0-cil                             1.2.6+dfsg-6ubuntu3                                        Mono libraries (1.0)
ii  libmono2.0-cil                             1.2.6+dfsg-6ubuntu3                                        Mono libraries (2.0)
ii  mono-1.0-devel                             1.2.6+dfsg-6ubuntu3                                        Mono development tools for CLI 1.0
ii  mono-common                                1.2.6+dfsg-6ubuntu3                                        common files for Mono
ii  mono-gac                                   1.2.6+dfsg-6ubuntu3                                        Mono GAC tool
ii  mono-gmcs                                  1.2.6+dfsg-6ubuntu3                                        Mono C# 2.0 and C# 3.0 compiler for CLI 2.0
ii  mono-jit                                   1.2.6+dfsg-6ubuntu3                                        fast CLI JIT/AOT compiler for Mono
ii  mono-mcs                                   1.2.6+dfsg-6ubuntu3                                        Mono C# compiler for CLI 1.1
ii  mono-runtime                               1.2.6+dfsg-6ubuntu3                                        Mono runtime
ii  mono-utils                                 1.2.6+dfsg-6ubuntu3                                        Mono utilities
misha@misha-d630:~$ Starting new FSpot server

```

---

### Post by directhex on 2009-07-26
Looks like a GTK# bug in hardy

---

