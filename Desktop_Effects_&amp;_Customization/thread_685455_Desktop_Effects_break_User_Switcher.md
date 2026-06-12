---
title: "Desktop Effects break User Switcher"
date: 2008-02-02
forum: Desktop Effects &amp; Customization
---

### Post by rkillcrazy on 2008-02-02
I've been going back and forth with this over the past few months.  I suppose I was hoping an update would fix it.  Hey, it costs nothing to dream! ;)

Nonetheless, whenever I enable **Desktop Effects**, all works fine until I go to switch users.  If I use the **User Switcher** on the panel (Ubuntu's default install's location for it) I get a white/blank screen.  Luckily I've figured out that it's the password promt so I just start typing the password and hope for the best.  I get the white/blank screen when I use the **User Switcher** on the panel or if I log off completely.  I think I've narrowed it down to it only happening if the other user, who you are trying to switch to, is currently logged on.  Meaning - if that other user isn't logged on, the password screen shows up fine (more often than not).

In case someone neded to know...  I'm using an **ASUS EN7600GS SILENT/HTD/256M** PCI Express card.  The card uses an SLI-ready nVidia GeForce chipset.

If anyone can shed some light on this, it would be great.

02-02-08
0854 EST

---

### Post by dirtsurfer on 2008-02-02
I, too, have this issue. In my case it seems to be a much more sever lockup (I can't switch to VT#1 via ctrl+alt+1 and ctrl+alt+baksp does nothing). I also assumed that there was a password prompt there that I could not see, but the system does not respond to any keystroke since my keyboard has gone down with the ship (Caps lock does not even toggle).

I also have a similar GPU, so that might have something to do with it. It is an ASUS EAH3850 (Radeon HD 3850 series).

I have checked the web and forums and a lot of users are having similar troubles. I have not yet found a thread with a fix or workaround.

If anyone can point us to such a workaround, it would be much appreciated.

---

### Post by PoopyTheJ on 2008-04-30
Same thing here with Radeon 3850HD. My wife and son both use this PC and it would be really nice not to have to constantly restart my 51Gb Doctor who download continuously, like some other OS I know of.

---

### Post by emptybox on 2008-05-01
I had this problem in Gutsy, and I'm **still** having this problem with a clean install of Hardy. In fact if anything it's worse, because I used to be able to right click the user switcher to change log-in options, but now nothing comes up. Well the menu comes up, but it doesn't bring up the dialogue.
I have to use the one in Administration (or Preferences?), instead.

I've got an nVidia 7600GT using the restricted driver, so I think the problem is with compiz. I've got another older PC using an ATI card, but the user switcher works fine on that under compiz?

If you are faced with the white screen, take the cursor near the middle until it changes to a line and left click. You should then be able to enter the password OK.

---

