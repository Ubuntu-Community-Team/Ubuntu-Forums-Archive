---
title: "&quot;Chat&quot; icon in MessagingMenu gone"
date: 2010-09-07
forum: Desktop Environments
---

### Post by Chronos77 on 2010-09-07
Hello Ubuntu-Fam!
I have a problem. The "Chat"-Entry of the Messaging Menu is gone.
I did a little troubleshooting because i had problems that on my Ubuntu-64bit system Gwibber wasn't working with facebook. No entries.
Therefore i put in these commands in the terminal:

rm -rf ~/.cache/desktop-couch ~/.config/desktop-couch ~/.local/desktop-couch

but after rebooting the entry "chat" in the messaging menu was gone.  i tried to reinstall empathy, desktopcouch and gwibber. No success yet. I deleted all the empathy entries but no luck.
By the way, Gwibber is working in the meantime.
For the moment i start empathy with the -h command as startprogram, but the additional icon is not the best solution. The integration in the messaging menu was much better.
I want this chat entry back. Please!! ;-)
Can someone help?
I hope you understand what the problem is. My english is not the best.
Thank you!!
Peter from Mainz /Germany

---

### Post by Chronos77 on 2010-09-07
Sorry, i helped myself so far:D
I created the file empathy (textfile) in the directory 
/usr/share/indicators/messages/applications with the following content:

"/usr/share/applications/empathy.desktop"

That's it. My Icon is back :))

But now, when i click the chat icon, the Empathy-Icon/Program appears and doesn't hide the icon.
Has this ever been this way?? I don't remember that this program-.icon was there.
Some ideas how to integrate this in the messaging menu?

By Peter

---

### Post by clicker4721 on 2010-10-12
> **Chronos77 said:**
> I created the file empathy (textfile) in the directory 
/usr/share/indicators/messages/applications with the following content:

"/usr/share/applications/empathy.desktop"

That's it. My Icon is back :))

But now, when i click the chat icon, the Empathy-Icon/Program appears and doesn't hide the icon.
Has this ever been this way?? I don't remember that this program-.icon was there.
Some ideas how to integrate this in the messaging menu?

By Peter

This is definitely not how it's supposed to be. I'm here because I had the same error. I tried your fix, but it just adds the entry, no integration: always a "Set Up Chat..." entry.

Does anybody have a solution?

---

