---
title: "Keyboard shortcuts and locale settings not sticking, plus SCIM"
date: 2009-01-21
forum: General Help
---

### Post by iwsfutcmd on 2009-01-21
Hey everybody,

I've got three problems that I thought were unrelated, but after careful inspection, may have something to do with each other.

The first is my keyboard shortcuts. I'm on a laptop (Asus EEE 1000) and I've set keyboard shortcuts so fn+f10, fn+f11, fn+f12 do Volume Mute, Volume Down, and Volume Up, respectively. This works fine, but as soon as I restart the system, the shortcuts no longer work and I have to set them up again via the GUI.

The second is that my locale is set for English, South Africa, and I can't seem to get it to change. Both the applicable variables in /etc/environment are set to en_US, but if I run 'locale', everything comes up as en_ZA. If I use the GUI and go to the Language Support settings window, my default language is set as English (South Africa). The 'Enable support to enter complex characters' box is also not ticked (I would like it to be). When I change it to English (United States), the 'Enable support...' box becomes ticked, but if I click 'Apply', it just reverts to English (South Africa) and the box becomes unticked. If I hit 'OK' it closes the dialog box, but if I reopen it, back to South Africa.

My third issue is that SCIM doesn't work at all. The only way I can get the taskbar button up is to manually run the 'scim' command from the console, and even then, clicking on it does nothing. Right clicking gives me the setup menu, but I can't change the input method.

Thanks in advance for everything!

-Ben

-edit-
So I resolved issues 2 and 3. While futzing around with the Language Support panel, I figured out that if I did each step individually (turned on complex text, clicked apply, changed locale to US, clicked apply) it worked and got SCIM working too. The first issue is still unresolved though...

---

