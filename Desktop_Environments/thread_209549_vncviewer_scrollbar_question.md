---
title: "vncviewer scrollbar question"
date: 2006-07-05
forum: Desktop Environments
---

### Post by GeneW on 2006-07-05
Is there anyway to force a vncviewer client to not use scrollbars?  I'm connecting to a vncserver running on another linux box (FC4) and that server is sized to be exactly the size of my laptop screen.  This should work but the vncviewer always opens just a little smaller than the virtual screen and has scroll bars.  I've even tried experimenting with creating much smaller servers to connect to (like 1000x600) but the viewer always opens up slightly smaller than the server window size and can't be expanded.

---

### Post by scxtt on 2006-07-05
if you want to start a vncserver w/ a specific size, use:
[indent]vncserver -geometry 1000x600 -depth 24[/indent]well, assuming you're using "vncserver" on the FC4 box ...

---

### Post by GeneW on 2006-07-05
[QUOTE=scxtt]if you want to start a vncserver w/ a specific size, use:
[indent]vncserver -geometry 1000x600 -depth 24[/indent]well, assuming you're using "vncserver" on the FC4 box ...[/QUOTE]

Yes, I've used that to create vncservers on the FC4 box that are much smaller than my screen but the client on Ubunu always opens smaller than the server size, no matter how small.

---

### Post by scxtt on 2006-07-05
how strange, never had that problem myself ... looking at the man page for vncviewer, you can also pass the -geometry flag, so what happens if you use:
[indent]vncviewer -geometry 1000x600 "host":"screen"[/indent]

---

### Post by flabdablet on 2007-03-13
I've also got a niggling problem with vncviewer and scroll bars.  I'm using vncviewer to connect to a remote UltraVNC server on a Windows box with two screens: the left one is 1024*768, and the right one is 800*600.  This means that the remote desktop is (1024+800)*768, which is too wide to fit on my local 1600*1200 laptop display; so obviously I need a horizontal scrollbar.

However, I've not been able to find a way to make the vncviewer window high enough to include that scrollbar *and* the full height of the remote desktop, even though I have plenty of screen height for it to do that in.  ```
vncviewer -geometry 1200x1000 remote.server.name
```
results in the same window as
```
vncviewer -geometry 1200x768 remote.server.name
```
It seems that the height I specify is ignored, and that the window height is always set according to the height of the remote desktop.

Which would be fine except that the horizontal scrollbar gets wedged *inside* this height, rather than being tacked on below it, and this in turn makes a vertical scrollbar necessary as well.  I would much prefer to see the full height of the remote desktop all at once.  Does anybody know a way to force vncviewer to actually *use* a locally specified window height?

---

### Post by flabdablet on 2007-03-13
Updating to xvnc4viewer doesn't help, even though that version gives me a dynamically resizable local window.  It seems that the maximum local height and width are limited to the actual remote height and width, and that no allowance is made for the thickness of any necessary scroll bars.

I wish I could find the source code.

---

### Post by win2456 on 2007-12-25
sorry to re-open this issue... I have ubuntu 7.10 installed and having the same issue with xvnc4viewer.  I VNC into an XP machine with RealVNC (personal edition) installed.  Rescaling does not work.  I have tried everything from re-installing drivers, adding the line "virtual 1280    1280" into my xorg.conf, etc.
my dad's running xubuntu on his laptop (non-widescreen).  when i use xvnc4viewer to connect the same XP machine, it resizes automatically fits it on the monitor perfectly!  So, I decided to install Xubuntu on my laptop.  i first installed xubuntu-desktop on existing installation but still had the same problem with vnc so i formatted and re-installed Xubuntu... all that trouble and no luck!

can someone please help!!??  my laptop resolution is 1280x800, connecting to XP (higher res).  i am new to ubuntu (with very minimal experience on other distros).  And yes, I don't want to use terminal client at the moment.

Thanks in advance for all the help folks! :)

---

### Post by win2456 on 2007-12-25
i just installed ultravnc server on the XP machine... scaling still doesn't work from my laptop.  it's only my laptop it's giving trouble... this has anything to do with the settings in the xorg.conf?

---

### Post by win2456 on 2007-12-31
any ideas about this? :confused:

---

### Post by win2456 on 2008-01-04
bump

---

### Post by win2456 on 2008-01-20
someone help please... if there's a solution out there, share it... thanks!

---

