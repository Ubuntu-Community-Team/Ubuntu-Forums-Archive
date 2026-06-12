---
title: "Can't install Doomsday on Linux Mint"
date: 2008-11-16
forum: Gaming &amp; Leisure
---

### Post by marianogedisman on 2008-11-16
Hello everyone!
                I'm having an issue with installing the game as explained on the website [http://gaming.gwos.org/doku.php/guides:64bit:doomsday]("http://gaming.gwos.org/doku.php/guides:64bit:doomsday")

I've downloaded all the sources, but I get lost on the following part:

```
cd ~/Desktop
tar zxfv deng-1.9.0-beta5.1.tar.gz
cd deng-1.9.0-beta5.2/deng-1.9.0-beta5.1/doomsday/build
cmake ../
make
sudo checkinstall
```

How can I cd to deng-1.9.0-beta5.2 if this has never been created?

---

### Post by Burneddi on 2008-11-16
I'm not sure why it directs you to deng-1.9.0-beta5.2-directory instead of beta5.1 directory, because you are handling beta5.1 as far as I see.

If you have untarred the package to your desktop, you should have directory called deng-1.9.0-beta5.1 on your desktop. Try first checking with Nautilus (or whatever file manager you have) if that folder contains the folder /doomsday/build/ - and if yes, do
```
cd deng-1.9.0-beta5.1/doomsday/build
cmake ../
make
sudo checkinstall
``` which should complete the install from the point you were stuck in.

I hope you got my point, my post might've been a bit messy because of this tiredness :).

---

### Post by marianogedisman on 2008-11-16
```
mariano@tetrix ~/Desktop/deng-1.9.0-beta5.1/doomsday/build $ cmake ../
CMake Error: The source directory "/home/mariano/Desktop/deng-1.9.0-beta5.1/doomsday" does not appear to contain CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.
```

---

### Post by dragonny on 2009-01-22
> **marianogedisman said:**
> ```
mariano@tetrix ~/Desktop/deng-1.9.0-beta5.1/doomsday/build $ cmake ../
CMake Error: The source directory "/home/mariano/Desktop/deng-1.9.0-beta5.1/doomsday" does not appear to contain CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.
```

I have same problem...

---

