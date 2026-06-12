---
title: "Xbgm"
date: 2006-01-16
forum: General Help
---

### Post by drumlight on 2006-01-16
Hi I've been trying to run this program but am having trouble with one of the gtk-sharp assemblies. I'm only a couple of weeks into running linux so keep coming to dead ends in troubleshooting.
> ** (/usr/share/dotnet/xbgmsharp/xbgmsharp.exe:3233): WARNING **: The following assembly referenced from /usr/share/dotnet/xbgmsharp/xbgmsharp.exe could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=1)
     Version:    2.0.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/share/dotnet/xbgmsharp).

I ran it with debug log level in mono and can see it fail to find the gtk-sharp dll. I can locate this file a couple of places and have tried adding it to to MONO_PATH (export MONO_PATH=/usr/lib/mono/gtk-sharp-2.0:$MONO_PATH) but it doesn't seem t be working. 
Any guidance on how to get this going would be great.

---

