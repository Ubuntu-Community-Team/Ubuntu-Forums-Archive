---
title: "Sharing environment default programs between environments"
date: 2010-07-15
forum: Desktop Environments
---

### Post by Karnbeln on 2010-07-15
Hello.  I apologize if this is a common noob question I should have been able to find the answer to, but if it is I must lack the vocabulary to express it in a search.

While I've played around with Ubuntu before, I just recently installed it for the first time.  I'd been meaning to do it for a few years, so I knew about there being multiple desktop environments and quickly installed Xfce along with the GNOME that came with Lucid.  I don't know which environment I prefer, so I intend to switch around a lot.

Thunderbird came with Xfce, and I've set up my email accounts on it.  Of course, however, it is not a default program on GNOME.  I need to make Thunderbird show up in GNOME, but without actually installing a new copy, as I want anything I do in Thunderbird in one environment to affect it in the other.  Both environments also came with Firefox, and each copy acts independently of the other. I'd like to fix that as well if possible.

To see if it was even possible, I installed SuperTuxKart through the software center on GNOME.  Sure enough, it showed up automatically in xubuntu.  Now I just have to figure out how to make this work with those pesky default programs.

Thank you for any help you can give me.

---

### Post by lovinglinux on 2010-07-15
> **Karnbeln said:**
> Thunderbird came with Xfce, and I've set up my email accounts on it.  Of course, however, it is not a default program on GNOME.  I need to make Thunderbird show up in GNOME, but without actually installing a new copy, as I want anything I do in Thunderbird in one environment to affect it in the other.  Both environments also came with Firefox, and each copy acts independently of the other. I'd like to fix that as well if possible.

All you need to do is to create a new launcher on your desktop or menu. I don't use Xfce, so I don't know exactly the procedure (right-clicking on the desktop should give you an option) , but you should be able to launch any program on each desktop environments. For instance you can even launch KDE plasma over Gnome. 

For thunderbird, the command launcher will probably be "thunderbird" or "thunderbird %u" and for Firefox "firefox" or "firefox %u". You also might want to change the default programs for web and e-mail.

> **Karnbeln said:**
> Both environments also came with Firefox, and each copy acts independently of the other. I'd like to fix that as well if possible.

That's not how it works, unless Xfce is completely different, which I doubt. Firefox and Thunderbird rely on user profiles, that are saved in your home directory. Firefox is saved under ~/.mozilla/firefox and Thunderbird I guess under ~/.thunderbird. It doesn't matter which desktop environment you use, whenever you start Firefox or Thunderbird, they will look for the user profile on those folders and launch them. So, you will still be able to access all your bookmarks, e-mails, passwords, extensions and so on.

---

### Post by Karnbeln on 2010-07-16
Thanks for your help.

---

### Post by lovinglinux on 2010-07-17
> **Karnbeln said:**
> Thanks for your help.

Is you problem solved?

---

