---
title: "Deleting some files on the Desktop, causes deleting files of the &quot;incoming&quot; folder."
date: 2007-04-03
forum: Desktop Environments
---

### Post by Filiprino on 2007-04-03
Hello, I'm going to explain this poltergeist...
I have some .png images on my Ubuntu Feisty Fawn Desktop, and I delete them. Then, after an hour, more or less, I want to acces my incoming folder, which is also on my Desktop, but... there is no incoming folder, it has disappeared. I go to the recycle bin, and find my incoming folder with the .png images there. Sooo.... I cut and paste the incoming folder back to the Desktop, I open it, open the subfolder "torrents" which Torrentflux uses, and... there are some files disappeared. Curiously, Torrentflux says it could not open stat file for the disappeared files which I was seeding (other files than those seeded disappeared too), but continues to be seeding them.

Now, the funniest thing. I cut and paste back to the Desktop from the recycle bin those .png images, and voilà, 2 of the 3 files (the third one didn't disappear) which I was seeding with Torrentflux came back to the torrents subfolder, but as empty files (1MB in size, when the full size is ~700MB) and the rest remain hidden or in a better place which I don't know where is...

This is one of those unexplicable facts, I think... :(

If you have any doubt about the message (I think I haven't explained it well...) please ask for more information if you need it :)

---

### Post by kidders on 2007-04-04
Hi there,

I'm not sure what you mean by "incoming folder", but the only way something could be turning up in your trash is if something explicitly moves it there (ie rather than deleting it).

> Torrentflux says it could not open stat file for the disappeared files"Cannot stat [filename]" is just another way of saying "The file is either not there, or some very low-level error has occurred, which is stopping me from examining it". If I were you, I would check the preferences of any running programs ... one of them is probably doing something you don't want it to.

By the way... 700MB PNG images?!! (Just curious.)

---

### Post by Filiprino on 2007-04-04
By the 'incoming' folder, I mean the folder where all my peer to peer programs save the downloaded files.

---

