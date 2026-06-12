---
title: "Help: Conky on Compiz-Fusion"
date: 2007-07-17
forum: Desktop Effects &amp; Customization
---

### Post by Nessa on 2007-07-17
I've tried twice maybe three times. (I can't remember exactly.) Installation gave no error messages but conky simply doesn't show up. :(

I did the ctrl-alt-backspace. No effect. The .conkysomething file has been edited. I've loaded the dbe thing in section module or something. Can't remember. Added conky in session. But it the part of the tutorials where it says conky should be on the desktop, it's not.

Anything else I need to do?

---

### Post by Technoviking on 2007-07-17
You have to delay conky from running till Compiz-fusion loads.

I have Session load the following script instead loading conky directly.
```
#!/bin/bash
sleep 15 && conky;
```

---

### Post by Nessa on 2007-07-17
Sorry, I've only had ubuntu for a few days.

How do I do that?

---

### Post by Nessa on 2007-07-17
Finally got it working!

It seems like the cpu temp jumps a lot (10-30 C difference). Is this normal?

Also, conky only shows up in 1 workspace? Is that supposed to be that way?

---

### Post by Depressed Man on 2007-07-22
By default? Yes. But there's a line you enter into its configuration file that allows it to be seen on all desktops. I don't know it myself (it's in tons of forums if you do a search for it though) as I'm still trying to set mine up.

---

### Post by 5-HT on 2007-07-22
> **Depressed Man said:**
> By default? Yes. But there's a line you enter into its configuration file that allows it to be seen on all desktops. I don't know it myself (it's in tons of forums if you do a search for it though) as I'm still trying to set mine up.
Append 'sticky' to your 'own_window_hints' array in your ~/.conkyrc (given that you're drawing conky to its own window: 'own_window 1')
cheers,

---

