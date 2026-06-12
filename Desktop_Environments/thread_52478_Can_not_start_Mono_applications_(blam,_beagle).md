---
title: "Can not start Mono applications (blam, beagle)"
date: 2005-07-27
forum: Desktop Environments
---

### Post by fbn on 2005-07-27
Hi,

I get some error messages if I try to run Mono applications:

```

deniedfr@dettnb80:~$ blam

** (Blam:10118): WARNING **: The following assembly referenced from /usr/lib/blam/blam.exe could not be loaded:
     Assembly:   gecko-sharp    (assemblyref_index=12)
     Version:    1.0.0.0
     Public Key: ccf7d78a55e9f021
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/blam).


** (Blam:10118): WARNING **: The class Gecko.WebControl could not be loaded, used in /usr/lib/blam/blam.exe (token 0x01000081)

** (Blam:10118): WARNING **: The class Gecko.WebControl could not be loaded, used in /usr/lib/blam/blam.exe (token 0x01000081)

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00000> <unknown method>
in <0x002e7> Imendio.Blam.Application:.ctor (System.String[] args, System.Object[] props)
in <0x0002c> Imendio.Blam.Application:Main (System.String[] args)

```

```

deniedfr@dettnb80:~$ best

** (/usr/lib/beagle/Best.exe:10140): WARNING **: The following assembly referenced from /usr/lib/beagle/Tiles.dll could not be loaded:
     Assembly:   gecko-sharp    (assemblyref_index=8)
     Version:    1.0.0.0
     Public Key: ccf7d78a55e9f021
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/beagle).


** (/usr/lib/beagle/Best.exe:10140): WARNING **: The class Gecko.WebControl could not be loaded, used in /usr/lib/beagle/Tiles.dll (token 0x0100003c)

** ERROR **: file class.c: line 2119 (mono_class_setup_parent): should not be reached
aborting...
Abgebrochen


```

These are my installed Mono packages:

ii  libmono0       1.1.7-0ubuntu4 libraries for the Mono JIT
ii  mono           1.1.7-0ubuntu4 runtime of mono CLI (.NET)
ii  mono-assemblie 1.1.7-0ubuntu4 architecture specific files for Mono's class
ii  mono-assemblie 1.1.7-0ubuntu4 mono class library
ii  mono-common    1.1.7-0ubuntu4 common files for Mono
ii  mono-devel     1.1.7-0ubuntu4 mono CLI (.NET) runtime with development too
ii  mono-gac       1.1.7-0ubuntu4 mono GAC tool
ii  mono-jay       1.1.7-0ubuntu4 parser generator LALR(1), oriented to Java/.
ii  mono-jit       1.1.7-0ubuntu4 fast CLI (.NET) JIT compiler for Mono
ii  mono-mcs       1.1.7-0ubuntu4 mono C# compiler
ii  mono-utils     1.1.7-0ubuntu4 mono utilities


Am I missing something? How can I fix that error?

Regards,
  Frank

---

### Post by Majlo on 2005-07-28
Hi...

try install libgecko-cil

sudo apt-get install libgecko-cil

For beagle follow [http://beaglewiki.org/Ubuntu_Installation](http://beaglewiki.org/Ubuntu_Installation)

Regards

---

### Post by fbn on 2005-07-28
[QUOTE=Majlo]Hi...

try install libgecko-cil

sudo apt-get install libgecko-cil

For beagle follow [http://beaglewiki.org/Ubuntu_Installation](http://beaglewiki.org/Ubuntu_Installation)

Regards[/QUOTE]

Hi Majlo,

libgecko-cil is already installed ...

another idea?

---

### Post by Majlo on 2005-07-28
I have installed also these packages

libgtk-cil
libgtk2.0-cil
libgnome-cil
libgnome2.0-cil
libglib-cil
libglib2.0-cil
libglade-cil
libglade2.0-cil
libgecko-cil
libgconf-cil
libgconf2.0-cil

Try

---

### Post by fbn on 2005-08-11
I've already installed all these packages.

I followed the instructions on [http://beaglewiki.org/index.php/UbuntuInstall](http://beaglewiki.org/index.php/UbuntuInstall) but I still get the error :(

Any idea?

---

