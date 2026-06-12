---
title: "libwine-cil .NET Problem"
date: 2005-11-05
forum: Gaming &amp; Leisure
---

### Post by gray on 2005-11-05
hi

i'm not sure if it's possible to do what i'll try to do, so i hope you can help me with this prob. I installed wine & cedega & libwin-cil & mono. I'd like to run a .NET C# exe with swf_invoke but it isnt starting.

```
gray@demeter:~/.wine/drive_c/Program Files/Ultima Online 2D/Beta 13$ swf_invoke Client.exe

** (Client.exe:4232): WARNING **: The following assembly referenced from /home/gray/.wine/drive_c/Program Files/Ultima Online 2D/Beta 13/Client.exe could not be loaded:
     Assembly:   Microsoft.DirectX.Direct3D    (assemblyref_index=4)
     Version:    1.0.900.0
     Public Key: 31bf3856ad364e35
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/gray/.wine/drive_c/Program Files/Ultima Online 2D/Beta 13/).


** (Client.exe:4232): WARNING **: The class Microsoft.DirectX.Direct3D.Device could not be loaded, used in /home/gray/.wine/drive_c/Program Files/Ultima Online 2D/Beta 13/Client.exe (token 0x0100003a)

** (Client.exe:4232): WARNING **: The class Microsoft.DirectX.Direct3D.PresentParameters could not be loaded, used in /home/gray/.wine/drive_c/Program Files/Ultima Online 2D/Beta 13/Client.exe (token 0x01000040)

** (Client.exe:4232): WARNING **: The class Microsoft.DirectX.Direct3D.VertexBuffer could not be loaded, used in /home/gray/.wine/drive_c/Program Files/Ultima Online 2D/Beta 13/Client.exe (token 0x01000029)

** ERROR **: file class.c: line 1692 (mono_class_init): assertion failed: (class)
aborting...
/usr/bin/swf_invoke: line 7:  4232 Aborted                 /usr/bin/cli "$@"

```

Another exe starts perfectly but it isn't using any directx at all. So my question is if there is a possibility to use directx with libwine-cil? I tried to change the wineserver in the swf_invoke forum the normal wine wineserver to the cedega wineserver but it doesn't work neither. So please tell me if there is a possibility to use directx.

You might recognize that i try to get the Krrios Client (Ultima Online) workin. If someone is playing with it and has another way then using libwine-cil please tell me. The same if someone has a way to use Razor under linux.

Hope you can help me. :)

---

