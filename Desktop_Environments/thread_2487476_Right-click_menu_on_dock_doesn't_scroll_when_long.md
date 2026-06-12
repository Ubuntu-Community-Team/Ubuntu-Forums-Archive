---
title: "Right-click menu on dock doesn't scroll when long"
date: 2023-06-06
forum: Desktop Environments
---

### Post by Paddy Landau on 2023-06-06
When you right-click on a "Favourite" in the dock, it shows a small menu relating to that app. For example, right-click on Nautilus to show the options "All Windows", "New Window", and the various Nautilus shortcuts.

However, when the menu is long (I have lots of Nautilus shortcuts, so this happens with me), the top of the menu, which is the most important bit (for me, anyway, as I want "New Window") disappears above the screen.

See the screenshot, which shows the very top-left of my monitor after I've right-clicked on the Nautilus shortcut.

Unfortunately, this menu cannot be scrolled.

Is there a solution to this? If not, where do I raise a bug report &#8212; with Gnome, Ubuntu or someone else?

Thank you
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292356&stc=1[/IMG]

---

### Post by douglas.e.ryan on 2023-06-09
I don't guess you want to default out Gnome? Even if not, that could be an option is if all else fails. Here are a couple ideas. Do you have an dock extensions that could interfere with the dock? Did this start happening after you changed the icon size? Maybe it could even be display scaling.

---

### Post by Paddy Landau on 2023-06-09
> **douglas.e.ryan said:**
> I don't guess you want to default out Gnome?
I'm sorry, I don't know what you mean?
> **douglas.e.ryan said:**
> Do you have an dock extensions that could interfere with the dock?
I don't believe so, no. But, I just tried turning off **all** of my extensions, and the problem remains. I still can't scroll the dock menu.
> **douglas.e.ryan said:**
> Did this start happening after you changed the icon size?
I changed my icons back to the default size. No change.
> **douglas.e.ryan said:**
> Maybe it could even be display scaling.
I haven't changed my display scaling; it's at the default 100%.

No, I think that the problem is that the menu doesn't have the ability to scroll when it gets so large that it exceeds the height of the monitor. At the very least, it needs to allow access to the top items of the menu.

I think that I should report this, but I'm unsure where. Is this default Gnome behaviour, or did Ubuntu introduce it?

---

### Post by Paddy Landau on 2023-06-20
I have [reported this problem]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2024424") on Launchpad.

---

