---
title: "dynamic resolution in remote desktop"
date: 2008-04-17
forum: Desktop Environments
---

### Post by dlstyley on 2008-04-17
Using Remote Desktop in Windows, I can do the following:

Start working on my "server" at 1280x1024.  Go downstairs and resume my session from my laptop and see my same desktop, but now it is displayed at 1200x800 (with all the windows resized appropriately).  I can then disconnect, go back to my "server" and resume the same session and be back at 1280x1024.

With the server running Ubuntu, I can connect remotely just fine, however I'm always stuck with the resolution that the server is running.  I've found some VNC clients that support "screen scaling", but that just makes things hard to read.  I've also seen suggestions about connecting to a new session at a different resolution, but that seems pointless (one of the biggest benefits to remote desktop solutions is resumable sessions.)

Is it possible to get the same dynamic screen resolution that RDC gives me using an Ubuntu server?  If so, please tell me what I'm missing.

Thanks

---

### Post by MrFSL on 2008-04-18
Try NoMachine.  ([http://www.nomachine.com/](http://www.nomachine.com/))

It's free, and this is one of the reasons I use it.

---

### Post by dlstyley on 2008-04-21
I've tried the nomachine client, but all I could get was "screen scaling".  This is doesn't work very well for me as I can barely read text on the screen (it's badly distorted).  

Am I doing something wrong?

---

### Post by dlstyley on 2008-04-21
Just found this.  Looks like I'm not the only one:

[http://www.opensourcetutor.com/2007/06/21/nomachine-nx-desktop-sharing-shadowing-now-available/]("http://www.opensourcetutor.com/2007/06/21/nomachine-nx-desktop-sharing-shadowing-now-available/")

---

### Post by isbent on 2008-06-11
I just had this problem also using Tight VNC from a windows box to the stock gnome remote client vino. 

The xserver needs to be configured to include virtual resolutions, which surpass the machines hardware capabilities.


the easy way:

first, in your VNC session from Applications -> Accessories open a terminal,

sudo gedit /etc/X11/xorg.conf

which will open xorg.conf in a text editor

I added the display subsection inside the screen section, as the stock install left the display subsection out.

Section "Screen"
      Identifier "Default Screen"
      Monitor "Configured Monitor"
      Device "Configured Video Device"
   SubSection "Display"
      Depth 24
      Virtual 1024 768
      Virtual 1280 1024
      Virtual 1400 1050
   EndSubSection
EndSection

keep in mind this box has no monitor so its lacking all the normal modes in the example above. Note the lack of an x separating the values, distinguishing virtual resolutions.

After this you'll have to restart xserver (which kills your VNC session and logs you out of the gnome session, which you'll have to log back into to use vino) or reboot. On your next remote session the new virtual resolutions should be available on the Screen Resolution menu under preferences.

---

