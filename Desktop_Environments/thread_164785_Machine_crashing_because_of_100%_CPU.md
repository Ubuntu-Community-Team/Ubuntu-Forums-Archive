---
title: "Machine crashing because of 100% CPU"
date: 2006-04-23
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-04-23
Hey, I have my computer crashing almost every day.

Lately I noticed that when doing certain things (like: converting audio files, for example), my CPU is constantly at 100%. That's when my computer crashes (after a while)

Attached is a screenshot that shows that Xorg is to blame. It ain't always Xorg, but in this case the machine crashed some 15 seconds after taking the screenshot.

What shall I do?

---

### Post by kingmonkey on 2006-04-23
Have you checked your ram?

---

### Post by dmizer on 2006-04-23
actually, i don't think xorg is to blame per se.  xorg is just trying to catch up because some process is overrunning the ram.

in my case, the problem was that gaim was flooding my ram.  same issue.  xorg showed 100% cpu usage in the system monitor, but when i looked in top to see what else was going on, there were multiple instances of gaim all taking up a piece of memory.

if you use the ubuntu distributed version of gaim, i highly reccomend you upgrade to gaim2, and that may solve your problem.

---

### Post by GabrielWolff on 2006-04-23
[QUOTE=kingmonkey]Have you checked your ram?[/QUOTE]

No. How do I do that? What should I check there?

As to gaim: At the Prosessor window I coulcn't find any program called *gaim* running. Don't know what it is neither. Was I looking at the wrong place?

Thanks

G

---

### Post by dmizer on 2006-04-24
at boot, press the key to get into the grub menu and select the option for memory test ... memory86+ or some such (can't remember off the top of my head, but it should be obvious once you get into the grub menu).

bear in mind, a full memory test will take hours and hours.

---

### Post by GabrielWolff on 2006-04-24
[QUOTE=dmizer]at boot, press the key to get into the grub menu and select the option for memory test ...[/QUOTE]

I lost you here:

1) Which "*key to get into the grub*"?
2) What should a memory test reveal? What's wanted? What should catch my eye?

Maybe the easiest is to refer me to some HOWTO or so. I just don't even know what to look for...

Thanx

G

---

### Post by Ramses de Norre on 2006-04-24
You'll need to press esc if grub menu is disabled. In grub choose memtest86+ and it will check you're ram, see if it tells you anything about corrupt ram.

---

### Post by GabrielWolff on 2006-04-24
[QUOTE=Ramses de Norre]You'll need to press esc if grub menu is disabled. In grub choose memtest86+ and it will check you're ram, see if it tells you anything about corrupt ram.[/QUOTE]

Thanks. Last question: 
Can I copy and paste the output of such a test? Like: If it finds anything corrupt, I most probably will have to post the output here, as I hardly will understand anything of it...

G

---

### Post by eitan on 2006-04-24
for what it's worth: i recently upgraded from breezy to dapper 6.06 beta.  zeroconf goes to 100% cpu;  i kill it after boot up.  i'm sure i'll soon just uninstall or disable it.  or maybe a forthcoming update will fix this?

---

### Post by dmizer on 2006-04-25
[QUOTE=GabrielWolff]Thanks. Last question: 
Can I copy and paste the output of such a test? Like: If it finds anything corrupt, I most probably will have to post the output here, as I hardly will understand anything of it...[/QUOTE]
if the memory test finds something wrong, it means your memory is bad and will need to be replaced.  so it is not necessary to know what it means, just know if it passes or not.

---

### Post by GabrielWolff on 2006-04-26
[QUOTE=dmizer]if the memory test finds something wrong, it means your memory is bad and will need to be replaced.  so it is not necessary to know what it means, just know if it passes or not.[/QUOTE]

I see. Isn't there a possibility that the RAM is configured wrongly (or something like that. Correct me if thtis is a total newbie question)?

G

---

