---
title: "Anyone using gTVlistings?"
date: 2006-04-02
forum: Desktop Environments
---

### Post by Etoile on 2006-04-02
Is anyone using [gTVlistings](http://gtvlistings.sourceforge.net/)?  It looks like a nifty program but I'm having trouble making it work.  I followed the (very brief) installation instructions, which were:
> 	There is currently no installer
	so simply copy the gtvlistings folder to /usr/share
	and copy the gtvlistings.desktop file to /usr/share/applications
But when I go to /usr/share/gtvlistings and try to run ./gtvlistings this is what I get:
```
** (/usr/share/gtvlistings/gtvlistings.exe:15978): WARNING **: The following assembly referenced from /usr/share/gtvlistings/gtvlistings.exe could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=1)
     Version:    1.0.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/share/gtvlistings).


** (/usr/share/gtvlistings/gtvlistings.exe:15978): WARNING **: Missing method Init in assembly /usr/share/gtvlistings/gtvlistings.exe, type Gtk.Application

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
```
I installed the packages mono, mono-classlib-1.0, mono-common, mono-jit, xmltv, xmltv-gui, and xmltv-util prior to attempting installation of gTVlistings.  I'm not sure if I missed a mono package or what.  Can anybody parse those error messages and give me some tips?  Thanks!

---

### Post by MonkeyNet on 2006-06-13
[QUOTE=Etoile]Is anyone using [gTVlistings](http://gtvlistings.sourceforge.net/)?  It looks like a nifty program but I'm having trouble making it work.  I followed the (very brief) installation instructions, which were:

But when I go to /usr/share/gtvlistings and try to run ./gtvlistings this is what I get:
```
** (/usr/share/gtvlistings/gtvlistings.exe:15978): WARNING **: The following assembly referenced from /usr/share/gtvlistings/gtvlistings.exe could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=1)
     Version:    1.0.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/share/gtvlistings).


** (/usr/share/gtvlistings/gtvlistings.exe:15978): WARNING **: Missing method Init in assembly /usr/share/gtvlistings/gtvlistings.exe, type Gtk.Application

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
```
I installed the packages mono, mono-classlib-1.0, mono-common, mono-jit, xmltv, xmltv-gui, and xmltv-util prior to attempting installation of gTVlistings.  I'm not sure if I missed a mono package or what.  Can anybody parse those error messages and give me some tips?  Thanks![/QUOTE]

Hey there,

Installed Mono and gTVListings on my machine this evening. Had the same problem. In your Synaptic Package Manager, you need to install the gtk-sharp package. It will also install other dependent packages as well. Now i'm just trying to work out XMLTV so I can start using it. Let me know if you have an further probs.

Cheers,

Andrew

---

