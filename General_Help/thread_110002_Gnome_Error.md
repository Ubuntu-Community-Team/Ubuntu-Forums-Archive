---
title: "Gnome Error"
date: 2005-12-29
forum: General Help
---

### Post by Tmyers on 2005-12-29
Alright, while browsing myspace (I know,I know the horribly coded myspace) I entered a profile and the computer went semi-frozen. (I could move the mouse around but it was really glitchy) So I restarted gnome  through the keyboard. I don't know what happened next because I walked away from the computer but when I returned it was at the gnome login screen. When I tried to login I get this error:

**Your session only lasten less than 10 seconds.  If you have not logged out yourself this could mean that there is some installation problem or that you may be out of diskspace. Try loging in with one of the failsafe methods to see if you can fix this problem.**

Does anybody know what happened? I would hate to have to reinstall everything because "gnome got myspaced to death". There is no way im out of disk space, Ive only had the ubuntu installation for about a week and a half now, and I haven't added a windows partition yet. 

Your help is appreciated, I can't use my computer until this is resolved.

---

### Post by narcolept on 2005-12-29
Log in by selecting failsafe terminal in GDM, and look at dmesg and some other logs to see if you see an error, it could besomething as simple as permissions on /home/user/.ICEauthority.

---

### Post by Tmyers on 2005-12-29
Ive pulled up dmesg and am looking through it now. Theres a bit to go through and Im not that confident with the terminal yet. Ive only had about a week and a halfs experience with it. Anything in particular I should be looking at?

---

### Post by Tmyers on 2005-12-29
You were right. It was a .IceAuthority problem. I just ran "sudo chown tj .ICEauthority" where tj is my username. Thanks for suggesting that I look into the "permissions on /home/user/.ICEauthority."

---

