---
title: "Where is my shutdown button"
date: 2013-10-22
forum: Desktop Environments
---

### Post by cash1981 on 2013-10-22
When I upgraded to Ubuntu 13.10 my shutdown button from the top right menu is gone.
I can't find it anywhere.

So I cant logout, restart og shutdown without using the terminal.

Any ideas?

---

### Post by Frogs Hair on 2013-10-22
Open the dconf editor  > apps > indicator session make sure it is not suppressed. Next try the following command and logout - in or restart. ```
sudo apt-get install --reinstall indicator-session 
```

---

### Post by dvanzo on 2013-10-23
Reinstalling indicator-session did the trick for me!! Thanks so much!

Regards,

Daniel

---

### Post by cash1981 on 2013-10-24
> **Frogs Hair said:**
> Open the dconf editor  > apps > indicator session make sure it is not suppressed. Next try the following command and logout - in or restart. ```
sudo apt-get install --reinstall indicator-session 
```

Thanks.

Had to reinstall to make it work.

---

### Post by garyzw on 2013-10-29
I have the same problem. The shutdown indicator will go missing. I use ctrl+alt+del to log out and back in and the indicator is back.
Would reinstalling the indicator fix that problem?

---

### Post by vanadium on 2013-10-29
No. There is an issue with indicators in Ubity. Most typically, the datetime indicator sometimes does not appear after booting. Once i had both datetime *and* session indicator missing. It is a random problem. On a next reboot (or perhaps even logout/login), they are back. An issue that is know, fixed, and about to land in our  systems any time soon (currently in "proposed").

---

### Post by Frogs Hair on 2013-10-29
This has been recurring with mainly upgrades since 12.10 or so. I did receive  indicator-session and gnome-control-center date time updates from the proposed repository Monday 10-28.

---

### Post by JTPete on 2013-11-01
Thank you Frogs Hair, I just had this problem and your solution worked first try.

---

### Post by vanadium on 2013-11-01
Just loging out and loging in may also "fix" this. I thaught a fix would have been pushed with an update today, but I still had a missing indicator today.

---

