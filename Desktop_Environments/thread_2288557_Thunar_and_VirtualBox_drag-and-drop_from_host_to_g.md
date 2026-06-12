---
title: "Thunar and VirtualBox drag-and-drop from host to guest"
date: 2015-07-28
forum: Desktop Environments
---

### Post by graham_bartlett2 on 2015-07-28
This could be a tricky one, because there are (at least) two possible places this could be broken.

I'm running VirtualBox on Win7 host with an XUbuntu 14.04 guest.  I've been using VirtualBox from v4.2.22 through to the current v5.0.  VirtualBox used to be able to do drag-and-drop from host to guest, and as of v5.0 it should do drag-and-drop from guest to host as well.

I'm particularly concerned about drag-and-drop from the host to the guest.  For all this time, drag-and-drop from the host to the XUbuntu guest desktop has worked fine.  Drag-and-drop into some other applications also works (it's fine for Geany, for instance).  But dragging from the host to the guest, Thunar windows are shown with a "no entry" sign as not being drag-and-drop targets.  This suggests to me that Thunar is doing something different to the rest of Gnome with its drag-and-drop, or perhaps that there's some hook which it's not listening for.  Or perhaps it's relying on some implicit Linux sequence of events which doesn't happen the same way under a VM.

Of course, it could be that VirtualBox is not doing things in a standard way.  But it's curious that drag-and-drop to the desktop and to some other apps works, just not into Thunar, and that does make me suspect it's a Thunar problem.

Has anyone else experienced this, or have any feedback or ideas to try?

---

### Post by broadcast23 on 2015-07-29
I just tried Virtual Box 5.0 on windows 10 host...terrible!  No visualization, No ability to drag and drop, No copy and paste, couldn't share any files with host.  I hope they get those bugs fixed.  Oh and tried to install guest extensions to no avail I then tried it in 14.04 L.T.S. which has virtual box 4.3.10, everything worked like a charm. so you may want to back up a version or so.  Even says in the Virtual Box community form that visualization is a no go in Virtual Box 5.0

---

