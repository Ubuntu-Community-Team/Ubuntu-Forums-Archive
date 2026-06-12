---
title: "Machinarium retail version Linux installation"
date: 2011-04-05
forum: Gaming &amp; Leisure
---

### Post by Virus666 on 2011-04-05
Hi all,

**Machinarium** is a **Flash** based adventure game which was developed by **Amanita Design**. The game natively supports **GNU/Linux**, **MAC OS X** and **Windows**; moreover downloadable versions are on the way for **PlayStation 3**  and **Wii**.

[IMG]http://ismailhatip.files.wordpress.com/2010/10/290942-machinarium-per-pc-not_so_big.jpg[/IMG]

[IMG]http://img.bolumsonucanavari.com/images/e41de9b1-b220-4151-91f9-5e826e0ce8c3.jpg[/IMG]

However, after **Mamba Games** released the **retail** version of Machinarium, it appears that they removed the **Linux** files (inculuding the executable file) from the CD. For example; the contents of the CD that have are just **Install-Machinarium.exe** and the soundtrack folder...

[http://machinarium.net/forum/index.php?topic=1107.0](http://machinarium.net/forum/index.php?topic=1107.0)


Here is the method to install and play Machinarium retail version natively:


[LIST]
[*]Download Machinarium **Patch 01** for Linux: [http://machinarium.net/patch/Machinarium_patch01_en.tar.gz](http://machinarium.net/patch/Machinarium_patch01_en.tar.gz)
[*]Download Machinarium **Patch 02** for Linux and Mac: [http://machinarium.net/patch/Machinarium_patch02.zip](http://machinarium.net/patch/Machinarium_patch02.zip)
[*]Run the **Install-Machinarium.exe** file with **Wine** and install the game.
[*]Create a new folder in your **Home** folder and name it as **Machina** (or else you like).
[*]Open **~/.wine/drive_c/Program Files/Machinarium** folder and copy following folders to the **Machina** folder: **00**, **01**, **10**, **11**
[*]Patch 01: Copy and rewrite the files in **10**, **00** to the suitable folders in Machina.
[*]Patch 01: Copy **Machinarium** file to the Machina.
[*]Patch 02: Copy and rewrite the files in **00** to the suitable folder in Machina.
[/LIST]
[http://amanita-design.net/blog/2009/10/29/machinarium-patch-01/](http://amanita-design.net/blog/2009/10/29/machinarium-patch-01/)
[http://amanita-design.net/blog/2009/11/29/machinarium-patch-02/](http://amanita-design.net/blog/2009/11/29/machinarium-patch-02/)

You can start the game by double clicking the Machinarium file in Machina folder. Previous Machinarium installation is not required anymore; you can uninstall it via Wine safely.

**Note**: Do not forget to turn off **Flash Player**'s hardware accelaration in the game: [http://www.macromedia.com/support/documentation/en/flashplayer/help/help01.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/help01.html)

That's all. That method is applied for the retail versions which do not have required Linux files. The copy of the games which supports Linux do not need that method.

Enjoy... :guitar:

---

### Post by ElSlunko on 2011-04-05
My girlfriend and I played this game together. Had a great time figuring out the Puzzles. We both wish there was a part 2, we'd buy it in a heartbeat.

---

### Post by f1tz on 2011-04-09
I wasnt aware that you had to use wine to play it!? Odd... it being Flash and all. I've only played the demo, quite enjoyed that. You can download it from here, should you wish to try before buying: [http://www.bigdownload.com/games/machinarium/pc/machinarium-demo-linux/](http://www.bigdownload.com/games/machinarium/pc/machinarium-demo-linux/)

---

### Post by PhillyPhil on 2011-05-27
Thanks very much Virus!!! :)

---

### Post by X-jo on 2012-04-01
thanks.. this worked like a charm

---

### Post by Virus666 on 2012-04-22
> **f1tz said:**
> I wasnt aware that you had to use wine to play it!? Odd... it being Flash and all. I've only played the demo, quite enjoyed that. You can download it from here, should you wish to try before buying: [http://www.bigdownload.com/games/machinarium/pc/machinarium-demo-linux/](http://www.bigdownload.com/games/machinarium/pc/machinarium-demo-linux/)

You do not require Wine to play the game. I used Wine to unpack exe file. Normally, the game is compatible with GNU/Linux. However, some retail versions of the game do not contain Linux executables. That is why I used Wine to unpack exe file. Then I applied Linux patches and the game works without Wine. And yes, this is a Flash game.

---

