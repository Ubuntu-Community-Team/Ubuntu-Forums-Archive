---
title: "LXDE: &quot;Main Menu&quot; visibility settings not matching reality."
date: 2010-12-18
forum: Desktop Environments
---

### Post by spamhog on 2010-12-18
10.04 with LXDE via Synaptic (not actually Lubuntu).

I just noticed that in the dialog LDXE Main Menu / Preferences / Main Menu

- the LDXE Main Menu / System / Administration submenu is set as visible, but is actually HIDDEN

- the LDXE Main Menu / Applications / System Tools / Configuration Editor entry
always remains VISIBLE, no matter if set as visible or hidden.

So it seems that **[COLOR="Red"]visibility settings and actual visibility do not stay in synch[/COLOR]**. 

[B]Is there a way to resync, either way, visibility settings and actual visibility?

Or, which config file(s) may contain error?

Which errors may have caused this?[/B]

---

### Post by spamhog on 2010-12-18
Screenshot.

The "Preferences" submenu visible in the menu is the one WITHIN "Applications", and NOT the identical one nested inside "System".

Indeed, the whole "System" section is missing.

Yet, both are set as visible in the "Main Menu" dialog.

 [IMG]http://files.myopera.com/spamhog/albums/5616432/menu-shot.png[/IMG]

---

### Post by SteveDee on 2010-12-18
> **spamhog said:**
> 

...So it seems that **[COLOR="Red"]visibility settings and actual visibility do not stay in synch[/COLOR]**....
[/B]

Not quite sure what you are trying to say. I generally run LXDE session on my Ubuntu 10.10 laptop, but I can still run Gnome session if I chose during login.

My understanding is that the alacarte menu gui is only used by Gnome, and is not used by the simpler, lighter interface of LXDE...hence my info in your previous thread regarding : /etc/xdg/menus/lxde-applications.menu

---

### Post by spamhog on 2010-12-20
Thank you SteveDee!  Clarifications:


LXDE vs GNOME

> I generally run LXDE session on my Ubuntu 10.10 laptop,
> but I can still run Gnome session if I chose during login.

It means that you too added LXDE to a default Gome desktop, so we have identical setups, excellent!  I never questioned that.



WHICH GUI TOOL FOR MANAGING MENU?

> the alacarte menu gui is only used by Gnome
> and is not used by the simpler, lighter interface of LXDE...

Click on the LXDE logo. follow the LXDE menu to Preferences, click on Main Menu:  is this the GUI you use?  DOes it look like my screenshot?

Once inside the Main Menu GUI, go to Applications / Preferences / Main Menu entry, and click on Properties:  what is the command? Is it alacarte or something else?

Now try to hide / unhide the section Applications / System Tools / Configuration Editor: does it actually hide / unhide in the LXDE menu?  Does it stay always visibile like on my system?

Last, try to hide / unhide some other sections or entries: do they actually hide / unhide it in the LXDE menu as well[RIGHT][/RIGHT]?



XDG SYSTEM-WIDE SETTINGS OR UNPRIVILEGED USER-LEVEL SETTINGS?

> hence my info in your previous thread regarding :
> /etc/xdg/menus/lxde-applications.menu

Since all that filesystem branch is in lockdown and would at least require sudo to edit (try), while all of the changes above can be performed as user (try), it stands to reason that the settings that get changed are not there. Does your system behave differently? Or do you have to sudo to change /etc/xdg/menus/lxde-applications.menu while you can change evrerything as unprivileged user in LXDE Menu / Applications / Preferences / Main Menu as on my system?



I hope it's all more clear now. Thanks again for your attention!

---

### Post by SteveDee on 2010-12-20
> **spamhog said:**
> ...Does your system behave differently? Or do you have to sudo to change /etc/xdg/menus/lxde-applications.menu while you can change evrerything as unprivileged user in LXDE Menu / Applications / Preferences / Main Menu as on my system?



I'm sorry I completely missed the point earlier. Most of the time I use pure Lubuntu. It just happens that I also have a mongrel of a laptop that started out with Ubuntu and has had 'god knows what' loaded onto it. So I don't really trust this system as a reference to how things should work,

But you are absolutely right, I can pick the alacarte "Main Menu" app from the LXDE session menu.

A quick search revealed this: [http://wiki.lxde.org/en/LXDE:Questions](http://wiki.lxde.org/en/LXDE:Questions) which claims that alacarte can be used to edit LXDE menus. So I installed it to a Lubuntu system and found that the "Applications" menu contents match those available from the LXDE start button. However, disabling menu items via alacarte has no affect on LXDE menu contents in Lubuntu.

Anyway, back to mongrel 'buntu, I can add, enable, disable & delete items in the Applications section on the menu structure using alacarte. Although the System menus (Preferences & Administration) are listed in alacarte, they do not display from the LXDE start button.

So it looks like alacarte & LXDE and not completely compatible at this time.

Unfortunately I have just done your little trick and accidentally deleted the Preferences menu!

---

### Post by spamhog on 2010-12-20
Thank you!

So it looks like we reached the end of the Matrix for now! :-D

I'll keep my ears up.

---

