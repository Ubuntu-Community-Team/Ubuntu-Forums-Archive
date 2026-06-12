---
title: "associating mp3 files with cedega-based apps.."
date: 2005-10-31
forum: Desktop Environments
---

### Post by slimzky on 2005-10-31
i tried to install JetAudio using cedega & it works!!! so now i have an mp3 player on my Ubuntu box but i want to know how can i associate the mp3 files to JetAudio... is that possible? so that i cud play it by double-clicking.... 

also what are your windows apps that u got working on ubuntu using Wine/Cedega.. kindly post pls.. sorry for my bad english.. thnx!

---

### Post by phanboy_iv on 2005-10-31
Right-click on the MP3 file, select "Properties" then the "Open With.." tab.

Then click on the "Add" button. Click on the "Use custom command" option at the bottom of the dialog box and type in the word "cedega" then the full pathname of the JetAudio executable. Like this: 




> cedega /whatever/blabla/jetaudio.exe

Finally, click the add button. 

That's a bit long, but I think it should work. Oh, and just substitute "wine" for "cedega" if you want to use that instead.

Oh, and you could just set up Rhythmbox or Totem or etc...to play mp3's. It's not hard. Do a forum search.

Starcraft is the only Windows app that I _need_ in Ubuntu. Cedega works a little better for that than Wine, but not a whole lot better....

EDIT: Oh, and you may need to go back into Properties->Open With and select your custom command from the list.

---

### Post by GQed76 on 2006-01-04
I love Jet audio and its the one thing i miss from windows...

How did you get it to work in Cedega..ive not had luck

---

