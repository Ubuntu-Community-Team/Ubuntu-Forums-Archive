---
title: "WineCVS and World of Warcraft"
date: 2005-07-09
forum: Gaming &amp; Leisure
---

### Post by tbasten on 2005-07-09
Hi.

I have been trying to get World of warcraft to work with wineCVS. I followed all of the tutorial on these forums to install wineCVS and other stuff for it. I am getting this error when trying to run WoW

tbasten@Dyna:~/winetools/sys $ wine /wow/World\ of\ Warcraft/WoW.exe
wine: Call from 0x5ed09ec5 to unimplemented function KERNEL32.dll.IsWow64Process, aborting
wine: Unhandled exception (thread 0009), starting debugger...
Usage: winedbg [--command cmd|--auto] [--gdb [--no-start] [--with-xterm]] cmdline
err:seh:EXC_DefaultHandling Unhandled exception code c000013a flags 0 addr 0x400e5e76
tbasten@Dyna:~/winetools/sys $ 

I was getting some errors throught wine tools when trying to install fonts or other stuff. This is some of ther error message

downloading [http://download.microsoft.com/download/vb60pro/Redist/sp5/WIN98Me/EN-US/vbrun60sp5.exe](http://download.microsoft.com/download/vb60pro/Redist/sp5/WIN98Me/EN-US/vbrun60sp5.exe) to vbrun60sp5.exe with 1044168 bytes...
WINEDLLOVERRIDES="" wine ./vbrun60sp5.exe
waiting for wineservers to exit...
Warning: could not find DOS drive for current working directory '/home/tbasten/winetools/sys', starting in the Windows directory.
wine: cannot find './vbrun60sp5.exe'
all wineservers endet after 2 seconds...
Failed: 1
check installation by return value...
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Failed: 1
\*new\* fake Windows drive
software installation verified by /home/tbasten/.wine/winetools.log
dependency \*new\*
dcom98.exe
software installation verified by /home/tbasten/.wine/winetools.log
dependency dcom98.exe *not* fulfilled
Microsoft Internet Explorer.*
software installation verified by /home/tbasten/.wine/winetools.log
dependency Microsoft
Choice is Visual Basic 6 Runtime
vbrun60sp5.exe
software installation verified by /home/tbasten/.wine/winetools.log

Can someone help me?

---

