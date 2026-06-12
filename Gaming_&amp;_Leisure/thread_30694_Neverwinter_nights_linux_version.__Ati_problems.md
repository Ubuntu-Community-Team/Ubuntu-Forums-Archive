---
title: "Neverwinter nights linux version.  Ati problems"
date: 2005-04-29
forum: Gaming &amp; Leisure
---

### Post by graigsmith on 2005-04-29
Hi I just installed my neverwinter nights, and shadows of undrentide expansion pack.

so i started playing online, and it works great, i get great framerates and everything -- for about 20 minutes.   Then the screen goes black or blueish.  and all the 3d dissapears.  i can still see the mouse cursor and the inventory, and use the inventory.   I can hear all the sounds.  if i exit the game, and re-enter, it works for about another 20 minutes. then the 3d stops again.

Apparently the opensource ati drivers work best for this. and thats what im using. the ones that came with ubuntu 5.04.  Also i opened all the ports required for NWN, and this error still happens.

i asked on the neverwinter nights message board, and got a "never seen that before" response.  So i'm asking here.

here are my system specs.

ATI radeon 9200
nforce 2 motherboard
AMD 2800+
1GB of ram.

edit, also i have no problems running quake 3, or enemy territory.  they both run flawlessly for hours :)  and the framerate is quite good at 800X600

---

### Post by Seth on 2005-04-29
[QUOTE=graigsmith]Hi I just installed my neverwinter nights, and shadows of undrentide expansion pack.

so i started playing online, and it works great, i get great framerates and everything -- for about 20 minutes.   Then the screen goes black or blueish.  and all the 3d dissapears.  i can still see the mouse cursor and the inventory, and use the inventory.   I can hear all the sounds.  if i exit the game, and re-enter, it works for about another 20 minutes. then the 3d stops again.

Apparently the opensource ati drivers work best for this. and thats what im using. the ones that came with ubuntu 5.04.  Also i opened all the ports required for NWN, and this error still happens.

i asked on the neverwinter nights message board, and got a "never seen that before" response.  So i'm asking here.

here are my system specs.

ATI radeon 9200
nforce 2 motherboard
AMD 2800+
1GB of ram.

edit, also i have no problems running quake 3, or enemy territory.  they both run flawlessly for hours :)  and the framerate is quite good at 800X600[/QUOTE]
 All I can say is try this: [http://ubuntuforums.org/showthread.php?t=30481](http://ubuntuforums.org/showthread.php?t=30481)

Worked for me.

---

### Post by graigsmith on 2005-04-29
i dont think thats the issue.  my whole system is not freezing. its never done that.  and the game doesn't crash, the 3d just stops working.  i am able to quit the game normally.   all i have to do is leave the multiplayer game, and then from the main menu i go back in, and the 3d works again.  but thats getting annoying.

---

### Post by graigsmith on 2005-05-01
[QUOTE=graigsmith]i dont think thats the issue.  my whole system is not freezing. its never done that.  and the game doesn't crash, the 3d just stops working.  i am able to quit the game normally.   all i have to do is leave the multiplayer game, and then from the main menu i go back in, and the 3d works again.  but thats getting annoying.[/QUOTE]
 i figured out what this was.  it was a BIOS setting.  i disabled spread spectrum for FSB and AGP.

now it works great for hours. :)

---

### Post by nautilus on 2005-05-02
good stuff :)

ati can be a real pain...  amazing hardware, great company, and pathetic driver support.

granted, you weren't using the fglrx drivers, but you probably would have been if you had heard they "worked best", right? ;)

i returned my radeon 9800 pro for an nvidia for this reason.  actually, the reason was the trouble ticket, followed by the late response "The ATI Linux drivers are unsupported.." stopped reading, shutdown, remove card, demanded full refund.

sorry, this was a rant huh :D

---

### Post by graigsmith on 2005-05-02
seems like as long as you use the open source drivers your fine.  but the open source drivers apparently only support 3d on some of the older cards.  so basically if i understand this right, dont get anything higher than a 9200 :(

---

