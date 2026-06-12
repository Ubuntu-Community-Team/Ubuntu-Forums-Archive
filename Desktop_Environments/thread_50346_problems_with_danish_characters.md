---
title: "problems with danish characters"
date: 2005-07-20
forum: Desktop Environments
---

### Post by anti on 2005-07-20
hello there.

I've got an annoying problem, which is that the danish characters (æ, ø, å) stop working after I've connected to another box through ssh. at the normal prompt after login (still through ssh to another box) the characters show, but when I do a backspace, I can delete two spaces, even if one of those characters were the first on the line.
second, when I reattach to the screen (the app) I'm using the characters show up as boxes with spaces after them. only after switching from one "window" in screen will they show correctly, although still with the spaces after them.
this doesn't happen on my gentoo and fedora installs, so it's new to me. I've tried fiddling around with lang and locale settings, but nothing seems to help.
also, the screen/ssh/box I'm connecting to works with everything else.

thanks in advance :D

Edit: might be a good idea to add that I'm using gnome-terminal.
Eterm also has problems, not even displaying the characters correctly locally. æøå show up as Ã¦Ã¸Ã

---

### Post by uniko on 2005-07-20
Try changing the character encoding from UTF-8 or other to Nordic (ISO-8859-10). Helps me with åöä´s showing correctly on gnome terminal.

---

### Post by msh on 2005-07-20
The problem is that ubuntu uses UTF8 as character set but most other linux systems uses something else.

Either change the character set on your terminal or on the server to western or nordic.

---

### Post by pmj on 2005-07-20
I have the same problem. I can't write the Swedish characters å, ä and ö when I ssh to my Ubuntu box. It gets even worse in irssi (an irc client), if I press one of these keys more than once the text input breaks and I need to ctrl+c. I've tried every character encoding available in the SecureCRT settings, but I'm not really sure how this works so I might very well be doing something wrong.

---

### Post by msh on 2005-07-20
try changing the locale of your unbutu box to something other than utf8 in the controlpnel thing.

---

### Post by anti on 2005-07-20
thanks for the suggestions. found something that worked. dpkg-reconfigure locales and a reboot did the trick.

---

