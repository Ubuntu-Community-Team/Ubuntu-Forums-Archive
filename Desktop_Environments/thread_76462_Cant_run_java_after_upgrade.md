---
title: "Cant run java after upgrade"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Nasso on 2005-10-15
I wont get violet running after the breezyupgrade :/ anyone got a clue? I hate javas error messages :p
> 
nasso@nassolaptop:/opt$ java -jar violet-0.14.jar
Exception in thread "main" java.lang.NoClassDefFoundError: while resolving class: com.horstmann.violet.EditorFrame
   at java.lang.VMClassLoader.transformException(java.lang.Class, java.lang.Throwable) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.resolveClass(java.lang.Class) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at com.horstmann.violet.UMLEditor.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: java.beans.PersistenceDelegate not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:violet-0.14.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   ...5 more


---

### Post by fishfork on 2005-10-15
This is probably because Breezy installs free Java and enables it by default. You need to tell it to use Sun Java instead:

Run:

```
sudo update-alternatives --config java
```

and select the Sun JRE as default.

---

### Post by Nasso on 2005-10-15
[QUOTE=fishfork]This is probably because Breezy installs free Java and enables it by default. You need to tell it to use Sun Java instead:

Run:

```
sudo update-alternatives --config java
```

and select the Sun JRE as default.[/QUOTE]

Oh my god. You got no idea how grateful i am!! :D thanks! it though i whould have to do alot of reinstalling and fuzz :)

---

### Post by fishfork on 2005-10-15
No problem! I've added it to the Wiki page on Java.

---

