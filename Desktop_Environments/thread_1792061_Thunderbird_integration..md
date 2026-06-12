---
title: "Thunderbird integration."
date: 2011-06-27
forum: Desktop Environments
---

### Post by creata.physics on 2011-06-27
I've recently started using thunderbird and it is amazing. Much better and faster than Evolution.  My only problem is that I couldn't find any integration for gnome like how ubuntu comes with the integration for Evolution.

I've also uninstalled Evolution and when I click my little mail icon, the menus for Evolution are still there.

I assume a good programmer that preferrs Thunderbird over Evoltion would have made something very similar but I cannot find it, so I may be wrong.

My questions are:

1. If there is integration for Thunderbird like there is for Evolution, can somebody link me to the right place so I can make it happen?

2. If not, how can I remove the Mail, Compose New Message and Contacts icon from my mail icon thing?

---

### Post by Krytarik on 2011-06-27
I've just converted and updated an earlier UF post of mine, please see here:
[http://ubuntu4beginners.blogspot.com/2011/06/replace-evolution-with-thunderbird.html](http://ubuntu4beginners.blogspot.com/2011/06/replace-evolution-with-thunderbird.html)

Greetings.

---

### Post by creata.physics on 2011-06-27
Worked just the way I needed it to.

Now my last issue is this: How do I remove the old evolution mail stuff from that icon? Mail, Compose, Contacts

---

### Post by Krytarik on 2011-06-27
> **creata.physics said:**
> 
Now my last issue is this: How do I remove the old evolution mail stuff from that icon? Mail, Compose, Contacts
In fact, that isn't really Evolution specific, you can use those for Thunderbird as well.

Or is Evolution still listed there, too?

---

### Post by creata.physics on 2011-06-27
How sure are you about that? Evolution has been deleted, but it's icons remain.  When I click on Mail, Compose new message, or Contacts, nothing loads.  Thunderbird has a whole new category of it's own in there.

---

### Post by Krytarik on 2011-06-27
That's what I was meaning by:
> **Krytarik said:**
> 
Or is Evolution still listed there, too?

It seems like you still have the Evolution file here:
"/usr/share/indicators/messages/applications"

If so, delete it.

---

### Post by creata.physics on 2011-06-27
> **Krytarik said:**
> In fact, that isn't really Evolution specific, you can use those for Thunderbird as well.

I had to say the same thing twice, because I said it was there, and you said it wasn't specific until my second post when I was talking about the same thing both times.

[QUOTE=krytarik]It seems like you still have the Evolution file here:
"/usr/share/indicators/messages/applications"[/QUOTE]

Should I remove the whole directory? 
Or just "/usr/share/indicators/messages/applications/evolution"

Because gwibber, thunderbird, and pidgin are there as well.

Edit: Just removed the evolution file, logged out, logged back in and it got rid of it.  Thank you very much for this, it's very handy.  Now only if Thunderbird could be sent to run in the background.  It has to sit on my taskbar for me to get my notifications, and closing it out stops it from being of any use.

My bad, just noticed you said, "looks like you have an evolution file in "directory".  Anyway, you've been awesome, thanks for everything.

---

### Post by Krytarik on 2011-06-28
> **creata.physics said:**
> 
Now only if Thunderbird could be sent to run in the background.  It has to sit on my taskbar for me to get my notifications, and closing it out stops it from being of any use.
Try this extension, I did so once, and it worked fine as far as I remember:
[https://addons.mozilla.org/en-US/thunderbird/addon/minimizetotray-plus/](https://addons.mozilla.org/en-US/thunderbird/addon/minimizetotray-plus/)

Also, one another thing: You may want to disable "Show an alert" in Thunderbird's "Preferences -> General", if it is enabled, to get only one notification when new mails arrive. I forgot to add that to my guide.

---

