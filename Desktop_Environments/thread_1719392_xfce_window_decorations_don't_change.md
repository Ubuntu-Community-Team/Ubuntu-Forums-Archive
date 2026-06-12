---
title: "xfce window decorations don't change"
date: 2011-04-01
forum: Desktop Environments
---

### Post by Akovia on 2011-04-01
Not sure what happened but now when I try to change a theme under Settings > Appearence, most of the themes that are available in /usr/share/themes & ~.themes are not seen. It seems like only themes that don't decorate the windows are available. 

Not sure how to troubleshoot this, I wasn't able to find a similar problem in my searching.

Ako

Xfce 4 Desktop Environment
version 4.6.1 (Xfce 4.6)

Xubuntu 10.04 (Lucid) 2.6.32-30-generic SMP i686 GNU/Linux

Gnome 2.30.02

---

### Post by 3Miro on 2011-04-01
Appearance consists of two settings: GTK theme and Windows Decorations. GTK themes are common for all applications and desktop environments running GTK (Gnome, XFCE, LXDE and all the apps). Decorations are handled by the different windows managers (Metacity, XFWM4, OpenBox ... )

To change the window decoration for XFCE, you need to go to XFCE setting manager (it is called Setting Manager and it will probably be in System -> Prefs under Gnome and Settings under XFCE). From there you can select Window Manager and then change the decoration style. You can select only from a list of XFCE decorations. You can download more from either the Software Center or

[http://xfce-look.org/](http://xfce-look.org/)

---

### Post by Akovia on 2011-04-02
Guh!
I didn't think to look under the window manager, Now that I found it I realize that the interface to pick the themes under the Window Manager looks awfully similar to the theme chooser under the Appearance tab. I feel like such a newb, but I must say that the documentation on xfce's site isn't very clear, and to select themes from two totally separate categories from the main settings interface is far from intuitive.

I can't thank you enough for the swift reply with a clear solution. I went for help with another more serious problem to xfce's forums a few days ago and never got a reply. It's refreshing to not be ignored.

Cheers,
Ako

---

### Post by 3Miro on 2011-04-02
In Gnome appearance you also get different settings for the decorations and GTK if you select "customize" button. Some of the Gnome themes also come with GTK or Metacity part only and hence they change only one part of the appearance. It can be confusing both ways, but you should be fine if you keep in mind that decoration the window content are different.

In XFCE you do miss some of the drag-drop -> install features of Gnome, however, IMO this is a small price to pay for the added speed.

Many people here use Xubuntu or XFCE in general, so you should have no trouble getting response to your questions.

If you have no more questions about this one, please mark the thread as "solved".

---

### Post by Akovia on 2011-04-02
God I love this place, you may have just solved another problem I have been working on for hours. I am using XnView-MP and am not able to Drag & Drop from the thumbnail Pane to the Folder Pane. Again...I went to the source to ask for help last night and just posted again before checking back here. Again I get no replies, but now I find that Drag & Drop in not implemented in xfce. Are you psychic?

I will search on what overhead to expect to install the gnome libraries, but would love to hear your thoughts on any other work-arounds or pertinent info if you feel up to it. I'm happy to start a new thread as well if it's more appropriate.

Thanks again for everything!
Ako

---

