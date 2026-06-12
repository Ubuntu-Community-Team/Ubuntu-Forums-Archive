---
title: "Automatic accenting with apostrophe/quote."
date: 2006-09-24
forum: Desktop Environments
---

### Post by Glum_Reaper on 2006-09-24
Hi guys, 

Hope someone can help me with this, I´ve searched the forum and I´ve googled all I can but still can´t find the answer.

I´ve had dapper installed a few weeks, but the last couple of days it seems I have somehow turned on a really annoying automatic accenting option. Now when I press apostrophe or quote, it waits for me to press the next letter then accents it. So apostrophe followed by e produces é. To get an actual apostrophe or quote (or tild apparently) I have to double tap the key.

This is really annoying and takes me a lot longer to type anything!

In preferences > keyboard layout I have the keyboard as a Generic 101-key (although I have also tried 104/105 and a few others) and the keyboard layout is UK international with dead keys - which was the only one under UK apart from Dvorak.

Thanks for reading, hope you can help!

---

### Post by moeFinley on 2007-01-09
Run the following in the terminal.

```
xmodmap /usr/share/xmodmap/xmodmap.uk
```

It's something to do with XGL/Compix being setup for the UK?  There is a post about it [here]("http://ubuntuforums.org/showthread.php?t=291223").

---

