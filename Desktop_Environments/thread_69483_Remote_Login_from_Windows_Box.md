---
title: "Remote Login from Windows Box"
date: 2005-09-27
forum: Desktop Environments
---

### Post by TheOrangeRider on 2005-09-27
Hi there,

I'm trying to find out how to configure kubuntu to allow me to use my Windows box to get remote access via Cygwin X. I found some info about enabling xdm and gdm for the Gnome desktop (I think it's in the HOWTO section), but I haven't yet found anything about how to do it with KDE. I actually can't even find where my xdm config files are. Can anyone help me out?

Thanks!

---

### Post by ltmon on 2005-09-27
I can't really help you out with this problem as I've never tried it, but I can suggest another solution.  

I've been using FreeNX for a little while to remote login to my Kubuntu box.  It took less than an hour to set up from not knowing what FreeNX was to having it running.  It's also much faster than just X forwarding (a-la Cygwin-X), and can be comfortably used over a slowish DSL line.

There's plenty of information for setting up FreeNX in Google, and some tutorials on these forums.

[http://ubuntuforums.org/showthread.php?t=1968](http://ubuntuforums.org/showthread.php?t=1968) was a help, and freenx is now in the Ubuntu repositories, so you don't have to get it from Kannotix.

L.

---

### Post by lithorus on 2005-09-27
What are you excactly trying to achieve? Perhaps remote desktop through vnc(vino) would work better?

---

### Post by TheOrangeRider on 2005-09-27
[QUOTE=lithorus]What are you excactly trying to achieve? Perhaps remote desktop through vnc(vino) would work better?[/QUOTE]

I haven't really done much with VNC so correct me if I'm wrong, but I'm under the impression that VNC doesn't enable having a login screen so that multiple users can login to my kubuntu box at once, unless you do VNC over an xdm setup like I think they described in the HOWTO for gdm. A coworker of mine set up his xdm server on his Suse so that both him and I and anyone else can login to his box, and I've always been envious.

Maybe I'll try looking into this FreeNX thing and see if it get me my desired functionality. Or maybe someone can point out my ignorance of VNC? ;)

Thanks for the suggestions so far!

---

### Post by lithorus on 2005-09-27
[QUOTE=TheOrangeRider]I haven't really done much with VNC so correct me if I'm wrong, but I'm under the impression that VNC doesn't enable having a login screen so that multiple users can login to my kubuntu box at once, unless you do VNC over an xdm setup like I think they described in the HOWTO for gdm. A coworker of mine set up his xdm server on his Suse so that both him and I and anyone else can login to his box, and I've always been envious.

Maybe I'll try looking into this FreeNX thing and see if it get me my desired functionality. Or maybe someone can point out my ignorance of VNC? ;)

Thanks for the suggestions so far![/QUOTE]
That is correct about VNC. It was just that if you only meant to remotely control it, using Cygwin X would be a little overboard :) But FreeNX would infact be quite a good choice. I beleive it's even in the Breezy repository.
EDIT:
[https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX)

---

### Post by TheOrangeRider on 2005-09-27
Thanks for the info! I actually just figured out how to get kdm set up properly to use with X (that kde help center is pretty useful), but it does seem a little slow so maybe i'll go with FreeNX anyway. But for all those who wish to set it up the way I currently have it...

[LIST=1]
[*]Edit your kdmrc file (probably in /etc/kde3/) and go to the xdmcp section
[*]Change Enable=false to true
[*]Edit your Xaccess file (same dir) to allow your windows host to remotely connect
[/LIST]

Thanks again!

EDIT: For some reason it won't let my Windows box connect if I'm also VPN'd into another network. Just FYI.

---

### Post by YorYor on 2005-09-27
The only downside with the VNC over GDM method is that it does not persist over session; every time you log in it's a new session, and is not sync'ed to the actual desktop (:0) which the machine believes to be its primary output. The very same HOWTO ([http://www.ubuntuforums.org/showthread.php?t=42941](http://www.ubuntuforums.org/showthread.php?t=42941)) will work flawlessly with KDM+KDE...

All the best!

---

