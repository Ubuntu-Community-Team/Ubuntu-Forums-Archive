---
title: "Matlab 2007b trials"
date: 2009-08-12
forum: Education &amp; Science
---

### Post by Mynameistaken on 2009-08-12
I have been working for a while to get Matlab 2007b to work for me.  Here's what I'm workin' with.
Ubuntu 9.04 32-bit
Desktop effects set to "none" (recent change from "normal")
Matlab 2007b

I have had the "blank window after matlab starts" problem, the "can't type in the command window after opening a second window (usually a figure)" problem, and the "menu bars disappear or look like black blocks problem"

So far, I seemed to have gotten things working and the above problems appear to be fixed using

```

export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/
export AWT_TOOLKIT=MToolkit

```

I still get the following errors at the terminal on startup.  A problem with fonts is all I get from this, anyone know how to deal with this?

Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-arphic-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-arphic-ar pl uming uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-baekmuk-gulim-medium-r-normal--*-140-*-*-c-*-ksc5601.1987-0" to type FontStruct

Also, if anyone knows a way to have desktop effects and matlab together, that would be great.
Thanks

---

