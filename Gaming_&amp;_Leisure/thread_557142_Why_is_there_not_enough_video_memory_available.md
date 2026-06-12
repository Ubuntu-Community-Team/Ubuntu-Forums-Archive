---
title: "Why is there not enough video memory available"
date: 2007-09-22
forum: Gaming &amp; Leisure
---

### Post by secret_force on 2007-09-22
I installed Settlers (a demo) fine on my gutsy computer with help of wine 9.45. However, if I try to start Settlers I get the following fatal error:

> Graphics adapter does not meet minimum requirements.

At least 70 MB of available video memory required, only 57 MB detected.


How is this possible... I have a nvidia 7900GS VGA with 256 MB video memory...what can i do to solve the problem??

---

### Post by hikaricore on 2007-09-22
I'm not sure about the error, but is this the game you're attempting to run: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=5643](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5643)
Knowing the game in question may give other forum members a better idea of how to help  you.  ^_^

Be aware that not all ***dows titles will run via WINE

---

### Post by Sockerdrickan on 2007-09-22
You can set vidmem in regedit

---

### Post by cogadh on 2007-09-22
By default, Wine sets your video memory at 64 MB. As Tux0r said, you can make a regedit that will set it to the correct video memory ammount:
[LIST=1]
[*]Run "regedit" in a terminal
[*] go to HKEY_CURRENT_USER/Software/Wine and create a new Key named "Direct3D"
[*]In the new Direct3D key, create a new String Value named "VideoMemorySize"
[*] Change the value of the String to your actual video memory size
[/LIST]

---

### Post by disturbedite on 2007-09-22
i did this and it caused some games not to run.  (like blizzard games).  i don't know why.  i forget why i tried it in the first place, but there must have been a reason.  i realize it may not matter at all any way cuz all i have is a 64MB integrated video chip & use the intel driver.  (intel i845g)

---

### Post by secret_force on 2007-09-22
> I'm not sure about the error, but is this the game you're attempting to run: [http://appdb.winehq.org/objectManage...ation&iId=5643](http://appdb.winehq.org/objectManage...ation&iId=5643)
Knowing the game in question may give other forum members a better idea of how to help you. ^_^

Yes that is the game i'm talking about.


> By default, Wine sets your video memory at 64 MB. As Tux0r said, you can make a regedit that will set it to the correct video memory ammount:

   1. Run "regedit" in a terminal
   2. go to HKEY_CURRENT_USER/Wine and create a new Key named "Direct3D"
   3. In the new Direct3D key, create a new String Value named "VideoMemorySize"
   4. Change the value of the String to your actual video memory size


Thanks very much...it worked, the game starts, the ubisoft movie...even the menu (settings). However the game itself is black.  I will show you in a screenshot

---

### Post by cogadh on 2007-09-22
According to the Wine AppDB page for the demo, you need to turn off shader effects in the game's settings to get rid of the black screen problem.

EDIT - Hey, I just noticed I made an error when detailing how to make that registry edit. The Key is actually HKEY_CURRENT_USER/**Software**/Wine, not HKEY_CURRENT_USER/Wine. Since it worked for you, I am assuming you caught my mistake and adjusted for it. I've fixed the original post in case anyone else makes use of it.

---

### Post by secret_force on 2007-09-23
> **cogadh said:**
> According to the Wine AppDB page for the demo, you need to turn off shader effects in the game's settings to get rid of the black screen problem.

EDIT - Hey, I just noticed I made an error when detailing how to make that registry edit. The Key is actually HKEY_CURRENT_USER/**Software**/Wine, not HKEY_CURRENT_USER/Wine. Since it worked for you, I am assuming you caught my mistake and adjusted for it. I've fixed the original post in case anyone else makes use of it.

YES it worked again...thanks very much...

Yeah, if found out myself that the key was in a different directory... but that wasn't very hard ;)

---

