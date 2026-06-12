---
title: "Open/Save Dialogs"
date: 2009-03-24
forum: General Help
---

### Post by paulslocum on 2009-03-24
Maybe an odd question: Do Ubuntu and other linux distributions have a common open/save dialog?  In other words, does the operating system provide some of this capability of the open/save dialog (like in Windows) so the interface is consistent in all software?  Is it possible to install add-ons to the OS that enhance the open/save dialogs in all programs?

I have not used Ubuntu or other Linux distributions that include a GUI -- I've only used Linux in a command line environment.

---

### Post by Anthon on 2009-03-24
There is communality of programs based on the same GUI 'library' (Gnome, KDE etc), but as with Windows, as a programmer you don't have to use them. 
You will see some more variation on these themes as well because of devlopers being able to tweak the standard as they have access to the source code. To do that under windows just requires more effort. THat is why it is done less and does there seem to be a standard.
These specialised open/save dialogs are often more easy to use than generic ones.

---

### Post by paulslocum on 2009-03-24
So it is different in that you can't just make an API call to some Ubuntu function to call up an open/save dialog -- if you want an open/save dialog that looks the same, you have to find the same GUI library and build your own binary of that open/save dialog into your application?

(sorry if this is poorly worded or has errors, I rarely write any GUI-based software)

---

### Post by Anthon on 2009-03-25
I am more of a commandlien guy myself, so don't worry about the wording ;-)
Ubuntu comes with most GUI based software based on Gnome whereas Kubuntu and e.g. SuSE are KDE based. Those are based again on GTK resp. Qt graphics libraries and both of those work on top of the X Windowing System ("X").
X doesn't have widgets like a save/open dialog, it is more of a 2D API. However on a higher level ( GTK, Qt ) you should be able to have such a 'standard' dialog.
That doesn't stop people from writing their own, but they don't have to.

And because of X underlying most of the applications, you can run KDE apps on Ubuntu and Gnome apps on Kubuntu. The frst time you do so you might notice that a few extra libraries get installed, those include the common code include the open/save dialog (which an application writer might still go around).

---

