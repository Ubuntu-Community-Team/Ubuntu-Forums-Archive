---
title: "NWN no text, get's stuck"
date: 2013-03-04
forum: Gaming &amp; Leisure
---

### Post by remo88 on 2013-03-04
Hello all,

I am using the latest version of Lubuntu 64bit OS, and I am having problems with NWN.
I followed all available instructions online (bioware's sites and few others) and I got the game itself to work. But I seem to have a problem.
I don't see any text within the game main menu, and also when I try to start a campaign the entire game freezes which forces me to reboot the system.

I am using the latest AMD drivers. Please help =]

---

### Post by remo88 on 2013-03-04
Edit: I was able to fix the fonts problem, But I don't understand the cause of it.
the solution was to move the entire game folder to usr/share/games folder.
Can anyone explain why?

Another issue I am having is that movies don't work even after what the guide says.
Another issue I am having is that the game only runs via the sudo ./nwmain command. Otherwise I don't see text again, and if I try to run the ./nwn file then the game runs without sound.

---

### Post by oldrocker99 on 2013-03-04
Your problem is one I've never heard before; I have been running NWN for 5 years from my /home/oldrocker99/Games/nwn/ folder. I have never had any font problem at all.

You might try this:

sudo chown yourusername:yourusername /usr/share/games/nwn

Just to make sure that everything there belongs to you.

---

