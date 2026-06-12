---
title: "Help with xe-x64 emulator"
date: 2009-01-29
forum: Gaming &amp; Leisure
---

### Post by ProcyonSJJ on 2009-01-29
Hello.  I'm a bit new to linux, and I would truly like to be able to use XE emulator, but I'm having a little bit of trouble.  I am running Ubuntu Intrepid amd64, and I downloaded the amd64 install of XE.  I was able to make it just fine, and I installed it in my home directory.  But there are problems when I try to run it.

If I don't run it with sudo, I get the following warning:

Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkMessageDialog::use-separator' of type `gboolean' from rc file value "((GString*) 0x140aec0)" of type `GString'

Whether I run it with sudo or not, I get the "Operation not permitted" warning three times before the GUI pops up.  Then I choose a ROM, doesn't matter for what system, say NES or Genesis, I get one more "Operation not permitted" warning before the ROM begins to execute.  Only, I have no sound and no framerate control.  It runs as fast a possible.  I have the latest ALSA libraries installed, and I didn't get a sound warnings when I compiled, so I'm not sure what the problem is.

I've tried contacting the author of the emulator twice, but have gotten no response.  Any help that you could provide me would be greatly appreciated.  If there's any further information that you need from me, let me know.  Thanks very much!

Procyon

---

### Post by Grishka on 2009-01-30
I've had problems with this one as well. perhaps you'd want to try mednafen instead.

---

### Post by ProcyonSJJ on 2009-01-30
Hi Grishka, thanks, I also have Mednafen installed.  I am using it along with the front-end Gelide.  I was interested in Xe because of its built in GUI.

If nobody can assist me directly, can they point me to any location where I might be able to receive some helps?  (Other than the emu's author who, as I said, I have tried to email, but have thus far gotten no response.)  Thank you.

Procyon

---

### Post by ProcyonSJJ on 2009-02-02
I'm still having trouble with this one... I even tried to build the 32-bit version with no success.  Has anyone ever built the 64-bit version of this emulator and had it work correctly?  That is, it had sound and the frame rate was correct?  Thanks.

---

