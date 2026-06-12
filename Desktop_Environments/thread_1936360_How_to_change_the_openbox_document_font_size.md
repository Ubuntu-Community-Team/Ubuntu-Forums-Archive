---
title: "How to change the openbox document font size?"
date: 2012-03-05
forum: Desktop Environments
---

### Post by nullified_nostalgia on 2012-03-05
Openbox provides a great variety of options for changing font sizes on things, but I'm having some trouble with one of them.  I'm using Pidgin instant messenger and the size of the font in the conversation box is microscopic.  The only way I've found so far to make it any bigger is to adjust my screen resolution extremely far down, which I'd rather not do.  In Pidgin's online documentation it gives instructions to change the document font at the following link:  [http://developer.pidgin.im/wiki/Using%20Pidgin#HowdoIchangethefontPidginusesThebackgroundcolor](http://developer.pidgin.im/wiki/Using%20Pidgin#HowdoIchangethefontPidginusesThebackgroundcolor)

I've edited the .gtkrc-2.0 file as this documentation suggests and it's had no effect at all on the font size in Pidgin.  Does anyone know how I can successfully change the document font size using the openbox window manager?

I'd really appreciate any suggestions.

---

### Post by chestnyh on 2012-03-18
You can try delete pidgin with config files
```

sudo apt-get purge pidgin

```
and istall again.

---

### Post by nullified_nostalgia on 2012-05-16
I figured this one out and forgot to post the solution, so here it is:  In the pidgin plugin GTK+ Theme Control settings I had to go to the font tab and configure the fonts via the buttons that pull up the font settings.  Apparently you can't manually adjust these settings in the  .gtkrc-2.0 file.  Changing them in the plugin settings changes them in the file, but manually changing the file seems to have no effect for some reason.

---

