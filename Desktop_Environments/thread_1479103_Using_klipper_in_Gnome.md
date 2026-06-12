---
title: "Using klipper in Gnome"
date: 2010-05-10
forum: Desktop Environments
---

### Post by JimGvo on 2010-05-10
Glipper just doesn't hack it so I use Klipper on my Gnome desktop, however my clipboard entries are not saved across restarts of the window manager.  I suspect that's because GDM just kills klipper rather than signaling it somehow to quit.  I've tried all of the signals that I though might work hoping that one of them would cause klipper to save the clipboard but none worked.  So has anyone figured out how to save the clipboard history in klipper when the window manager or system restarts like in KDE?  I know I can quit klipper but I forget to.

Thanks,
Jim.

---

### Post by bilkay on 2010-08-08
How did you get klipper started? The only way I've been able to get it on my panel is to invoke it from a terminal, but it doesn't come back on re-login. And it produces a complaint message on logout.

To address your question, the obvious question is, did you check "Save clipboard contents on exit" in the configuration?

---

### Post by JimGvo on 2010-08-09
> **bilkay said:**
> How did you get klipper started? The only way I've been able to get it on my panel is to invoke it from a terminal, but it doesn't come back on re-login. And it produces a complaint message on logout.

To address your question, the obvious question is, did you check "Save clipboard contents on exit" in the configuration?

In reverse, yes I had the save clipboard contents on exit checked.  I've since upgraded to Ubuntu 9.10 on my laptop and it's working OK.

I have it added to the System->Sessions->Startup Applications and it comes up fine all the time, or at least so far.

Jim.

---

### Post by bilkay on 2010-08-09
> **JimGvo said:**
> In reverse, yes I had the save clipboard contents on exit checked.  I've since upgraded to Ubuntu 9.10 on my laptop and it's working OK.

I have it added to the System->Sessions->Startup Applications and it comes up fine all the time, or at least so far.

Jim.
I did that too, and it comes on OK, but a message comes up on logout that it's not responding.

Do you know if there's any way to tell it which panel (upper or lower) it installs in? It doesn't seem to have any man pages.

Thanks for the response.

---

