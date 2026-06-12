---
title: "gedit - set language"
date: 2006-01-29
forum: Desktop Environments
---

### Post by sup on 2006-01-29
Hi, I use Enlish on mys system since I am used to it but since I am Czech I often heve to handle with Czech files and subtitles. I have no problem with openoffice writer but it is a little too heavy to use it for small files without formatting, gedit would be a nice choice here, but it ussually fails to read files with czech letters corectly. I noticed there is an option  tools>set language but although I have Czech installed, I only get English variants to choose from. How can I add Czech or is there any other way to tell overcome this?

---

### Post by ow50 on 2006-01-29
[QUOTE=sup]gedit would be a nice choice here, but it ussually fails to read files with czech letters corectly.[/QUOTE]
This sounds like a character encoding problem. By default, Ubuntu uses UTF-8 encoding. Perhaps you're  trying to open some files saved on Windows. Use Gedit's open dialog and specify the character encoding to use for opening the file. I'm not familiar with Czech, but you can try the Windows-125* and ISO-8859-* variants.

[QUOTE=sup]I noticed there is an option  tools>set language but although I have Czech installed, I only get English variants to choose from. How can I add Czech or is there any other way to tell overcome this?[/QUOTE]
The Tools -> Set Language sets the language for spell checking. To get Czech there, you'd need some czech spelling package. I think Gedit uses Aspell dictionaries and Aspell does not seem to have Czech.

---

### Post by sup on 2006-01-29
I see, I never actually noticed this since I never open files from gedit (nor do I do save as much). cp1250 works well enoughf for me, thanks.

Spell checking is not an issue though, those are not files that wont survive some typos.

---

### Post by dcstar on 2006-01-29
[QUOTE=sup]Hi, I use Enlish on mys system since I am used to it but since I am Czech I often heve to handle with Czech files and subtitles. I have no problem with openoffice writer but it is a little too heavy to use it for small files without formatting, gedit would be a nice choice here, but it ussually fails to read files with czech letters corectly. I noticed there is an option  tools>set language but although I have Czech installed, I only get English variants to choose from. How can I add Czech or is there any other way to tell overcome this?[/QUOTE]
Have you done System-Preferences-Keyboard-Layouts and added a "Czechia" option (in addition to an English one)?

I believe you can then switch between the two with the "Keyboard Indicator" panel icon.

---

### Post by sup on 2006-01-29
yeah, that was actually the first thing I did after installing Ubuntu, since I am not used to writing smilies with English keyboard:-). But that was not the issue, I can view czech webpages, write in czech and view most files in czech with ease. The only problem was with files saved in windows non-unicode encoding, but it is not problem anymore since ow50 adviced me the way to set encoding of opened file. Thanks for help, though!

---

