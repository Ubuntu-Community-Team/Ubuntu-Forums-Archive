---
title: "org.xfce.SessionManager was not provided by any .service files"
date: 2012-07-11
forum: Desktop Environments
---

### Post by thaitang on 2012-07-11
I recently decided to install both lubuntu and xubuntu on my two aging laptops. I first installed lubuntu and then added xfce4 desktop (for my PC I generally do ubuntu and then xfce4 desktop, no issues).

Initially I could not shutdown my desktop using desktop buttons and I get the error:

"the name org.xfce.SessionManager was not provided by any .service files"

Shutdown via CLI is alright though, but then no session app status gets saved that way. Plus.
 Now when I log in the window manager seems to be all wonky with no titlebar and the windows underneath the xfce4 upper panel and no way to move, minimize them, just close using keyboard shortcuts (ALT+grab is not working).

Logging into lubuntu is ok except I have the same error from trying to shutdown with desktop buttons as listed above.  I also have xfce4 panels installed replacing the lxpanels since half of the applets like sensors and batt monitor seem hooped  and I like xfce4 panel applets anyway.

From within lubuntu this is the cintents of .xsession.errors file:
```
(polkit-gnome-authentication-agent-1:1656): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(polkit-gnome-authentication-agent-1:1656): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(xfce4-panel:1657): GLib-WARNING **: (/build/buildd/glib2.0-2.32.3/./glib/gerror.c:390):g_error_new_valist: runtime check failed: (domain != 0)
xfce4-panel: Failed to connect to session manager: Failed to connect to the session manager: SESSION_MANAGER environment variable not defined
** Message: applet now removed from the notification area

(nm-applet:1681): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
** Message: using fallback from indicator to GtkStatusIcon
** Message: applet now embedded in the notification area
Initialization file /usr/share/festival/init.scm not found

(xfce4-panel:1657): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

(xfce4-xkb-plugin:1738): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

(xfce4-xkb-plugin:1738): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

(xfce4-panel:1657): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

(xfce4-panel:1657): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

(xfce4-xkb-plugin:1738): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

(xfce4-panel:1657): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

(xfce4-xkb-plugin:1738): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

(xfce4-xkb-plugin:1738): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

(xfce4-panel:1657): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

(xfce4-xkb-plugin:1738): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

(xfce4-panel:1657): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

(xfce4-panel:1657): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

(xfce4-xkb-plugin:1738): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

(xfce4-panel:1657): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

(xfce4-xkb-plugin:1738): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

(xfce4-xkb-plugin:1738): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

(xfce4-panel:1657): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

```any ideas would be appreciated.
BTW, I don't think it should be an issue but I have nautilus and gedit installed (first time not installing complete ubuntu desktop) b/c somtimes nothing beats tabbed file browsing and I am addicted to gedit external tools and snippets that I cannot seem to find anything comparable in any other text editors (yeah kate has/does similar but gawd is there any end to configuring that beast?); but gedit crashes so frequently (different issue I wonder?) it is almost unusable--everytime I close a tab in gedit the wntire app closes down (suxorz if ya don't remember to save all tabs before closing one)

thanx,
tt

---

### Post by thaitang on 2012-08-03
Wow, it's really difficult to believe I am the only one who has experienced this problem on three laptops. Solution was to reinstall xubu 86'ing lubuntu altogether.
 
Like I said I use 3 different laptops and since reverting back no issues. And on desktop I just stayed with same old xubu/ubu desktop setup and that has never given me any probs.

Real shame about lubu though b/c one of my laptops is ancient and I am thinking I will need to just run CLI on that now.

---

