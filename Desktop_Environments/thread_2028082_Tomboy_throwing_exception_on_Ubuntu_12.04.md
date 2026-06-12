---
title: "Tomboy throwing exception on Ubuntu 12.04"
date: 2012-07-17
forum: Desktop Environments
---

### Post by lads on 2012-07-17
Hello everyone,

About a week ago Tomboy stopped functioning, I have it locked to the launcher, and when I click on the icon nothing happens. Launching it from the command line I get this exception:

```
$ tomboy

(Tomboy:11978): libtomboy-WARNING **: Binding '<Alt>F12' failed!


(Tomboy:11978): libtomboy-WARNING **: Binding '<Alt>F11' failed!

[INFO 21:22:52.927] Initializing Mono.Addins
Missing method Init in assembly /usr/local/stage/tomboy/lib/tomboy/addins/Evolution.dll, type GMime.Global
[WARN 21:22:53.214] Couldn't create a NoteAddin instance: Exception has been thrown by the target of an invocation.

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Tomboy.Evolution.EvolutionNoteAddin ---> System.IO.FileNotFoundException: Could not load file or assembly 'gmime-sharp, Version=2.4.0.0, Culture=neutral, PublicKeyToken=2b75c2ad004c52e4' or one of its dependencies.
File name: 'gmime-sharp, Version=2.4.0.0, Culture=neutral, PublicKeyToken=2b75c2ad004c52e4'
  --- End of inner exception stack trace ---
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (System.Reflection.MonoCMethod,object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.TypeInitializationException: An exception was thrown by the type initializer for Tomboy.Evolution.EvolutionNoteAddin ---> System.IO.FileNotFoundException: Could not load file or assembly 'gmime-sharp, Version=2.4.0.0, Culture=neutral, PublicKeyToken=2b75c2ad004c52e4' or one of its dependencies.
File name: 'gmime-sharp, Version=2.4.0.0, Culture=neutral, PublicKeyToken=2b75c2ad004c52e4'
  --- End of inner exception stack trace ---
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (System.Reflection.MonoCMethod,object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0
```

Inquiring at the Tomboy users list I was told to install the package libgmime2.6-cil. But it happens it is already installed:

```
$ dpkg --get-selections | grep libgmime2.6-cil
libgmime2.6-cil                    install
```

Any other clues on what may be causing this?

Thank you.

---

### Post by lads on 2012-07-17
After connecting some of the dots left by the developers in [the thread at the Tomboy users list]("http://comments.gmane.org/gmane.comp.gnome.tomboy/3855"), I managed to attain a simple recipe:

```
$ sudo ln -s /usr/lib/mono/gac/gmime-sharp/2.6.0.0__2b75c2ad004c52e4 /usr/lib/mono/gac/gmime-sharp/2.4.0.0__2b75c2ad004c52e4
```

Tomboy is looking for gmime-sharp 2.4 but in Ubuntu 12.04 there's only gmime-sharp 2.6. You have to lead it believing the old version is still there.

---

### Post by directhex on 2012-07-17
I'm astonished that symlinking like that would work - GMime actually changed in non-backward-compatible ways, which is why the package name changed.

General case: Tomboy in 12.04 is fine, your Tomboy isn't from 12.04 (e.g. it's self-compiled; check `which tomboy`)

---

### Post by lads on 2012-07-18
Hi directhex.

> **directhex said:**
> I'm astonished that symlinking like that would work - GMime actually changed in non-backward-compatible ways, which is why the package name changed.

Believe me it worked. As you can read in the Tomboy list, the program does some kind of search for that directory.

> General case: Tomboy in 12.04 is fine, your Tomboy isn't from 12.04 (e.g. it's self-compiled; check `which tomboy`)

Yes, the version of Tomboy I have is 1.10 and it was compiled from the source. But this was made on the advice of the development team, when some months ago [version 1.08 stopped synchronising with Ubuntu One]("http://ubuntuforums.org/showthread.php?t=1980953"). At that time it was your insight that got everything back to normal.

Best.

---

