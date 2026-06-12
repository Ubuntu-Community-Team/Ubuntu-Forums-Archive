---
title: "World of Warcraft stuck at connecting"
date: 2007-04-13
forum: Gaming &amp; Leisure
---

### Post by MakLeod on 2007-04-13
Just installed WoW on my computer.  Everything is working fine, but I keep getting stuck at the "connecting" phase.  Every once in a while I get to "authenticating", but that doesn't happen too often.  Here's is the terminal code which has relevance to the connection process:

fixme:win:EnumDisplayDevicesW ((null),0,0x33f168,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB


I am also using a wireless card to connect if that helps (Atheros chipset).  Thanks!

---

### Post by Amurko on 2007-04-13
In Wine and Cedega, there's an option to choose which OS to "fake"..  I had the same problem when I picked Windows XP but changing it to Windows 98 only made this problem occur maybe 1 in 10.  I hear that some people made it go away by choosing Windows ME.  The moral of the story: try changing and experimenting the OS wine or cedega reports and see if it improves.

---

### Post by MakLeod on 2007-04-13
Tried Windows 2000, ME, and 98 and still having the same problem.  Although it did get to "authenticating" once with Windows 98 emulated.  Any other ideas?

---

### Post by AndrewRiedi on 2007-04-13
I am able to log in with wine pretending to be Windows XP.

---

### Post by MakLeod on 2007-05-01
I think I figured out what the problem was.  After upgrading to Feisty (clean install), WoW worked without a hitch.  I thought about what I had installed in Edgy and forgotten about and I remembered that I installed moblock (similar to peer guardian) to block my ip address from being listed when using p2p applications.  I'm not 100% sure, but I bet that was preventing me from connecting to WoW.  Just an FYI FWIW.  :guitar:

---

### Post by Naegling23 on 2007-05-02
MakLeod: Yup, it was moblock, I had the same problem with it.  Once its installed, you need to keep it running, or remove it, otherwise it will block WoW.

---

### Post by volksolwagen57 on 2010-02-08
I am currently stuck having this problem. I tried faking all of the windows versions. I tried uninstalling firestarter which I used when installing new patches and I still have this problem! Somebody PLEASE help? It's been over three weeks that I've had this snafu and I'm getting desperate! :icon_frown:

---

