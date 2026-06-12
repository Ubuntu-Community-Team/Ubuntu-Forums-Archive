---
title: "Quake 4"
date: 2010-02-10
forum: Gaming &amp; Leisure
---

### Post by eranga1988 on 2010-02-10
Can anybody give a link for Quake 4..???Can we play it as a single player???Thanx...

---

### Post by eranga1988 on 2010-02-10
And I want to know how to install it!!!

---

### Post by tommcd on 2010-02-10
> **eranga1988 said:**
> Can anybody give a link for Quake 4..???Can we play it as a single player???Thanx...
> And I want to know how to install it!!!
If you have the retail version of Quake4, then you need the linux installer from Id Software. You can get it here:
[ftp://ftp.idsoftware.com/idstuff/quake4/linux/](ftp://ftp.idsoftware.com/idstuff/quake4/linux/)
Use the quake4-linux-1.4.2.x86.run installer.
Then you need to copy all the *.pk4 files from your Quake4 CDs to /usr/local/games/quake4/q4base. Read through the Quake4 FAQ:
[http://zerowing.idsoftware.com/linux/quake4/](http://zerowing.idsoftware.com/linux/quake4/)
Just make the necessary directories:
```

sudo mkdir -p /usr/local/games/quake4/q4base 
```
Then copy the *.pk4 files from the Quake4 CDs to /usr/local/games/quake4/q4base. If you have trouble mounting the CDs, then see this:
[http://zerowing.idsoftware.com/linux/quake4/#head-55969ff8b38fad088ee915b4e7da3480efcf5046](http://zerowing.idsoftware.com/linux/quake4/#head-55969ff8b38fad088ee915b4e7da3480efcf5046)
Then run the Quake4 installer using sudo. After running the installer, it will ask you if you want to launch the game. Answer NO! If you launch it after running the installer, then you will need to launch the game using sudo. Correcting this is a royal PIA!
So answer no, then you can just run the game right from the terminal by running: **quake4**.
Note: Installing Quake4 like this will add about 2GB to your Ubuntu root directory. Make sure you have enough room for that.

You can also install Quake4 to your /home directory:
[https://help.ubuntu.com/community/Games/Native/Quake4](https://help.ubuntu.com/community/Games/Native/Quake4)
Write back if you need more help. 
There are lots of threads on the Ubuntu forums about Quake4.

---

