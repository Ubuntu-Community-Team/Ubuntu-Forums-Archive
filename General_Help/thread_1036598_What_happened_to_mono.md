---
title: "What happened to mono?"
date: 2009-01-11
forum: General Help
---

### Post by BroadArrow on 2009-01-11
What happened to the mono package in 8.10?

In previous installations I've installed mono (and its dependencies) to run a Windows based programme (a XMLTV programme guide grabber) and it worked fine. 

However, on a new installation of 8.10 I can't find a mono package so I've tried installing some of the obvious components but can't get the programme to work. I'm obviously missing some essential dependencies.

Has the mono package now been deprecated? If so, what do I need to install to have the same functionality as before?

---

### Post by directhex on 2009-01-11
There is no "mono" metapackage, as it was undefined as to its purpose.

To eliminate bloat, Mono is heavily split, with apps able to depends ONLY on what they need (not on everything in one go).

Generally speaking, mono-runtime will give you the core of things (including the 'mono' command), and from there, simply install the libs you need - e.g. a complaint from your app about a missing System.Windows.Forms 2.0.0.0 requires the libmono-winforms2.0-cil package

---

### Post by BroadArrow on 2009-01-12
> **directhex said:**
> There is no "mono" metapackage, as it was undefined as to its purpose.

To eliminate bloat, Mono is heavily split, with apps able to depends ONLY on what they need (not on everything in one go).

Generally speaking, mono-runtime will give you the core of things (including the 'mono' command), and from there, simply install the libs you need - e.g. a complaint from your app about a missing System.Windows.Forms 2.0.0.0 requires the libmono-winforms2.0-cil package


So for those of us without any knowledge of the inner workings of the various mono packages it'll be a bit of a game of hit and miss. I'll have a go and see how I go!

---

### Post by BroadArrow on 2009-01-12
I can't work out which mono package I need. This is the error message I get:

```
** (/data/TVGuide/xmlTVNZ_3.0.0.12/xmlTVNZ.exe:7428): WARNING **: The following assembly referenced from /data/TVGuide/xmlTVNZ_3.0.0.12/xmlTVNZ.exe could not be loaded:
     Assembly:   System.Xml    (assemblyref_index=3)
     Version:    2.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/data/TVGuide/xmlTVNZ_3.0.0.12).


** (/data/TVGuide/xmlTVNZ_3.0.0.12/xmlTVNZ.exe:7428): WARNING **: Could not load file or assembly 'System.Xml, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: A type load exception has occurred.

```

---

### Post by directhex on 2009-01-12
> **BroadArrow said:**
> I can't work out which mono package I need. This is the error message I get:

```
** (/data/TVGuide/xmlTVNZ_3.0.0.12/xmlTVNZ.exe:7428): WARNING **: The following assembly referenced from /data/TVGuide/xmlTVNZ_3.0.0.12/xmlTVNZ.exe could not be loaded:
     Assembly:   System.Xml    (assemblyref_index=3)
     Version:    2.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/data/TVGuide/xmlTVNZ_3.0.0.12).


** (/data/TVGuide/xmlTVNZ_3.0.0.12/xmlTVNZ.exe:7428): WARNING **: Could not load file or assembly 'System.Xml, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: A type load exception has occurred.

```

```
jms@osc-franzibald:~$ apt-file search System.Xml.dll | grep 2.0
libmono-system2.0-cil: /usr/lib/mono/2.0/System.Xml.dll
libmono-system2.0-cil: /usr/lib/mono/gac/System.Xml/2.0.0.0__b77a5c561934e089/System.Xml.dll
mono-dbg: /usr/lib/mono/gac/System.Xml/2.0.0.0__b77a5c561934e089/System.Xml.dll.mdb
```

So... libmono-system2.0-cil

You'll also be wanting libmono-system-runtime2.0-cil:

```
jms@osc-franzibald:/tmp$ monodis --assemblyref xmlTVNZ.exe 
AssemblyRef Table
1: Version=2.0.0.0
	Name=mscorlib
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
2: Version=2.0.0.0
	Name=System.Xml
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
3: Version=2.0.0.0
	Name=System
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
4: Version=2.0.0.0
	Name=System.Runtime.Serialization.Formatters.Soap
	Flags=0x00000000
	Public Key:
0x00000000: B0 3F 5F 7F 11 D5 0A 3A 

jms@osc-franzibald:/tmp$ apt-file search System.Runtime.Serialization.Formatters.Soap.dll | grep 2.0
libmono-system-runtime2.0-cil: /usr/lib/mono/2.0/System.Runtime.Serialization.Formatters.Soap.dll
libmono-system-runtime2.0-cil: /usr/lib/mono/gac/System.Runtime.Serialization.Formatters.Soap/2.0.0.0__b03f5f7f11d50a3a/System.Runtime.Serialization.Formatters.Soap.dll
mono-dbg: /usr/lib/mono/gac/System.Runtime.Serialization.Formatters.Soap/2.0.0.0__b03f5f7f11d50a3a/System.Runtime.Serialization.Formatters.Soap.dll.mdb
```

---

### Post by BroadArrow on 2009-01-14
Thanks for that. Working perfectly.

I didn't know about apt-file (and had to install it) so thanks for the heads up. I'm sure I'll need it again!

---

