---
title: "Spanish input with Japanese keyboard?"
date: 2005-04-27
forum: Desktop Environments
---

### Post by AMPF on 2005-04-27
Hi. For a long time Japanese input was quite difficult with Linux. Now that it's pretty much solved I'm suffering the opposite. I installed Ubuntu 5.04 on a Japanese Toshiba laptop. Within Gnome, once I choose Japanese 106 international keyboard everything works fine, but as soon as I add the Spanish layout (or any additional layout to the Japanese one) then, when I choose Japanese from the keyboard switcher applet or in the keyboard preferences, I get katakana when I type.
If you wonder why I don't use a Spanish-only layout it's because some symbols aren't available on a Japanese keyboard when it's set to a Spanish mapping. Also it's nice to get the symbols drawn on the keys Another point is that I'm not the only user of the computer and I'd like to have a full-working dual language setup.
As a sidenote, and just an issue of usability, something is not quite right if a Japanese layout behaves differently if there are more layouts on the list. It doesn't make much sense. Also, the keyboard image shown on the keyboard preferences doesn't agree with the katakana output. Of course, these two problems would go if the katakana thing doesn't happen.

Help greatly appreciated. TIA.

---

### Post by an9n on 2005-07-18
[QUOTE=AMPF]Hi. For a long time Japanese input was quite difficult with Linux. Now that it's pretty much solved I'm suffering the opposite. I installed Ubuntu 5.04 on a Japanese Toshiba laptop. Within Gnome, once I choose Japanese 106 international keyboard everything works fine, but as soon as I add the Spanish layout (or any additional layout to the Japanese one) then, when I choose Japanese from the keyboard switcher applet or in the keyboard preferences, I get katakana when I type.
If you wonder why I don't use a Spanish-only layout it's because some symbols aren't available on a Japanese keyboard when it's set to a Spanish mapping. Also it's nice to get the symbols drawn on the keys Another point is that I'm not the only user of the computer and I'd like to have a full-working dual language setup.
As a sidenote, and just an issue of usability, something is not quite right if a Japanese layout behaves differently if there are more layouts on the list. It doesn't make much sense. Also, the keyboard image shown on the keyboard preferences doesn't agree with the katakana output. Of course, these two problems would go if the katakana thing doesn't happen.

Help greatly appreciated. TIA.[/QUOTE]
 I just posted a reply in this thread, I think it would help you.with your keyboard layout problems.

[http://ubuntuforums.org/showthread.php?p=260053#post260053](http://ubuntuforums.org/showthread.php?p=260053#post260053)

---

### Post by DanIssa on 2007-07-12
This can be done easier actually even with the Japanese keyboard (at least this is what I did with my British keys). First, you can get a set of Spanish keyboard stickers (I got mine at [http://www.latkey.com]("http://www.latkey.com")) and then do the following:

1.Edit the file: /usr/share/X11/locale/en_US.UTF-8/Compose
2.Replace the occurences of the &#263; with ç, for both lower and uppercase.
3.Edit the file: /etc/gtk-2.0/i386-redhat-linux-gnu/gtk.immodules
4.Find the line configuring "xim", and add the "en_US" and "en" locales there, like this:
  "/usr/lib/gtk-2.0/2.4.0/immodules/im-xim.so"
  "xim" "X Input Method" "gtk20" "/usr/share/locale" "ko:ja:th:zh:en_US:en"

---

