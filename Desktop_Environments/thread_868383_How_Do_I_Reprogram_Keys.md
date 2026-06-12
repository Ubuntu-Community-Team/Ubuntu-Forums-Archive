---
title: "How Do I Reprogram Keys?"
date: 2008-07-23
forum: Desktop Environments
---

### Post by SuperMike on 2008-07-23
I have a special Euro key on the keyboard. When I click it, I get one of those setkeycodes messages in my /var/log/messages. What's the fastest way to reprogram this so that it draws this Euro symbol in my programs in GNOME (including Firefox)?

---

### Post by pauper on 2008-07-23
1) This works for Firefox.

System--Preferences--Keyboard (Preferences)

"Layout Options" tab, select "Adding the EuroSign...", check any suitable box.
Then select "Third level choosers", check any suitable box.

Now to generate &#8364; press these two keys.

[edit:] Done a few tests.
Works in Firefox, gVim, oowriter, oocalc, oobase, ooimpress, PDFedit.
Doesn't work: gedit, subtitleeditor, tomboy.

2) This works everywhere assuming the character is supported.

System--Preferences--Keyboard (Preferences)

"Layout Options" tab, select "Compose key position", check any suitable box.

Press <Compose Key><e><=>

[edit:] Done a few tests.
Doesn't work in PDFedit.

---

### Post by tamoneya on 2008-07-23
you can remap individual keys with xkeycaps.```
sudo apt-get install xkeycaps
```

---

### Post by SuperMike on 2008-07-23
I found that when I chose US International keyboard with dead keys, set it as default, and rebooted, I could do the following:

Right Alt = AltGr

AltGr+5 = Euro
AltGr+Shift+4 = British Pound
AltGr+Dash = Yen

I tried xkeycaps, but it doesn't want to notice the specialized Euro key on my Acer Extensa 4420 laptop. BTW, for anyone new to xkeycaps (I was), you have to rightclick a key to edit it and make it do something. But if that key doesn't even display, that's an entirely different story.

---

### Post by SuperMike on 2008-12-18
> **tamoneya said:**
> you can remap individual keys with xkeycaps.```
sudo apt-get install xkeycaps
```

Wow, that program sucks. I found I could remap the key, but then it screwed up my ability to flip to different terminals.

The fix was:

$ sudo su
# cd /home/<my username>
# ne .xmodmaprc

ne is my favorite command-line editor. You might use vi or joe instead.

Once inside that file, I do this:

keycode 116 = sterling

Now when I type the right windows key, it makes a pound sterling symbol.

---

### Post by tmetro on 2009-09-24
> **SuperMike said:**
> I tried xkeycaps, but it doesn't want to notice the specialized Euro key on my Acer Extensa 4420 laptop. 

On my Acer Aspire 8930, the is a key with the Euro symbol and enother with just "$" and neither seem to generate a scan code according to xev, which suggests to me that they can't be remapped, unless a different keyboard driver/profile is used.

I posted about this here:
[http://ubuntuforums.org/showthread.php?p=6792826#post6792826](http://ubuntuforums.org/showthread.php?p=6792826#post6792826)
but no one offered up any suggestions.

 -Tom

---

