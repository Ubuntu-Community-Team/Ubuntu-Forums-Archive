---
title: "Telnet Clients that support VT102 Control Codes?"
date: 2006-04-21
forum: Desktop Environments
---

### Post by Video Toaster on 2006-04-21
After logging on to my local library's INNOPAC server using the telnet command, I found that I could not print forms directly to my local printer as I could using NetTerm on Windows.  After doing some research, I found that INNOPAC uses VT102 printer control codes to handle printing to the local printer.  Are there any Linux telnet clients that can handle that?  (I already tried running NetTerm via Wine, but it froze soon after logon :D)

---

### Post by slushy77 on 2006-04-26
have you tried using konsole or gnome-terminal or even xterm(the original vt102 emulator) ? It seems a bit long-winded to use wine to run a windows based terminal emulator, when you have native terminal emulators.](*,) 

use synaptic or adept to install the telnet client and either konsole(should be installed already if your running kde) or gnome-terminal. 
 
invoke konsole or gnome-terminal from the menu and just type ```
telnet <server>
``` both have options to print output in their menus

---

### Post by Video Toaster on 2006-04-26
Thanks for your reply!

Yes, that was the first thing I tried.  Telnet in Konsole worked great except that nothing ever got sent to my local printer when INNOPAC tried to print holds notices to my local printer - instead, they flashed on my screen.  I only tried using Wine when I couldn't get it to work in Konsole and could not find another native Telnet client for Linux (PuTTY didn't work, either).

---

### Post by slushy77 on 2006-04-26
what about the print-to-file option in konsole's print screen menu. If that works you could use that instead, printing out the pdf later.

---

### Post by RavenOfOdin on 2006-04-26
You just gave me a great idea. 

Thanks. :)

---

### Post by Video Toaster on 2006-04-26
[QUOTE=slushy77]what about the print-to-file option in konsole's print screen menu. If that works you could use that instead, printing out the pdf later.[/QUOTE]
I think you're talking about printing an image of the text on the Konsole screen.  That feature works fine on my computer, but it doesn't meet my needs for INNOPAC.  I need to actually have the Telnet client be able to send print jobs to the printer BY ITSELF.  INNOPAC uses special printer control codes to do this.  Konsole seems to be ignoring these and rapidly flashing my print jobs on the screen.  I can't even manually print them, as the flash by too quicky (INNOPAC is usually trying to print 40 pages or more).  As I said, the old version NetTerm on Windows used to handle this wonderfully.

---

### Post by cmnorton on 2007-12-10
> **Video Toaster said:**
> After logging on to my local library's INNOPAC server using the telnet command, I found that I could not print forms directly to my local printer as I could using NetTerm on Windows.  After doing some research, I found that INNOPAC uses VT102 printer control codes to handle printing to the local printer.  Are there any Linux telnet clients that can handle that?  (I already tried running NetTerm via Wine, but it froze soon after logon :D)

I use Ericom's PowerTerm Interconnect for Linux. I could not get the mapping out of any of the open source emulators I tried. Our application makes full use of mapped function and control keys.

---

