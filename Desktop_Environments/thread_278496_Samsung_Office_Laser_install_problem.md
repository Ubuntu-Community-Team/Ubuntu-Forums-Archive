---
title: "Samsung Office Laser install problem"
date: 2006-10-16
forum: Desktop Environments
---

### Post by hodad on 2006-10-16
I recently installed Ubuntu, and have had various problems getting devices to work.  Getting better at ferreting out these probs as I go, but I'm stuck on the printer driver install for the Samsung 4521F:

From another posting, I followed suggestion of going to Samsung to download printer driver.  I extracted the tarball OK and ran the resulting Autorun file.   GOt the following error messages:

dave@dave-desktop:~/Downloads$ sudo ./cdroot/autorun
libstdc++.so.5 (gcc 3.0.x .. 3.3.x) not found, intstall ... done
libstdc++ v3 (gcc 2.96) not found, intstall ... done
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

********

I then ran the following to see what libraries were there:  

dave@dave-desktop:~/Downloads$ apt -cache search libstdc
bash: apt: command not found
dave@dave-desktop:~/Downloads$ apt-cache search libstdc
libgmp3-dev - Multiprecision arithmetic library developers tools
libstdc++5 - The GNU Standard C++ Library v3
libstdc++5-3.3-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6 - The GNU Standard C++ Library v3
libstdc++6-4.0-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-4.0-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-4.0-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-dev - The GNU Standard C++ Library v3 (development files)
lib32stdc++6-4.0-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++5-3.3-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++5-3.3-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++5-3.3-pic - The GNU Standard C++ Library v3 (shared library subset kit)
libstdc++6-4.0-pic - The GNU Standard C++ Library v3 (shared library subset kit)
libstdc++6-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-pic - The GNU Standard C++ Library v3 (shared library subset kit)


Does anyone know what I should do for my next step?

Thanks in advance for your help!

---

