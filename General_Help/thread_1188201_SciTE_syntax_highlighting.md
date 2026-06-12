---
title: "SciTE syntax highlighting"
date: 2009-06-15
forum: General Help
---

### Post by crazyfuturamanoob on 2009-06-15
SConstruct/Sconscript files are Python scripts, but SciTE doesn't use Python syntax highlighting for them (it doesn't highlight them at all). How to make SciTE automatically do it?

And GLSL vertex/fragment shading language syntax is almost identical to C, but it has a few different types & keywords. I want to make a 1:1 copy of C++ syntax highlighting settings, modify them and use them for .fs and .vs files.

---

### Post by bhagabhi on 2009-06-16
> SConstruct/Sconscript files are Python scripts, but SciTE doesn't use Python syntax highlighting for them (it doesn't highlight them at all). How to make SciTE automatically do it?

If you open your python.properties, what does the first lines look like? (You can open it in the menu Options->Edit Properties->Open Python.properties) I have 

file.patterns.py=*.py;*.pyw
file.patterns.scons=SConstruct;SConscript

at the top, and SConstruct files at least opens nicely colored (on SciTE 1.78 )

---

### Post by crazyfuturamanoob on 2009-06-16
I have those lines but SciTE doesn't highlight SConstruct/script files.

---

### Post by bhagabhi on 2009-06-16
Your SciteGlobal.properties, at line 590 I have 

import python 

- it might be commented out (an # in the beginning of the line).

Those things are the ones that come to mind immediately...

---

