---
title: "keyboard combination for non-ASCII characters"
date: 2010-05-04
forum: Desktop Environments
---

### Post by Skaperen on 2010-05-04
I have a list of keyboard combinations for entering certain non-ASCII European characters for a number of languages.  These work on Slackware 12.0 which I have at home.  I'd like to use some of these on Ubuntu (presently 9.10, will be switching to 10.04 probably next month when new PCs come in).  These combinations may be specific to ISO-8859.  I presume Ubuntu is using UTF-8 now.  The key combinations from that list do not work.  Is there a different list to use, instead?

This is on a US layout keyboard, specified as such during the install.

How would you type Eyjafjallajökull for example?  I had to highlight and paste that in since I don't know the key combination to use for letter 'ö'.  I can type it on my home Slackware system with ALT+v using a USA keyboard there.

---

### Post by Zorael on 2010-05-06
One way to do this is by using the Compose (Multi_key) key. I have an AltGr key on my Swedish keyboard that's automatically Compose, but if you don't have one you'll have to assign a different key - such as Right Ctrl if you don't use it much. I believe there's a GNOME dialogue for this somewhere in the keyboard settings.

See [this table](http://www.hermit.org/Linux/ComposeKeys.html). They're fairly intuitive; I mean, %o makes &#8240;, "o makes ö, etc. You can also hit Compose+U, then type a unicode keycode, and hit enter to commit it. Neat if you need to suddenly type out pi or other weird greek letters. This MAY only work in GTK applications.

Another way is to set up your custom key mapping. You can tell your machine that Alt+O should be **ö**, Alt+A should be **å**, etc, by using **xmodmap**.

Run '**xmodmap -pke**' in a terminal to get your current listing. Find the keycode in the list for the key you want to modify to include your new character. You can also run '**xev**' in a terminal and focus the window that pops up, then hit the key you want to divine the keycode of. Then parse the terminal output to find the keycode.

Example from my machine (excerpt from the '**xmodmap -pke**' wall of text);
```
**keycode 32  = [COLOR="Green"]o[/COLOR] [COLOR="Red"]O[/COLOR] [COLOR="Magenta"]o[/COLOR] [COLOR="Blue"]O[/COLOR]**
```
**Keycode 32** translates to the physical key for **O** on my keyboard. Pressing it without any modifiers translates to [COLOR="Green"]**o**[/color], with Shift [COLOR="Red"]**O**[/COLOR], with Alt [COLOR="Magenta"]**o**[/COLOR], with Shift+Alt [COLOR="Blue"]**O**[/COLOR].

Unlikely you need those Alt and Shift+Alt assignment, so just change them to **odiaeresis** and **Odiaeresis** to get **ö** and **Ö**.
```
$ xmodmap -e "**keycode 32 = [COLOR="Green"]o[/COLOR] [COLOR="Red"]O[/COLOR] [COLOR="Magenta"]odiaeresis[/COLOR] [COLOR="Blue"]Odiaeresis[/COLOR]**"
```

I'm not sure if it's possible to set up more than four key codes for a single key, but it looks like it. I don't know how.

Anyway, when you decide on a setup, save the part that's encased within quotes to **~/.Xmodmap**. That should (hopefully) make it be read automatically when you log in. It does in Kubuntu lucid, at least. If it doesn't, you can create a startup script to do it.

I have mine set up to change my Caps Lock key to be **F35** (like F1 and F2 but F35) without modifiers, and to Caps Lock when hit with Shift. Then I bind Yakuake to pop up when I hit F35. I also have the Menu key (next to right Meta key) bound to **F34**, for which I've configure KDE to translate to Ctrl+Tab. So I can hit it to hop to the next tab.
```
$ cat ~/.Xmodmap
keycode 66 = F35 Caps_Lock
keycode 135 = F34 NoSymbol F34 NoSymbol
```

---

### Post by simosx on 2010-05-06
> **Skaperen said:**
> I have a list of keyboard combinations for entering certain non-ASCII European characters for a number of languages.  These work on Slackware 12.0 which I have at home.  I'd like to use some of these on Ubuntu (presently 9.10, will be switching to 10.04 probably next month when new PCs come in).  These combinations may be specific to ISO-8859.  I presume Ubuntu is using UTF-8 now.  The key combinations from that list do not work.  Is there a different list to use, instead?

This is on a US layout keyboard, specified as such during the install.

How would you type Eyjafjallajökull for example?  I had to highlight and paste that in since I don't know the key combination to use for letter 'ö'.  I can type it on my home Slackware system with ALT+v using a USA keyboard there.

The US layout (as with most other layouts) supports certain variants which you can enable in order to type those characters. Those characters that you mention are available on the US keyboard layout on the 'USA International (with dead keys)´ variant.

Therefore, go to System &#8594; Preferences &#8594; Keyboard &#8594; Layouts and add the USA/USA International (with dead keys) layout. You may remove the plain USA layout so that your only layout is USA International (with dead keys).

To type ü, you hit AltGr + u. You can type all sort of characters, including áåé®ðßæñµç«»×¥²³¤€¼½¾‘’&#551;&#7777;š&#283;&#345;&#357;&#328;&#337;&#417;&#303;

---

