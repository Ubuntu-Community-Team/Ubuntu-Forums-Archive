---
title: "Keyboard layout for Lubuntu 14.04"
date: 2014-04-24
forum: Desktop Environments
---

### Post by srope01 on 2014-04-24
I have been running Lubuntu 12.04 for a couple of years on an old IBM ThinkCentre S50. With the LTS release of 14.04, I have upgraded it, hoping that it will give me several more years of life.

First problem I have is the keyboard layout. I am using a Swiss keyboard and previously with 12.04 it was set for the Swiss French layout with no problems. When I booted into 14.04 the first time, I got the US keyboard layout. I changed it via the Keyboard Layout Handler panel application, but the list of layouts does not include the French (Swiss) layout! At the moment I am using German (Swiss) because that one is the closest I can get to the layout I want. The Swiss French and Swiss German layouts are different even though the same keyboard is used. Is there a reason Swiss French is not included in Lubuntu?

I also tried installing Lxkeymap which does list Swiss French, but when I click on Apply, it does not change the layout. I still get German characters.

Can anyone help out there?

---

### Post by bapoumba on 2014-04-24
I just have one keyboard type and cannot test. Would something here work ? [http://ubuntuforums.org/showthread.php?t=1455877](http://ubuntuforums.org/showthread.php?t=1455877)
I've checked my own /etc/default/keyboard, and that looks about right for the French keyboard I use here.

---

### Post by srope01 on 2014-04-25
Thanks for your quick reply. I looked at /etc/default/keyboard and it appears to be correct.

```

XKBMODEL="pc105"
XKBLAYOUT="ch"
XKBVARIANT="fr"
XKBOPTIONS=""
```

CH is Switzerland and FR is the French variant. I also ran the setxkbmap command.

```
setxkbmap -layout "ch(fr)"
```

But I am still locked to the Swiss German keyboard. Is this a bug in LXDE? Something seems to be overwriting the layout (possibly the Keyboard Layout Handler since it does not have CH(FR) in the list).

EDIT (recent update): I just found under Preferences -> Keyboard Input Method which leads to IBus Preferences dialog box. Under the Advanced tab, there is a checkbox Use system keyboard layout. I checked this, but it still has no effect. Also under Preferences -> Input Method, I get the following message.

```
Current configuration for the input method:
 * Active configuration: ibus (normally missing)
 * Automatic configuration: ibus (normally ibus or fcitx or uim)
 * Number of valid choices: 2 (normally 1)
The configuration set by im-config is activated by re-starting X.
Explicit selection is not required to enable the automatic configuration, if the active one is default/auto/cjkv/missing.
  Available input methods: ibus xim
Unless you really need them all, please make sure to install only one input method tool.
```

Could someone explain to me what this message means?

---

### Post by bapoumba on 2014-04-25
I'll have to look around, but I have the exact same message.

One stupid idea, would you happen to have another ch keyboard to test ?

Edit, is an additional reading. In addition, is your locale set to fr_ch ? You can check running **locale** in a terminal.
[http://forums.linuxmint.com/viewtopic.php?f=175&t=62681](http://forums.linuxmint.com/viewtopic.php?f=175&t=62681)

I'd also try this : [http://ubuntuforums.org/showthread.php?t=1455877&p=10844633#post10844633](http://ubuntuforums.org/showthread.php?t=1455877&p=10844633#post10844633)
Back up the current file before editing, just in case, log out and log back in to be effective.

---

### Post by Krytarik on 2014-04-25
> **srope01 said:**
> I changed it via the Keyboard Layout Handler panel application, but the list of layouts does not include the French (Swiss) layout! At the moment I am using German (Swiss) because that one is the closest I can get to the layout I want.
> **srope01 said:**
> ...possibly the Keyboard Layout Handler since it does not have CH(FR) in the list
Look harder, it does :P - right under the one you've found, which happens to be the main layout for Swiss keyboards, "ch".

> **srope01 said:**
> I also tried installing Lxkeymap which does list Swiss French, but when I click on Apply, it does not change the layout. I still get German characters.
Hmm, that works here too.

Regards.

---

### Post by srope01 on 2014-04-25
> **bapoumba said:**
> One stupid idea, would you happen to have another ch keyboard to test ?

Yes, I do. Using a more modern Swiss keyboard there is unfortunately no difference.

> **bapoumba said:**
> Edit, is an additional reading. In addition, is your locale set to fr_ch ? You can check running **locale** in a terminal.
[http://forums.linuxmint.com/viewtopic.php?f=175&t=62681](http://forums.linuxmint.com/viewtopic.php?f=175&t=62681)

I ran locale and it is set to en_GB. But this is what I expect because I am using Swiss computers and keyboards, but my main language is English.


> **bapoumba said:**
> I'd also try this : [http://ubuntuforums.org/showthread.php?t=1455877&p=10844633#post10844633](http://ubuntuforums.org/showthread.php?t=1455877&p=10844633#post10844633)
Back up the current file before editing, just in case, log out and log back in to be effective.

I tried this (XKBLAYOUT="us,ua,ru") which is effectively trying to change the keyboard layout to a US keyboard and setting a toggle. This also has no effect. I still have the Swiss German layout. It seems to me that any change to /etc/default/keyboard is ineffective because all those parameters are being overwritten by something else. It seems that Keyboard Layout Handler has the final master control. But unfortunately, that does not have the Swiss French layout as an option. (see reply below) Is there a way to suppress the Keyboard Layout Handler and force LXDE to just use the X11 file /etc/default/keyboard?

> **Krytarik said:**
> Look harder, it does :razz: - right under the one you've found, which happens to be the main layout for Swiss keyboards, "ch".

But take a look at what it says under Description. This is the German variant of the ch keyboard which gives German umlaut characters instead of French accented characters. I would like the French variant of the ch keyboard. It should have been listed under Layout - ch, Description - French (Switzerland). As a side note, the French keyboard layout (Layout - fr, Description - French) is completely different from the Swiss one.

---

### Post by Krytarik on 2014-04-25
> **srope01 said:**
> But take a look at what it says under Description. This is the German variant of the ch keyboard which gives German umlaut characters instead of French accented characters. I would like the French variant of the ch keyboard. It should have been listed under Layout - ch, Description - French (Switzerland).
Well, I said "under", not the exact one :-) - hit the arrow symbol in front of it to reveal all the variants of "ch", incl. the "ch(fr)" one.

---

### Post by srope01 on 2014-04-25
Ah yes, thank you. Not obvious because they ordered the flags by languages. The list should have been ordered by country name. As a francophone, I would contest that the French variant would be hidden behind ch-German. But in any case, case solved. Thanks again.

---

### Post by bapoumba on 2014-04-26
Thanks Krytarik, and thanks srope01 for marking your thread as solved :)

---

### Post by fugazi32 on 2014-04-28
Hi, changed my */etc/default/keyboard* to:

```

# If you change any of the following variables and X is configured to
# use this file, then the changes will become visible to X only if udev
# is restarted.  You may need to reboot the system.

# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.

XKBMODEL="pc105"
XKBLAYOUT="gb,us"
XKBVARIANT=","
XKBOPTIONS="grp:ctrl_shift_toggle,grp_led:scroll"

# If you don't want to use the XKB layout on the console, you can
# specify an alternative keymap.  Make sure it will be accessible
# before /usr is mounted.

```

I wanted a UK keyboard but still got an American one on boot up :(

---

### Post by bapoumba on 2014-04-28
Are you on lubuntu ?
Right click on the panel keyboard and choose "Keyboard Layout Handler" Settings, you should have different layouts to choose from. Add the one you need if it is missing.

---

