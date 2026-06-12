---
title: "Consequences of forcing shutdown"
date: 2009-03-13
forum: General Help
---

### Post by acimmarusti on 2009-03-13
Hi,

I installed warcraft 3 on wine 1.0.1 and it caused my screen to freeze when I tried starting the game. I had to force shutdown (twice!). How bad is that? should I run some tool to make sure my computer is fine and won't crash in doing some other task?

Thanks

---

### Post by Locutus_of_Borg on 2009-03-13
you can usually safely perform a forced reboot by holding the Alt ad SysRq keys, then typing r-e-i-s-u-b 

if you are concerned,

sudo touch /forcefsck

will force a file system check on next boot

---

### Post by Bapabooiee on 2009-03-13
My guess would be it shouldn't have *too* much of an impact. It does look like the operating system still shuts-down relatively peacefully to me.

Though, I don't know if it signals all running processes to close, or if it just immediately terminates all running processes. Either way, it kinda seems in a hurry to shut-down, I suppose.

---

### Post by DeMus on 2009-03-13
> **Locutus_of_Borg said:**
> you can usually safely perform a forced reboot by holding the Alt ad SysRq keys, then typing r-e-i-s-u-b 

if you are concerned,

sudo touch /forcefsck

will force a file system check on next boot

One question: which key is the SysRq key? There is no key with this text on my keyboard.

---

### Post by Locutus_of_Borg on 2009-03-13
on my laptop it shares the same key as Delete

i dont know where yours might be

---

### Post by DeMus on 2009-03-13
> **Locutus_of_Borg said:**
> on my laptop it shares the same key as Delete

i dont know where yours might be

I have no idea. Could it be the Pause/Break key?

---

### Post by Locutus_of_Borg on 2009-03-13
find it through trial and error?

---

### Post by Bapabooiee on 2009-03-13
On my keyword, the "SysRq" key is shared with the "Prnt Scrn" key.

I'd recommend just looking around that general area of the keyboard and see if you can find it.

---

### Post by scphan on 2009-03-13
in comparison to windows, forcing the shutdown to my ubuntu computer doesn't seem to have any obvious consequences, it justs starts back up and running as smoothly as before everything went wrong.  

windows on the other hand takes about a day or two to recover for me and sometimes makes me feel that the data integrity on disk decreases everytime i have to force a shutdown

just to be safe make sure you're not in the process of saving something to disk or an external device or emptying the trash when you know you'll might need to force a shutdown

running a file system check on boot should be fine for checking your data integrity after a force shutdown

---

