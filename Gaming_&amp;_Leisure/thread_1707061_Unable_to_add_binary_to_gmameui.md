---
title: "Unable to add binary to gmameui"
date: 2011-03-14
forum: Gaming &amp; Leisure
---

### Post by fubeca6 on 2011-03-14
Please Help:

 I have both xmess and xmame files (binaries?) in my /usr/games/ directory. However,  I open GMAMEUI and go to Options>Directories..., then I click ADD (referencing MAME Executables) I find /usr/games/ and click the mame/xmess files - I've tried all of them: xmame, xmame.SDL, xmame.x11, xmess, and xmess.SDL. Nothing happens. Nautilus closes, but no directories are displayed in the box. 

When I click "Close" it pops up, saying "No MAME Executables Have Been Chosen: Without a MAME executable, you will not be able to emulate any ROMs. Are you sure you want to close the window?"

I've searched the forums and not found anything that solves this problem, including editing the /[username/.config/gmameui/gmamui.ini file. But nothing yet has worked :(  Sad days.

---

### Post by disturbedite on 2011-03-14
my recommendation: [http://ubuntuforums.org/showpost.php?p=9550787&postcount=2](http://ubuntuforums.org/showpost.php?p=9550787&postcount=2)

---

### Post by fubeca6 on 2011-03-14
> **disturbedite said:**
> my recommendation: [http://ubuntuforums.org/showpost.php?p=9550787&postcount=2](http://ubuntuforums.org/showpost.php?p=9550787&postcount=2)


Thanks for the reply! I hadn't seen that post before. It kinda strikes me as strange though, just because I read a post earlier that said NOT to use sdlmame, and to use xmame instead :S  

O well! I will try sdlmame when I get home! Thanks again for the reply!

---

### Post by fubeca6 on 2011-03-15
SOLVED: It helps if you have write permissions to GMAMUI

$cd /usr/games
$sudo chmod 770 gmameui
$sudo chmod 770 mame

Then was able to add the directories. I swear, I'm such a noob sometimes :(

---

### Post by disturbedite on 2011-03-15
> **fubeca6 said:**
> Thanks for the reply! I hadn't seen that post before. It kinda strikes me as strange though, just because I read a post earlier that said NOT to use sdlmame, and to use xmame instead :S 

no problem.
i suppose the only the way that would be true is if one wants to use old, antiquated software (like frontends).

---

