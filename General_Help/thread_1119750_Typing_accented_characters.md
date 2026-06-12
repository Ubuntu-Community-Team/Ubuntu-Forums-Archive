---
title: "Typing accented characters"
date: 2009-04-08
forum: General Help
---

### Post by ppb7 on 2009-04-08
Hello,
as a foreign language teacher, being able to type accented characters is vital. Under Windows, I had grown accustomed to type on the numeric keypad the codes associated with them (4-digit codes).
Switching to Linux is only a realistic option if I can type those characters equally as easily WHATEVER THE APPLICATION(:!:). I found a downloadable macro enabling me to type them, but it's only valid for OpenOffice. What i'd really need is a system-wide app that could re-configure the keyboard. So far, I have looked at the character map app which gives UTF codes, but i wouldn't know how to use them without going back to Character map so I would be grateful for your help.

P.S.: BTW, at the moment holding ALT I need 4 keypresses with word, and 3 presses (first 2 presses, then 1 while holding down CTRL)only in OpenOffice. Is there a possibility to assign keyboard shortcuts to those characters?:?:

---

### Post by ppb7 on 2009-04-08
I have just read the page on accented characters at [https://help.ubuntu.com/community/ComposeKey]("https://help.ubuntu.com/community/ComposeKey") but would still like to know if it's possible to create 1- or 2-press keyboard shortcuts as you can on Macs.

---

### Post by Topsiho on 2009-04-08
I see you found information how to do this with a compose-key. I was going to mention [http://ubuntuforums.org/showthread.php?t=45809](http://ubuntuforums.org/showthread.php?t=45809) where you will also find information how to do this with defining a compose key.

The way I do it is using a US international keyboard with dead keys.

This gives me the possibility to do é, ä, ñ, and so on, by typing first the character on top and next the one under it.

Only thing that I cant do is doing ç (c cedilla)(by typing ,c), which however I can do using the compose key method.

I don't know which keyboard you use, typing accented letters may come naturally if you use a French keyboard. Just try :)

Topsiho

---

### Post by ppb7 on 2009-04-09
> **Topsiho said:**
> I see you found information how to do this with a compose-key. I was going to mention [http://ubuntuforums.org/showthread.php?t=45809](http://ubuntuforums.org/showthread.php?t=45809) where you will also find information how to do this with defining a compose key.

The way I do it is using a US international keyboard with dead keys.

This gives me the possibility to do é, ä, ñ, and so on, by typing first the character on top and next the one under it.

I live in England, so assume mine must be a UK keyboard. As I haven't got constant access to a Linux distro, i can't easily test what you mentioned but I have seen that you can define your keyboard via preferences->keyboard.
What puzzles me is that I can't see the difference between what is described in the thread mentioned and the ComposeKey method that you are talking about if you want to write "ç".:?:

---

### Post by ppb7 on 2009-04-09
> **Topsiho said:**
> 
The way I do it is using a US international keyboard with dead keys.
How do you use those dead keys? Do you assign a certain key combination? What is the difference with using a compose key?
I have actually decided to assign the Compose key to the left-Win key but would be very interested in learning if there is an easier way of typing accented characters that does not make you press several keys at the same time. Writing a capital letter means i sometimes have to do WIN+SHIFT+the required key; and what about something like ÄWher I type WIN+SHIFT+diaresis, then SHIFT+A?

---

### Post by jjgomera on 2009-04-09
i think the best solution is change the keyboard layout, look in you /etc/X11/xorg.conf a section like:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
```

with spanish layout I have no problem to write ç, á, ä, à, â...

if you want to change that use the command: sudo dpkg-reconfigure xserver-xorg

If the problem is your keyboard dont support that keys, you can use the dead keys, for this you can use xbindkeys-config (its in repo) to add configuration for that keys

---

