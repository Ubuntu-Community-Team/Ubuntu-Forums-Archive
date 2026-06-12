---
title: "GTK theme not held when tunneling over SSH"
date: 2008-08-06
forum: Desktop Environments
---

### Post by harrypotter2k5 on 2008-08-06
Hey All,

I currently run Ubuntu 8.04 in a VM on my macbook, and have been using SSH to tunnel x11 output of the VM onto a native X11 client on Mac OS X. 
In ubuntu I have set the theme to "crux", the theme in which all gtk windows render if i'm in my vm, however, through SSH on my Mac the GTK theme switches back to the nasty default "redmond" theme.

I've tried running gtk apps from another computer at my university, and their themes are applied over ssh.

Can anybody tell me how to change this? I've tried compiling and running gnome-settings-daemon on my mac, but this does not seem to help.

---

### Post by RC Howe on 2009-08-23
Try running gnome-appearance-properties over the ssh connection. Worked for me.

---

### Post by npmeyer on 2009-09-25
This fixed the problem for me too, but only for the current session.  If I log out and log back in again, I once again don't get any GTK themes on tunneled apps.

It'd be interesting to know what running gnome-appearance-properties does to fix this -- perhaps that info would point to a more permanent fix.

---

### Post by ergosteur on 2011-02-19
> **RC Howe said:**
> Try running gnome-appearance-properties over the ssh connection. Worked for me.
Sorry for reviving an old thread, but I can't figure this out, and can't run gnome-appearance-properties since my remote server doesn't have gnome installed.

Strangely, when I use X over ssh from my mac, the Clearlooks theme is applied to all windows, but when attempting to do the same from any Ubuntu machine I get ugly unthemed gtk2 controls.

---

### Post by deconstrained on 2011-02-19
Why has nobody recommended remote desktop (VNC), or for the security-conscious, VNC tunneled over ssh? You can just use ChickenOfTheVNC on the Mac end. The connection/interface will be faster than straight X-tunnelling over SSH, because the interface is a virtual framebuffer device instead of the full mechanics (which I think is why it doesn't get the GTK theme in the first place). It's also more secure than X-tunnelling.

I first learned VNC tunnelling through SSH from here:
[http://www.nas.nasa.gov/Users/Documentation/vnc.html](http://www.nas.nasa.gov/Users/Documentation/vnc.html)
To get this on your Ubuntu machine the package you want is vnc4server.

You basically SSH into your Ubuntu box, start up vncserver (while ssh'd), forward the port by hitting [Enter] [~C] (which allows you to issue commmands to the SSH client itself) and then "-L 590[n]:localhost:590[n]", where [n] is the number printed in the message vncserver gives you:
"New '[hostname]:[n] ([username])' desktop is [hostname]:[n]"
Then you can set up and configure your VNC server sessions in ~/.vnc/xstartup to your heart's content. If you want gnome you can just replace x-window-manager with gnome-session at the end of the file.

---

