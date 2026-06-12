---
title: "Shift + Backspace logs out of gnome.."
date: 2006-06-19
forum: Desktop Environments
---

### Post by Dakaru on 2006-06-19
How can I change this? It is really starting to piss me off.

---

### Post by Joeb on 2006-06-19
Are you sure you have the right keyboard and locale set (ie 104 or 105 and the correct country)?  I have heard that certain locales use shift-backspace the same as ctrl-alt-backspace to restart the X server which would look like it is taking you back to the login screen.

---

### Post by calx on 2006-06-19
[http://www.ubuntuforums.org/showthread.php?t=140658]("http://www.ubuntuforums.org/showthread.php?t=140658")

[QUOTE=Dakaru]How can I change this? It is really starting to piss me off.[/QUOTE]

---

### Post by Dakaru on 2006-06-19
[QUOTE=calx][http://www.ubuntuforums.org/showthread.php?t=140658]("http://www.ubuntuforums.org/showthread.php?t=140658")[/QUOTE]
Sweet. Thanks.

---

### Post by leohart on 2006-06-21
[QUOTE=calx][http://www.ubuntuforums.org/showthread.php?t=140658]("http://www.ubuntuforums.org/showthread.php?t=140658")[/QUOTE]

That is NOT a good solution at all since it remaps all your keyboard combination thus making all Copmiz keyboard shortcut stop working. The ONLY reason to get Xgl working (for most people) is Compiz. If Compiz doesn't work then why do I need Xgl to start with. We need a better solution. Anyone?

---

### Post by TimL on 2006-06-30
From the compiz forums ([here]("http://www.compiz.net/viewtopic.php?id=1199")) the suggestion is to do the following:

xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

Put this in a script and call it as one of your startup programs via the sessions settings.

Cheers,

Tim

---

### Post by jimarko on 2006-07-01
TimL, you champ. That xmodmap command works a treat.

Thanks!

---

### Post by Lord Illidan on 2006-07-01
[quote=leohart]That is NOT a good solution at all since it remaps all your keyboard combination thus making all Copmiz keyboard shortcut stop working. The ONLY reason to get Xgl working (for most people) is Compiz. If Compiz doesn't work then why do I need Xgl to start with. We need a better solution. Anyone?[/quote]

When I wrote that howto, my compiz keyboard shortcuts still kept on working.

---

