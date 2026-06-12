---
title: "adding a secondary desktop environment"
date: 2023-10-20
forum: Desktop Environments
---

### Post by jaldunate on 2023-10-20
In the past I have had KDE and Gnome installed simultaneously in my Ubuntu installation. It was nice being able to switch if there was any problem with one in particular and didn't want to fix it right away.

Nowadays, I am having problems with Gnome, it gets extremely sluggish every now and then, and figuring out the reason is very difficult. The problem comes and goes. So I was thinking to install a some simple desktop environment along with Gnome (thinking XFCE or LXDE, but open to suggestions) so that I could switch to it whenever I get fed up. (btw, I have nothing against Gnome, I really like it!)

Have any of you done this? I am afraid that upon install of a second desktop environment, I might mess up the video drivers (I have nvidia in this laptop) or maybe end up with services running uselessly in Gnome, because they were intended for the other desktop, et cetera. 

Any recommendations? Warnings? Experiences?

thanks!

---

### Post by tea for one on 2023-10-20
Are you logging into Gnome with a Wayland session?

Wayland and Nvidia are not best friends at the moment.

---

### Post by jaldunate on 2023-10-23
I'm on x11

---

### Post by TheFu on 2023-10-23
The problem with a userid using different DEs is because each DE will often have different settings, but use the same names.  This doesn't happen very much with KDE/Qt vs Gnome/GTK+ but it has happened a number of times with Gnome-based DEs, of which there are many.  

The best practice is to use different user logins for each DE.  This can be a hassle if you don't really understand the underlying permissions model of Unix systems.  OTOH, if you place both userids into the same _group_ and manage your file storage in a way that allows both users/owners equal access to the others, at most, it might be an inconvenience every few weeks, but not more often than that.  After all, Unix systems were designed to allow people to work together on data.  It is somewhat of a lost art for all these 'single-user' systems, even though Unix is always a multi-user system.

LXDE and XFCE are both Gnome based, so mixing those would be slightly dangerous.  Perhaps LXQt would be a better choice?  If, if you want to be really crazy, don't bother with any DE at all. It isn't like a DE is needed.  Openbox, fvwm, and other long-time Window Managers work well like they have since the mid-1990s.  When I found LXDE to be too bloated, I returned to using fvwm and I don't have any plans to change again.

---

### Post by jaldunate on 2023-10-24
haha to this point I hadn't realized that window manager and desktop environment were two different things 
[https://www.geeksforgeeks.org/difference-between-desktop-environment-vs-window-manager-in-linux/](https://www.geeksforgeeks.org/difference-between-desktop-environment-vs-window-manager-in-linux/)

Thank you for your ideas!!

---

### Post by jrbassett on 2023-11-03
As far as desktop environments go, it depends on what you prefer. If your adding a secondary de, I recommend trying Cinnamon. It is very good and is user customizable.

---

