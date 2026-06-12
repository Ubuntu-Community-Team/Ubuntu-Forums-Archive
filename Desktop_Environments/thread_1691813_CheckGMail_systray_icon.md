---
title: "CheckGMail systray icon"
date: 2011-02-20
forum: Desktop Environments
---

### Post by bertles86 on 2011-02-20
Hi folks,

I'm running Meerkat and have CheckGMail installed from the Ubuntu Software Centre.

It runs fine and functionality is 100%, but the icon is a grey/white envelope with a white/light grey background.

How can I get it to blend into the systray?

I did a search, and followed a couple of sets of instructions with no luck.

---

### Post by nidzo732 on 2011-02-20
Right click>>preferences>>set tray background

---

### Post by bertles86 on 2011-02-20
Afraid I tried that one, with no change. Any other clues? Or is an alternative Gmail notifier?

---

### Post by bertles86 on 2011-02-20
So I updated it:

```
sudo checkgmail --update
```

In shell I then type 'Y' to agree to the update, it gets down to:

```
OK to update to new version via 'sudo mv checkgmail /usr/bin/'?(Y/n)> Y
chmod a+x checkgmail
sudo mv checkgmail /usr/bin/

Restarting checkgmail ...
Warning: Gtk2::Sexy not found ...

CheckGmail uses Gtk2::Sexy for clickable URLs in mail messages
Please download and install from CPAN (http://search.cpan.org) if you want to use this feature ...

Creating translations file at /root/.checkgmail/lang.xml ...
Updating translations file ...
Wide character in print at /usr/bin/checkgmail line 5118.
 ... done!
```

Then opens the preferences window, and it still has the wrong background.

The shell hangs on 'done!' and doesn't return to the prompt.

---

### Post by bertles86 on 2011-02-20
I found the fix [here]("http://ubuntuforums.org/showthread.php?t=1520603/#8"). All working.

---

