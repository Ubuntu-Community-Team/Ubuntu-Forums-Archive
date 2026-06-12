---
title: "Displaymanager, Window manager, X, etc."
date: 2010-06-04
forum: Desktop Environments
---

### Post by b0wter on 2010-06-04
Hey,
I'm trying to understand how the Ubuntu GUI works. There is the X-Server and then there is stuff like compiz, GDM, KDM, metacity, sawfish, theme engines and so on. I just dont see how these parts all play together and what they all do. Can somebody point me to a web site that explains some of that or maybe just give me some hints?

---

### Post by Boondoklife on 2010-06-04
Ok here is a quick rundown of how they sit from lowest level up.

MetaCity/Compiz - Window Manager/Decorations
Gnome/KDE/sawfish - Desktop GUI
GDM/KDM - Login Managers
X - GUI Core

X is the actual service that facilitates a GUI
GDM is the actual login manager this gets you into your desktop
Gnome is your desktop
Metacity/Compiz are window managers that provides effects and the prettyness of the actual windows and interface

Each piece plays a part in your GUI experience. I know this is not too indepth but just google each to get a better understanding.

---

### Post by b0wter on 2010-06-04
I still dont get why you would need a login manager? Is that to separate all the system processes from the user processes?

---

### Post by Boondoklife on 2010-06-04
> **b0wter said:**
> I still dont get why you would need a login manager? Is that to separate all the system processes from the user processes?

How about to login? You have to authenticate yourself to the system so it knows who you are and what files are yours (think desktop, settings, etc).

---

### Post by b0wter on 2010-06-04
Oh, that's not what I meant. I was just wondering why not use GNOME to show a login screen? Or is GDM utilizing GNOME?

From what I have experienced GDM seems to have different settings than GNOME (when using an external monitor (1920*1200 resolution) on my laptop (1440*900 resolution the login screen runs at the laptops resolution and switches to my monitors resolution after logging in)

---

### Post by Boondoklife on 2010-06-04
> **b0wter said:**
> Oh, that's not what I meant. I was just wondering why not use GNOME to show a login screen? Or is GDM utilizing GNOME?

From what I have experienced GDM seems to have different settings than GNOME (when using an external monitor (1920*1200 resolution) on my laptop (1440*900 resolution the login screen runs at the laptops resolution and switches to my monitors resolution after logging in)

The reason it switches is the resolution of your session and the GDM session are stored separately, I believe this can be configured but never cared to do so myself.

The reason Gnome itself doesn't show a login screen is you may not want to load gnome, you can use GDM to load other sessions than Gnome (such as a failsafe to trouble shoot an X/gnome issue).

---

