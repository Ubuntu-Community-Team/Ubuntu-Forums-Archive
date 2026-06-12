---
title: "GDM and XFCE problem"
date: 2010-06-13
forum: Desktop Environments
---

### Post by tinmice on 2010-06-13
Really struggling with this, please help!

I have 10.04 xubuntu on an old laptop I'm using and have had a problem since the last update I ran. I use aptitude to keep my stuff up to date and ran an update this morning as normal. After the update I used it for a while longer without problems before restarting. 

When I logged back in my window decorations preferences had been set back to default, but the panel I have at the top of the screen was still there in it's normal state. After everything had loaded though it looked like there was a GDM session running as well, with the standard gnome top and bottom panels on the screen. The XFCE panel still works fine, but the top GDM one will sometimes pop out over the top of it, as if autohide is enabled, it isn't though. 

I was somewhat confused as to how this happened so thought I would log back in again and make sure I just had an XFCE session running from the session selector. (My normal setup is to have the [auto-startx disabled]("http://tech.akom.net/archives/46-Disabling-X-server-autostart-gdm-on-Ubuntu-Karmic-9.10.html") so that you have to login in a shell and manually startx - just a preference of mine). So I undid this comment and went to login in the GUI and select my session. When I did my usual username and password would not grant me access, nor would my root password - very worrying. After making sure I had typed it properly I gave up and had to revert to a rescue shell to re-comment out the auto-startx. When I did this I could log back into the shell OK and startx manually as normal (for me).

I don't know what updates were performed, but I'm pretty sure it's the update that triggered this behaviour,the only other thing I did was install spotify. Is there a way to track a previous update in aptitude? 

Sorry this is so long-winded, but it has really baffled me and I don't even know where to begin. Help much appreciated!

---

### Post by 3Miro on 2010-06-13
When you are using XUbuntu you will get a gdm session working as well. XFCE under Ubuntu uses something from gdm (I am not sure what).

You problem is probably not gdm, but rather Gnome panel. Those are separate components. If you can see the Gnome panels than you have gnome panel working. Try killing it from the shell or from the system monitor. Than look around for what it starting it (it is probably something associated with startx, that is where I would start).

---

