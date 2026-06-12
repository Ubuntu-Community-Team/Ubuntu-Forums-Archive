---
title: "gnome-power-manager ignores suspend button"
date: 2007-07-15
forum: Desktop Environments
---

### Post by niemand on 2007-07-15
When I hit the suspend button, I get the following message:

gnome-power-manager: (niemand) Doing nothing because the suspend button has been pressed

I have run gnome-power-preferences and cannot find any pull downs, tabs, switches or anything else related to handling the pushing of the suspend button.

Would someone please tell me how I can map my suspend button to hibernate my machine? I know suspend works because I have been testing it with gnome-power-cmd.sh. I will test hibernate when I get the chance, but I would really like to be able to hibernate at the push of a button or two. So, the problem is not hardware but rather with my lack of understand of the gnome desktop environment (hence this group instead of hardware).

I have googled and searched these forums for an answer with no success.

Any and all help is appreciated.

PS:
MSI 171772 laptop with AMD64x2 Turion TL-60
Everything (sound, video, acpi, firewire, usb, etc.) works with Feisty Fawn. :)

---

### Post by glennric on 2008-02-05
> **niemand said:**
> When I hit the suspend button, I get the following message:

gnome-power-manager: (niemand) Doing nothing because the suspend button has been pressed

I have run gnome-power-preferences and cannot find any pull downs, tabs, switches or anything else related to handling the pushing of the suspend button.

Would someone please tell me how I can map my suspend button to hibernate my machine? I know suspend works because I have been testing it with gnome-power-cmd.sh. I will test hibernate when I get the chance, but I would really like to be able to hibernate at the push of a button or two. So, the problem is not hardware but rather with my lack of understand of the gnome desktop environment (hence this group instead of hardware).

I have googled and searched these forums for an answer with no success.

Any and all help is appreciated.

PS:
MSI 171772 laptop with AMD64x2 Turion TL-60
Everything (sound, video, acpi, firewire, usb, etc.) works with Feisty Fawn. :)

Did you ever figure this out?  I was having this problem and unset some gconf keys that were causing a conflict and this fixed the problem.  Let me know if you want more details.

---

### Post by niemand on 2008-02-05
No I have not. I have moved onto Gutsy and will be moving to Hardy soon. Gutsy behaves much better with respect to power management. I figure Hardy will be even better solving my problem.

Thanks for you offering though.

---

### Post by glennric on 2008-02-06
> **niemand said:**
> No I have not. I have moved onto Gutsy and will be moving to Hardy soon. Gutsy behaves much better with respect to power management. I figure Hardy will be even better solving my problem.

Thanks for you offering though.

Try this and see if this solves the problem.

Open the "Configuration Editor" by typing gconf-editor in the terminal.  Go to /apps/gnome-power-manager and unset all of the keys that show up to the right while that key is selected.  One of those keys should be something about the suspend button.  That is really the one that needs to be unset, but as far as I can tell those are all deprecated keys.  Then go to "Power Management" in System->Preferences, and look under the General tab.  Make sure that Suspend is selected for the action of "When the suspend button is pressed:"

That fixed the problem for me.

Edit: Looking at your first post I see that you want to Hibernate instead of Suspend, so select that instead for the action.

---

### Post by niemand on 2008-02-06
I guess I forgot to mention that I  am running enlightenment and not gnome. I still use some of gnomes tools like gnome-power-manager, but I do not have all of the pull down menus and stuff.

Anyway, I ran gnome-power-preferences and all of the old pull down for what to do when what buttons are pushed were there again. Shows how much I use the power facilities on my laptop I guess. Anyway, I configured it the way I wanted but have not fully tested it. I will get to that someday, but I bet that I upgrade to Hardy Heron before I get around to testing it.

Again, thanks for the help and it is good to complete these items for all of the other people that may have related problems that do search the forums.

---

