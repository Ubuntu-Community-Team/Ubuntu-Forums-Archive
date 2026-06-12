---
title: "bzflag not working"
date: 2006-02-25
forum: Gaming &amp; Leisure
---

### Post by Cysman on 2006-02-25
Hi all, I've read a couple of posts from folks having problems with bzflag but they all seem to have some operability to their game.  My problem is when I try and run it from the menu, it flashes on the screen for half a second and then quits altogether.  I wanted to mention it here because I haven't seen this type of problem with bzflag posted before.  Any  suggenstion?:-k

---

### Post by hentaidan on 2006-02-25
Try typing bzflag in a terminal, and seeing what (if any) messages it gives you.

---

### Post by Cysman on 2006-02-25
[QUOTE=hentaidan]Try typing bzflag in a terminal, and seeing what (if any) messages it gives you.[/QUOTE]

Hi, all it says is command not found.

---

### Post by cdsboy on 2006-02-26
then it isn't installed right. also go into the menu editor and see the command the menu is using try doing to in the terminal as root.

---

### Post by Cysman on 2006-02-27
[QUOTE=cdsboy]then it isn't installed right. also go into the menu editor and see the command the menu is using try doing to in the terminal as root.[/QUOTE]


Well, this is what I get after apt-get install bzflag and it's server.  I had removed it beforehand with Synaptic. 

kenoutten@ubuntuhome:~$ bzflag
X Error of failed request:  BadValue (integer parameter out of range for operati on)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x75
  Serial number of failed request:  122
  Current serial number in output stream:  124

You asked about the command used to open the app.  I'm not quite sure but this perhaps shows it. 

Type=Application
Encoding=UTF-8
Name=bzflag
GenericName=
Comment=
Icon=/usr/share/bzflag/bzflag-32x32.xpm
Exec=/usr/games/bzflag
Terminal=false
Categories=X-Debian-Games-Arcade

Any ideas?

---

### Post by farmer26 on 2007-05-19
I have exactly the same problem, I have only just installed and not played it yet

---

### Post by djgrant on 2007-05-21
Ditto here

---

### Post by bigpilot on 2007-08-26
I had the same problem. It's because you're trying to start BZFlag fullscreen which it won't do for some reason. However, if you start it windowed (with 'bzflag -window') it will start up in a small sized window. You can then change the window size by using the 'maximize' button on the window. You can only change the window size by changing te 'Confine mouse' setting under 'Input Settings' to 'No.'  After you've changed the window size you should for best results change the 'Confine mouse' setting under 'Input settings' to 'Yes'

---

