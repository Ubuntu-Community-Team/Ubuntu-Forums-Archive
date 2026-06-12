---
title: "after update, uninstalled compiz and now have no desktop effects"
date: 2007-10-08
forum: Desktop Effects &amp; Customization
---

### Post by alwiap on 2007-10-08
A few days ago I got a pop-up saying updates were available. (NOTE: I didn't have compiz or beryl or anything of that nature installed, but I was just using the built in Ubuntu desktop effects available through System > Preferences, and I have no need for compiz etc.).  I installed the updates, and restarted, and the computer was slow as ****.  I opened up system monitor, and i saw that 'compiz-core' was taking up 50-60% of the processes.  So I ended the process, I lost my window borders, so i typed 'metacity --replace' in the terminal and everything was fine, but every time i would restart the computer it would be the same old.

So I went into synaptic package manager, and deleted compiz-core, which in turn deleted desktop-effects, and some other files.  Now the computer runs fine after I put 'metacity --replace' in Sessions > Startup Programs.

Since I like eye-candy, but am using my laptop which I don't deem capable of compiz, I would still like to have things as I did, with just the desktop-effects enabled.  However, every time I go to install that though synaptic package manager, it prompts me that compiz-core has to be installed, and obviously I don't want to do that because that puts me back to square 1. 

Could it be that i have some repos enabled that keep wanting to get compiz?  I really have no clue as I only a month into Ubuntu.  Again, my laptop is running fine but w/out desktop-effects, I would like them enabled but no compiz.  

Thanks so much for reading.

---

### Post by ThrobbingBrain66 on 2007-10-08
Those desktop effects you like so much ARE compiz.  You can always try reinstalling all compiz-related packages.  As a last option you could use Trevino's 3rd party Compiz repo for Feisty or wait 10 days for Gutsy to be released.  Compiz Fusion is default in Gutsy and has many bug fixes and improvements over Feisty's Compiz.

---

