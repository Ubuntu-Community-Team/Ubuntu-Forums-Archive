---
title: "Open/Find battery file (.sav) from vba express with vba-m"
date: 2018-06-11
forum: Emulators
---

### Post by michisaurio on 2018-06-11
Hi,

I installed Visual Boy Advance Express in my Ubuntu 16.04 LTS (64 bits) machine some time ago, and I have been playing Pokemon Crystal without any problems. Now I would like to continue playing with another emulator: vba-m, since it offers more options.

My problem is that when I try to open the .gbc file with vba-m, a new .sav file is created in the same folder, and the game starts from the beginning as if it was the first time.

When I played with vba express, no .sav file was created in that folder because I did not specify any path for save state or battery. I am new to emulators, and I did not know that it might be a good idea to specify a path.

I have performed an experiment where vba express saves the .sav file in the current folder. Then it is possible to continue playing with vba-m.

I assume/suppose that the .sav file for my original game was saved somewhere by vba express. But I haven't managed to find it. In the VisualBoyAdvance.cfg file it is written that "# Directories. Not setting one them makes the file go the rom directory." (sic). But as I mentioned above, no .sav file is saved in the folder of the .gbc file when I open my original game with vba express.

I have found almost none documentation for the vba express, and I have been reading different forum threads, but without any results.

Does somebody know where vba express saves the .sav file by default?

Is there a way to go around and open this file with vba-m?

Thanks in advance

P.D: By the way, I use vba-m with wine, but I don't think this is the cause of the problem.

---

### Post by howefield on 2018-06-11
Thread moved to the "*Emulators*" forum.

---

### Post by michisaurio on 2018-06-21
Solved. Using [https://askubuntu.com/questions/89393/how-to-search-entire-hard-drive-for-a-file](https://askubuntu.com/questions/89393/how-to-search-entire-hard-drive-for-a-file) , I found the location of the .sav file.

---

