---
title: "caller id"
date: 2007-08-10
forum: Desktop Effects &amp; Customization
---

### Post by Lary Grant on 2007-08-10
Is there any linux app to read the caller ID from a phone line and pop it up on the screen when a call comes in?

---

### Post by kidders on 2007-08-11
Hi there,

Although I don't know of any off hand, I'm sure a quick web search will throw up applications that do what you need.

If you know a little about the AT command set though, such an application is unnecessary. For instance, a single command along the lines of the following would do the trick...
```
kdialog --msgbox "Incoming call from `grep -m 1 '^+CLIP' /dev/ttyACM0 | sed 's/.*: \([^,]*\),.*/\1/'`"
```Working from the inside out...[LIST]
[*]I constructed this example using my mobile phone, connected at /dev/ttyACM0, configured to echo this sort of thing when a call comes in...
```
+CRING: VOICE
+CLIP: "+353830000000",129,,,""
```
[*]The **grep** waits for a line starting "+CLIP", and terminates.
[*]The result is passed to **sed**, which captures the phone number.
[*]**kdialog** uses that as part of its command line arguments, throwing up a dialog box.[/LIST]Anyhow, unless you're likely to find the other features that telephony applications tend to offer useful, I would suggest the low-tech approach. Otherwise, why not try a few apps, and see which you like best?

---

