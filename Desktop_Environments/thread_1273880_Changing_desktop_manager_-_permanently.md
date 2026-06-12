---
title: "Changing desktop manager - permanently"
date: 2009-09-23
forum: Desktop Environments
---

### Post by SPARTAN-118 on 2009-09-23
Hi all, SPARTAN-118 here.

Just like to know how to change the window manager - permanently - so that I don't have to switch it using Alt+F2 and type "emerald --replace" every time I log in. I tell you, it's a real pain in the ***** to have to switch this **every single time I start my computer...**

And yes, I use Compiz+Emerald for my windows/desktop effects. 
I can't find good enough Metacity borders.

---

### Post by renkinjutsu on 2009-09-24
system/preferences/startup applications

just add your command there and check the box for your task


or, you can get rid of gdm and have your own .xinitrc

---

### Post by mcduck on 2009-09-24
> **SPARTAN-118 said:**
> Hi all, SPARTAN-118 here.

Just like to know how to change the window manager - permanently - so that I don't have to switch it using Alt+F2 and type "emerald --replace" every time I log in. I tell you, it's a real pain in the ***** to have to switch this **every single time I start my computer...**

And yes, I use Compiz+Emerald for my windows/desktop effects. 
I can't find good enough Metacity borders.

If you want to use Emerald as the default decorrator for Compiz, just change the setting in CompizConfig Settings Manager, under Window Decoration-plugin's settings. There's an option for telling what decorator Compiz shuld load by default, just change that to "/usr/bin/emerald".

(If you just add "emerald -replace" to Gnome's startup, you'll end first starting GWD and then replacing it with Emerald, when you could just load the correct decorator in the first place.)

---

### Post by SPARTAN-118 on 2009-09-24
> **mcduck said:**
> If you want to use Emerald as the default decorrator for Compiz, just change the setting in CompizConfig Settings Manager, under Window Decoration-plugin's settings. There's an option for telling what decorator Compiz shuld load by default, just change that to "/usr/bin/emerald".

(If you just add "emerald -replace" to Gnome's startup, you'll end first starting GWD and then replacing it with Emerald, when you could just load the correct decorator in the first place.)

Ok, thanks I think that worked!

BTW how do you add [SOLVED] to the actual thread title? Change the prefix? How do you do that to an already-created thread?

NVM didn't see Thread Tools... 

Thanks!

---

