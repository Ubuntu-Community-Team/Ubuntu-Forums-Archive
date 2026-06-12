---
title: "Compiz and tabs?"
date: 2011-09-20
forum: Desktop Environments
---

### Post by woodyg on 2011-09-20
I left Ubuntu for Xubuntu because there no longer are any tabs for navigation between documents/applications. Using some keyboard combination to jump between documents/applications simply is a big step backwards in my opinion as overview now is completely missing and navigation now is less straight forward.

I did however recently come across someone who claimed that tabs might be achieved through Compiz somehow. It was never explained how, so I'm a bit lost at the moment. How can I do that? I can't find anything in CompizConfig Settings  Manager... I would love to be able to implement tabs in Ubuntu. How can I  achieve this?

---

### Post by Copper Bezel on 2011-09-20
Do you mean the kind of tabs used in a file manager or web browser, or do you mean the keyboard-based Alt+Tab application switching (which should be enabled by default in almost any distro)?

There's another kind of "tabbing" provided by Compiz, but it's unrelated, more to do with "grouping" windows.

---

### Post by woodyg on 2011-09-20
> **Copper Bezel said:**
> Do you mean the kind of tabs used in a file manager or web browser, or do you mean the keyboard-based Alt+Tab application switching (which should be enabled by default in almost any distro)?

There's another kind of "tabbing" provided by Compiz, but it's unrelated, more to do with "grouping" windows.

I mean the old fashioned kind of tabs (that now has appeared in web browsers), not the keyboard based switching/tabbing.

---

### Post by Copper Bezel on 2011-09-20
Do you mean the task bar The bar at the bottom that lists open windows?

If so, you can revert to that style of task switching by logging out and selecting the "Ubuntu Classic" interface at the bottom after selecting your user account and before entering your password.

---

### Post by woodyg on 2011-09-21
> **Copper Bezel said:**
> Do you mean the task bar The bar at the bottom that lists open windows?

If so, you can revert to that style of task switching by logging out and selecting the "Ubuntu Classic" interface at the bottom after selecting your user account and before entering your password.

Yes, that is what I mean. I am however under the impression that the Ubuntu classic option will disappear at some point in the future, and if that is the case then I can as well move to a different distro straight away, rather than just putting off the inevitable.

But can this "tab effect"/task bar be achieved with Compiz, or was the person who told me this misinformed?

---

### Post by Copper Bezel on 2011-09-21
Yes, I think there might have been a confusion of terms. There's nothing like Classic mode's task bar available in Compiz; it's Compiz that actually draws the Unity interface. However, the task bar panel will remain an option for the foreseeable future, as it's available (to install) in an upgraded form in Gnome 3, which ships with the next version of Ubuntu.

---

### Post by woodyg on 2011-09-24
Is there **a taskbar that works under Unity** that I can install? I have been searching but not found anything...

---

### Post by Krytarik on 2011-09-24
> **woodyg said:**
> Is there **a taskbar that works under Unity** that I can install?
Well, at least in Natty 11.04* you can run Gnome Panel concurrently to Unity. Therefore just add "gnome-panel" to your "Startup Applications". Then just remove its upper panel.

Hopefully, it will be displayed above the top panel of Unity, or if it's below, you are able to find a pixel of it, so that you can use its right-click menu to remove it. Otherwise, you would need to use "gconf-editor" for that (path: "/apps/panel").

 *It seems like it's possible in Oneiric 11.10, too; with the Gnome Fallback Session installed.

Greetings.

---

### Post by woodyg on 2011-09-24
Great! :P I just moved the top gnome-panel (which otherwise cover any close/minimise window button) down to the bottom and deleted the left one, and I have my tabs displayed just like it should be. I think I may actually move back to Ubuntu when 11.10 is out. Thanks a million! :grin:

---

### Post by woodyg on 2011-10-14
:( Well, that didn't last long. Have been trying out 11.10, and it seems the gnome-panel isn't compatible with Ubuntu 11.10. Looks like it will be XFCE for the foreseeable future for me...

---

### Post by Copper Bezel on 2011-10-14
Install gnome-session-fallback, log out, and select it from the menu when you log in to get the Gnome Panel back. = ) It's a little different, particularly in modifying its settings, many of which are accessed on Alt+Right Click.

---

### Post by woodyg on 2011-10-15
gnome-session-fallback would give me some sort of Ubuntu Classic, or am I wrong? In that case it's a dead end anyway, as one may suspect that option to disappear in the near future. Can as well move to a completely different solution straight away then, e.g. XFCE. If someone has a different solution to this, I would love to hear it.

---

### Post by Copper Bezel on 2011-10-15
Yes, it's similar to the Gnome 2 desktop, but written against the GTK3 libraries and with some tweaks and enhancements. It's Gnome's fallback interface for the near future, and it's very unlikely to disappear, honestly, in the entire Gnome 3 cycle. It's certainly not just going to disappear one day in your 11.10 install. = )

There are a *number* of alternatives, though. Hell, you could just use a Gnome session with xfce4-panel, if that's what you're going for. = )

---

