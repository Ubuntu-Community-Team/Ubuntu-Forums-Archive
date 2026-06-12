---
title: "Setting up a Quake 3 server w/ no UI drivers"
date: 2005-11-24
forum: Gaming &amp; Leisure
---

### Post by _cashel on 2005-11-24
Can this be done? I have a machine w/ the Ubuntu server install that I'm using as a dedicated server for my lans. I don't have any sort of UI drivers installed and I'm not planning on playing any games on the machine. I do all of my work via SSH. Is there some sort of way I can bypass the UI driver check at the beginning of the Quake 3 install?

---

### Post by cdsboy on 2005-11-24
why is it so important that you donnot have the UI drivers?

---

### Post by _cashel on 2005-11-24
Well it's not, I just didn't want to have to go through the trouble of doing it. Now I am having some issues with it though. I went ahead and followed the instructions on Ubuntuguide for the Nvidia drivers, but I'm still getting the same UI error when installing Q3. What other X11 dependencies would I need to install besides the four required by the nvidia driver installation?

---

### Post by crane on 2005-11-26
You should be able to run the linux installer without x11 as well.But if you have it installed on another system just copy it over. You do not need x11 to run q3 as a server. 
[Check this out]("http://www.planetquake.com/weaponsfactory/quake3/server-docs/WFA-Linux-Server-Docs.html")

I would suggest running the server as a user as well.

---

