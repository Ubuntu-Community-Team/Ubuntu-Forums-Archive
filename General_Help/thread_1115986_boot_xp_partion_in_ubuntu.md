---
title: "boot xp partion in ubuntu?"
date: 2009-04-04
forum: General Help
---

### Post by kristen89 on 2009-04-04
is it possible to boot the xp partion inside ubuntu 9.04?

if so will i still be able to boot xp normaly?

id like to do this so i can access files and things alot easier instead of restarting every 4 min... and i really dont wanna have to reformat xp jsut to get it to work! 

ive reformat a total of 36 times this week -.-"

forgot to mention... i already have xp and ubuntu installed on my system

---

### Post by coffeecat on 2009-04-04
> **kristen89 said:**
> id like to do this so i can access files and things alot easier instead of restarting every 4 min

If you're running 8.04 (Hardy) or 8.10 (Intrepid), you have full read-write to your Windows partition already. You just have to mount it.

From the Main Menu (top left) click on Places. Have a look in there. I'm posting from Jaunty so I can't remember whether the layout is different in Hardy/Intrepid, but what I can see when I hover my mouse over 'Removable Media' is my Windows partition which I can click on and a file manager window opens.

Alternatively, click on 'Computer' and double-click on the Windows partition icon that you'll see in the 'Computer' file browser.

---

### Post by SBDxAric on 2009-04-04
You can use virtual box to run xp from inside Ubuntu :)

Try this guide:
[URL="http://seogadget.co.uk/the-ubuntu-installation-guide/"]this guide
[/URL]
The part you need to use is towards the bottom

---

### Post by 3Miro on 2009-04-04
IF you just need to see files (Documents Pictures and such), you can mount the XP partition (go to places and it should be lited there).

Otherwise you can run a Virtual Machine, however, not all programs run from within a virtual machine (3d games for example don't run).

---

### Post by kristen89 on 2009-04-04
im running 9.04 beta >.< is there a way for that ?

i can view the files already, i would liuke to boot and run windows within ubuntu ^ ^

---

### Post by 3Miro on 2009-04-04
Virtual Machine (i.e. Virtual Box, which is free, or VM ware, which is not free).

For Virtual Box, I would advise to first install a new copy of XP and check to see if the programs that you need are running.

---

### Post by kristen89 on 2009-04-04
i guess i can transfer my music files to my ubuntu folder then delete the windows partion and use virtualbox to boot xp :(  i love mediamonkey thoe which is why i am still useing windows xp :D

---

### Post by coffeecat on 2009-04-04
It looks as though [MediaMonkey will run under Wine]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=15795").

If you don't know what Wine is, basically, you run Wine in Ubuntu/Linux, and you run your Windows app in Wine. Install Wine with Synaptic. It doesn't work for all Windows apps, but you might be in luck for MediaMonkey. Give it a try. :wink:

---

### Post by kristen89 on 2009-04-04
> **coffeecat said:**
> It looks as though [MediaMonkey will run under Wine]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=15795").

If you don't know what Wine is, basically, you run Wine in Ubuntu/Linux, and you run your Windows app in Wine. Install Wine with Synaptic. It doesn't work for all Windows apps, but you might be in luck for MediaMonkey. Give it a try. :wink:

ive tried that and failed... twice .... >.> it ran slower then it does on xp 

i also wanna keep windows xp for my music cause it is alot easier to organise my music libary ... i listen to music 24/7 so i must be able to organise 20 thousands songs easily :)

but then again i like ubuntu casue it doesnt get infected by every site i go too >.> unlike windows everysite has some kind of virus in it.. so it seems.... :)

so getting it to boot somehow in ubuntu would be awsome!

also if i install xp within virtualbox would i be able to get my soundcard drive in it?

---

