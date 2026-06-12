---
title: "Steam problem"
date: 2014-04-18
forum: Gaming &amp; Leisure
---

### Post by Ehab_Charek on 2014-04-18
hi guys,
I switched to ubuntu on April 8th (because of the xp end of support thing) and evr since then I've been in love with ubuntu. However, after the latest 14.04 upgrade, steam haven't been working properly. See, I am using the windows version using wine because I like mods (mainly the hidden: source 4b). On 13.10 it worked fine. Now, however, it looks like this
[IMG]https://dl.dropboxusercontent.com/u/32414374/Screenshot%20from%202014-04-18%2017%3A10%3A01.png[/IMG]
I also uninstalled it and all of the files of the games I had in 13.10. Reinstalled it and nothing changed.
any idea how to fix it?

---

### Post by w3bd on 2014-04-18
I'm using 13.10 (waiting for the upgrade to 14.04 to complete) and I can use mods with my linux native steam. Will check with 14.04 as soon as it finishes....

---

### Post by Ehab_Charek on 2014-04-19
how did you do it? "The Hidden" only comes in .exe form. I tried installing it with the linux version of steam but it was not recognized by the program and did not show it in the games list

---

### Post by Ehab_Charek on 2014-04-19
nvm. I figured out how to do it. However, it says that source SDK base 2006 isn't supported on my platform (linux obviously) so I'm downloading 2007. Hope it works D:

---

### Post by Ehab_Charek on 2014-04-19
nevermind, I got it to work!!!!!!
all I had to do is to edit the desktop shortcut (the Steam.desktop) with a text editor and add " -no-dwrite" at the end of the Exec command.
Edit: talking about the windows version

---

### Post by Ehab_Charek on 2014-04-20
ok, I'm having a problem. 
After I went through all the trouble of downloading steam, fixed the issue mentioned above, and installed the hidden, it seems like if I press any button on the keyboard in the game it crashes. Not steam, just the game. I tried it without the fix and it still crashes. Do you know why this is happening?

---

