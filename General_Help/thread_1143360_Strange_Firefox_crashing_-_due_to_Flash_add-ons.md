---
title: "Strange Firefox crashing - due to Flash add-ons?"
date: 2009-04-29
forum: General Help
---

### Post by emu42 on 2009-04-29
I was having problems with playing Flash on Firefox, so I decided it wouldn't hurt to just install the most recent version of Firefox (3.0.10). But now, Firefox seems to quickly check the add-ons when I start it up, and then starts in safe mode. When I go to Tools->Add-ons Firefox immediately shuts down with no message or anything.

I (still) use Ubuntu 8.04.

---

### Post by fdrake on 2009-04-29
try to remove and reinstall:
```
sudo apt-get remove firefox (remove)
sudo apt-get install firefox (install)
firefox (run)
```
if firefox crashes again paste here the output of the terminal

---

### Post by emu42 on 2009-04-29
The re-installment of Firefox went normally, no error messages, but this was outputted when I started Firefox again:

"firefox

(firefox:29847): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(firefox:29847): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(firefox:29847): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."

and then when I began to use it, this came up:

"** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)"

---

### Post by fdrake on 2009-04-29
does it crashes too?

what about :
> sudo firefox

---

### Post by emu42 on 2009-04-29
When I do sudo firefox, it doesn't start in safe mode and those error messages aren't there at the beginning. Thanks for suggesting that. But, when I try to use Flash, I get something like this in the terminal:

"
(firefox:7203): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7203): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7203): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7203): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7203): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7203): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7203): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7203): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7203): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed"


I still don't know what this is. I have the latest verion of Flash, which I downloaded about a month ago so it shouldn't be too dated.

---

### Post by emu42 on 2009-04-30
The sudo firefox command doesn't start up Firefox in safe mode, which is good. But how do I make it always start up that way? When I go to the icon and do right click->properties and change the command to something else, it gives the error "Failed to close file '(...)gnome2/panel2.d/default/launchers/sudo.desktop.MCVUSU': fclose() failed: Success". I'm sure I'm just doing something wrong, but I'm not sure what.

I just installed the latest version of Flash and problems are persisting. When I try to play a Flash video, it goes for about 2 seconds and then stops. It's really annoying.

---

### Post by fdrake on 2009-04-30
> **emu42 said:**
> The sudo firefox command doesn't start up Firefox in safe mode, which is good. But how do I make it always start up that way? When I go to the icon and do right click->properties and change the command to something else, it gives the error "Failed to close file '(...)gnome2/panel2.d/default/launchers/sudo.desktop.MCVUSU': fclose() failed: Success". I'm sure I'm just doing something wrong, but I'm not sure what.

I just installed the latest version of Flash and problems are persisting. When I try to play a Flash video, it goes for about 2 seconds and then stops. It's really annoying.

first of all i don't suggest you to use "sudo firefox" to often for you internet navigation, for security reasons.

second.to change the command of the icon do this:
   1.select/run properties
   2.on "Type"filde select "Application in terminale"
   3. on "Command" field ,type this "sudo firefox"

i am looking to find out the possible causes of this issue.

i don't understand why ur firefox runs in safe mode?

---

### Post by fdrake on 2009-04-30
i have a new suggestion now. tell me what happens if you run firefox like this  (without SUDO):
1. go to the firefox icon and select "Properties"
2. Selecte "TYPE" as "application" (no terminal)
3."COMMAND" "firefox %u"[URL="http://support.mozilla.com/en-US/kb/Firefox+is+stuck+in+Safe+Mode#Ubuntu"]

SOURCE[/URL]

---

### Post by emu42 on 2009-04-30
When I click "Close" after I've adjusted the properties, it still gives that error message (Failed to close file '(...)gnome2/panel2.d/default/launchers/sudo.desktop.MCVUSU': fclose() failed: Success).

---

