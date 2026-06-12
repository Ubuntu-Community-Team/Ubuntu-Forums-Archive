---
title: "Visual Boy Advance, VBA Express, and the Pokemon games!"
date: 2007-08-10
forum: Gaming &amp; Leisure
---

### Post by BigSilly on 2007-08-10
Hi there, can anyone help me out a little?

I've downloaded the GBA emulator Visual Boy Advance from Ubuntu's repos, and also the GUI for it called VBA Express. I'm having a bit of bother with the Pokemon games...

I'm not sure why, but Pokemon Ruby and Sapphire won't load up. I've obtained the GBA.BIOS file for the emu, but it's made no difference. All I'm getting is a white screen when I try to load up the games. I'm getting the ROM from a very reliable source, but no joy. Can anyone help?

Also, I'm trying to play Pokemon LeafGreen, which seems to load and play fine, but I cannot save the game. It just keeps saying "error saving". Is there anything I can do?

Thanks in advance (no pun intended). :)

---

### Post by Zylar on 2007-08-10
Make sure that under the 'Other' tab that RTC is checked.  Most Pokemon games require the realtime clock.  As far as the save error goes, that I'm not sure of.

Good luck,

Edit: [Here's]("http://forums.ngemu.com/visualboy-advance-discussion/51349-when-i-play-pokemon-fire-red-leaf-green-wont-save.html")  a link that might help with the LeafGreen.

---

### Post by BigSilly on 2007-08-10
Thanks for your reply. I've now got this emu on my Windows XP. It's exactly the same apart from a different front end, and I've got these games working fine there. It seems that the VBA Express GUI is missing some options, including the save options. It looks like I need to change the save options to "flash 128k" but I'm not sure how to do this in the terminal. Can you offer any advice?

Thanks again.

---

### Post by Zylar on 2007-08-11
Looks like the '--flash-128k' switch will enable 128k flash saves.

I opened a terminal and just typed 'vba' and it gave me all the options.

Good luck,

---

### Post by BigSilly on 2007-08-11
I've sorted it now. Thanks for your help Zylar, you're a star.

I found the visualboyadvance.cfg text file in the file searcher and made some adjustments. I set the save type to 128k, and also set it to automatic type save. I then saved this as a file and selected import a configuration in the VBA Express GUI. I imported the settings. Then I made sure that rather than using the US roms (denoted by a U), I got a hold of the European versions (denoted by an E). This seems to have done the trick wonderfully. 

I have posted this up in the hope that anyone with this problem in the future will find this after a search. Hopefully this will help them out.

Thanks again. :)

---

### Post by Zylar on 2007-08-11
My pleasure.

Glad you got it all worked out.  

Have fun, the poke games are great, even for an old fart like me.

---

### Post by rbprogrammer on 2007-08-11
> **Zylar said:**
> My pleasure.

Glad you got it all worked out.  

Have fun, the poke games are great, even for an old fart like me.

i have a question, i want to play the older pokemon games, like the red, blue i think there was a green, the yellow, gold, and silver, etc...

**would those work on visualboyadvance??**  also, i have not installed it yet, but where do i get the ROMs?  do they come with the emulator??

---

### Post by hikaricore on 2007-08-11
> **rbprogrammer said:**
> but where do i get the ROMs?  do they come with the emulator??

**Do not ask about illegal rom/movie/software downloads on Ubuntu Forums.**
I believe your question was innocent, so search google and mention nothing more of it here.

---

### Post by rbprogrammer on 2007-08-11
whoops #-o

i didnt realize that they could of been *illegal*, i just figured that some games might of came with the emulator.

sorry about that..

---

### Post by hikaricore on 2007-08-11
> **rbprogrammer said:**
> whoops #-o

i didnt realize that they could of been *illegal*, i just figured that some games might of came with the emulator.

sorry about that..

No worries, there's a fine line between what is legal and not legal.
While we're not going to try and tell you what to do on your own system, we can't be party to any such activity.
It's just safer for everyone and the community to steer clear of it as there are other sites for such information and discussions.

---

