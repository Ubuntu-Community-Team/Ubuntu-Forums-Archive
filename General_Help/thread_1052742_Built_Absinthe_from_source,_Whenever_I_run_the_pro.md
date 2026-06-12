---
title: "Built Absinthe from source, Whenever I run the program I get this error Unhandled Exc"
date: 2009-01-28
forum: General Help
---

### Post by Panarchy on 2009-01-28
Hi

Just built [absinthe]("http://www.0x90.org/releases/absinthe/") from source.

Now, whenever I build it (yes I've tried rebuilding), then run it, I get this message;

```
panarchy@hiscomp:~$ absinthe

Unhandled Exception: System.DllNotFoundException: wx-c
  at (wrapper managed-to-native) wx.App:wxApp_ctor ()
  at wx.App..ctor () [0x00000] 
  at MyApp..ctor () [0x00000] 
  at MyApp.Main () [0x00000] 

```

Please tell me how to fix this error.

Thanks in advance,

Panarchy

PS: The program also had this 'disclaimer' at the end of the build process;
(You will need to have at least Mono v1.0 to run Absinthe)

---

