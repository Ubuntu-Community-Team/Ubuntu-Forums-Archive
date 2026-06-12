---
title: "Missing Menu entries in Konqueror since Breezy"
date: 2005-11-15
forum: Desktop Environments
---

### Post by coaxx on 2005-11-15
Hi all,

I am just curios about the missing "Search File/Folder..." option in the "Tools" menu of Konqueror. In hoary it was there. But in Breezy I have to go to K-menue and open "Find File/Folders" as an extra Window.

Or have I missed something?! :confused:

---

### Post by hedge on 2005-11-15
[quote=coaxx]Hi all,

I am just curios about the missing "Search File/Folder..." option in the "Tools" menu of Konqueror. In hoary it was there. But in Breezy I have to go to K-menue and open "Find File/Folders" as an extra Window.

Or have I missed something?! :confused:[/quote]

Rt clk the K menu>Panel Menu>Configure panel. KDE panel will open and then clk layout>Menus Tab> and select the optional menus to display.

hedge

---

### Post by coaxx on 2005-11-15
[QUOTE=hedge]Rt clk the K menu>Panel Menu>Configure panel. KDE panel will open and then clk layout>Menus Tab> and select the optional menus to display.

hedge[/QUOTE]

thx hedge, bu thats not what I meant. I am missing itin the Konqueror Menue (File Manager)

---

### Post by hedge on 2005-11-15
[quote=coaxx]thx hedge, bu thats not what I meant. I am missing itin the Konqueror Menue (File Manager)[/quote]

Sorry about that, what your looking for is in settings > configure tool bars. Then scroll down on the left side and select >find file and clk the arrow to add...

hedge

---

### Post by adriantry on 2005-11-21
I've just been looking for the answer to this question, too. I found it once before, but I've just installed Ubuntu/Kubuntu on a new Sony laptop, and I'd forgotten the answer.

I've just found this:

How do I change Konqueror back to the default KDE profiles?

Kubuntu Breezy comes with a simplified Konqueror profile to make things more use friendly compared to default KDE.

To get back to the default KDE profiles:

sudo rm -r /usr/share/kubuntu-default-settings/kde-profile/default/share/apps/konqueror
sudo cp /usr/share/apps/konqueror/konqueror-orig.rc /usr/share/apps/konqueror/konqueror.rc

I'm about to give it a try, but I'm pretty sure it's the way to go.

By the way, Ubuntu recognised practically everything (including built in wifi) on my laptop first go without any help from me. That's impressive!

Adrian

---

### Post by adriantry on 2005-11-21
Well, that didn't seem to help me much, actually! Something's changed, but it looks like more is missing. I'll have more of a look around.

---

### Post by adriantry on 2005-11-21
Well, I just totally uninstalled konqueror and reinstalled. Then ran the commands.

When I click on the Konqueror Web Browser icon on the task bar, I still get the wrong menu.

But when I use one of the menu items in the System icon (e.g. Home), the menus are now OK - i.e. the old Konqueror menus.

Hope that helps.

---

