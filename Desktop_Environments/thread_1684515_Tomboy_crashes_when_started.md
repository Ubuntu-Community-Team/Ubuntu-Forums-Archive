---
title: "Tomboy crashes when started"
date: 2011-02-09
forum: Desktop Environments
---

### Post by krackersk on 2011-02-09
Hi,

When I start Tomboy the applet comes up on the task bar and then it crashes.

I have tried re-installing Tomboy and Mono but it still happens.

I ran Tomboy --debug in the terminal and this is the output:


  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00068>
  at Mono.Addins.Serialization.BinaryXmlReader.SkipToValue (string) <0x00060>
  at Mono.Addins.Serialization.BinaryXmlReader.ReadStringValue (string) <0x00013>
  at Mono.Addins.Database.FileDatabase.OpenFileForPath (string,string,Mono.Addins.Serialization.BinaryXmlTypeMap,bool,object&) <0x00097>
  at Mono.Addins.Database.FileDatabase.ReadSharedObject (string,string,string,string,Mono.Addins.Serialization.BinaryXmlTypeMap,bool,string&) <0x00066>
  at Mono.Addins.Database.FileDatabase.ReadSharedObject (string,string,string,string,Mono.Addins.Serialization.BinaryXmlTypeMap,string&) <0x00021>
  at Mono.Addins.Database.AddinScanFolderInfo.Read (Mono.Addins.Database.FileDatabase,string,string) <0x00054>
  at Mono.Addins.Database.AddinDatabase.GetFolderInfoForPath (Mono.Addins.IProgressStatus,string,Mono.Addins.Database.AddinScanFolderInfo&) <0x0003d>
  at Mono.Addins.Database.AddinDatabase.GetFolderDomain (Mono.Addins.IProgressStatus,string) <0x0001e>
  at Mono.Addins.AddinRegistry..ctor (string,string) <0x000bb>
  at Mono.Addins.AddinManager.Initialize (string) <0x00107>
  at Tomboy.AddinManager.InitializeMonoAddins (string) <0x0025c>
  at Tomboy.AddinManager..ctor (string,string) <0x0008a>
  at Tomboy.NoteManager.Initialize () <0x002e0>
  at Tomboy.Tomboy/<Main>c__AnonStorey2.<>m__0 () <0x00019>
  at GLib.Timeout/TimeoutProxy.Handler () <0x00034>
  at (wrapper native-to-managed) GLib.Timeout/TimeoutProxy.Handler () <0x00051>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
  at Gtk.Application.Run () <0x0000a>
  at Gnome.Program.Run () <0x0000a>
  at Tomboy.GnomeApplication.StartMainLoop () <0x00016>
  at Tomboy.Application.StartMainLoop () <0x0001c>
  at Tomboy.Tomboy.StartTrayIcon () <0x00047>
  at Tomboy.Tomboy.Main (string[]) <0x00354>
  at (wrapper runtime-invoke) <Module>.runtime_invoke_void_object (object,intptr,intptr,intptr) <0x00043>

Native stacktrace:

	mono() [0x80d4d0b]
	mono() [0x810ffeb]
	[0x8cc40c]
	mono() [0x81efebe]
	mono() [0x81f13fd]
	mono() [0x81b566e]
	[0x3f44e9]
	[0x3f4436]
	[0x4978d77]
	[0x4978bbc]
	[0x4978ab1]
	[0x4978efe]
	[0x4978f11]
	[0x4978f11]
	[0x4978f11]
	[0x4978f11]
	[0x4978f11]
	[0x4978f11]
	[0x4978f11]
	[0x4978f11]
	[0x4978f11]
	[0x4978f11]
	[0x4978f11]
	[0x4978f11]
... (I took out more of this line)
	[0x4978f11]
	[0x4978f11]
	[0x4978f11]
	[0x4978f11]
	[0x4978f11]
	[0x4978f11]

Debug info from gdb:

Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted


Any help is appreciated

---

### Post by directhex on 2011-02-10
Try erasing ~/.config/tomboy/addin*

---

### Post by krackersk on 2011-02-10
Genius. It worked

---

