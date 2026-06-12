---
title: "Where are the settings for Indicator Applet Complete"
date: 2011-07-14
forum: Desktop Environments
---

### Post by choudharypranay on 2011-07-14
I want to edit (remove some items, especially evolution) from the "Indicator Applet Complete" present in the right top corner.
I'm using Natty in classic mode.

How can I do this? I do not want the chat, mail and ubuntu one options in my panel.

Thanks in advance.

---

### Post by Krytarik on 2011-07-14
You are talking about:

[LIST]
[*]"indicator-me": status/chat
[*]"indicator-messages": mail envelope
[/LIST]
To remove them from the applet, just remove those packages. Unfortunately, there is no other way.

The same is true for "indicator-sound", if you want to remove those item as well.

Greetings.

---

### Post by choudharypranay on 2011-07-16
> **Krytarik said:**
> To remove them from the applet, just remove those packages.

I uninstalled the following components:
1. empathy
2. gwibber
3. ubuntu one
4. evolution

But still i get mail envelop and chat icon.
mail envelop now shows only one option : set up mail (clicking on which nothing happens)
chat icon has all items disabled except about me.

---

### Post by Krytarik on 2011-07-16
Actually, it was more meant like this ;-) :
```

sudo apt-get purge indicator-me
sudo apt-get purge indicator-messages
```Greetings.

---

### Post by choudharypranay on 2011-07-18
> **Krytarik said:**
> ```

sudo apt-get purge indicator-me
sudo apt-get purge indicator-messages
```Thanks. It worked.

---

