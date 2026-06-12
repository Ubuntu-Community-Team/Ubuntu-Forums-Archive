---
title: "NeoDS we need a converter for linux"
date: 2008-05-01
forum: Gaming &amp; Leisure
---

### Post by Wobedraggled on 2008-05-01
[http://groups.google.com/group/neods/]("http://groups.google.com/group/neods/")

Let's you play Neogeo games on your DS, but the converter is for windows,  but source is included.

Can someone with some know how get this ported for us?

Much appreciated.

---

### Post by Wobedraggled on 2008-05-02
bump, someone else must wanna try this out

---

### Post by GSZX1337 on 2008-05-02
Is this app similar to PocketNES?

---

### Post by Wobedraggled on 2008-05-02
> **GSZX1337 said:**
> Is this app similar to PocketNES?


It's an emulator, plays neogeo games.

---

### Post by Grishka on 2008-05-02
what exactly seems to be the problem?

---

### Post by Wobedraggled on 2008-05-02
> **Grishka said:**
> what exactly seems to be the problem?


The conversion software only works in windows, but source is included. I was wondering if someone could get it working for the people without windows.

---

### Post by Grishka on 2008-05-02
you can try to compile it yourself. you'll need devkitARM, libfat and libnds from here: [http://sourceforge.net/project/showfiles.php?group_id=114505](http://sourceforge.net/project/showfiles.php?group_id=114505)

---

### Post by k33bz on 2008-05-02
> **Grishka said:**
> you can try to compile it yourself. you'll need devkitARM, libfat and libnds from here: [http://sourceforge.net/project/showfiles.php?group_id=114505](http://sourceforge.net/project/showfiles.php?group_id=114505)

can i use devkitpro to recompile games to work in linux?

---

### Post by Wobedraggled on 2008-05-02
> **Grishka said:**
> you can try to compile it yourself. you'll need devkitARM, libfat and libnds from here: [http://sourceforge.net/project/showfiles.php?group_id=114505](http://sourceforge.net/project/showfiles.php?group_id=114505)



I dont need the .nds file converted I need the file that converts the roms and bios into a.neo file.

---

### Post by Grishka on 2008-05-02
> **Wobedraggled said:**
> I dont need the .nds file converted I need the file that converts the roms and bios into a.neo file.

if you mean NeoDsConvert, you can run it with Wine. I had to install Microsoft Visual C++ from here: [http://www.microsoft.com/downloads/thankyou.aspx?familyId=32bc1bee-a3f9-4c13-9c99-220b62a191ee&displayLang=en](http://www.microsoft.com/downloads/thankyou.aspx?familyId=32bc1bee-a3f9-4c13-9c99-220b62a191ee&displayLang=en) to get it to run, though.

---

### Post by Wobedraggled on 2008-05-02
> **Grishka said:**
> if you mean NeoDsConvert, you can run it with Wine. I had to install Microsoft Visual C++ from here: [http://www.microsoft.com/downloads/thankyou.aspx?familyId=32bc1bee-a3f9-4c13-9c99-220b62a191ee&displayLang=en](http://www.microsoft.com/downloads/thankyou.aspx?familyId=32bc1bee-a3f9-4c13-9c99-220b62a191ee&displayLang=en) to get it to run, though.

And knowing is half the battle, excellent news. I'll give that a go when I get home, a native version still wouldn't hurt.

---

### Post by theschlubb on 2008-12-18
I'm not sure if this thread is dead, or nobody found the solution.  I have found a way to make NeoDSConvert work with all games.  You don't need to install Microsoft Visual C++.  All you need are the three .dll files and the .manifest to get it working.  You can get the .zip for them here: [**http://www.sweetpotatosoftware.com/files/microsoft.vc80.crt.zip**]("http://www.sweetpotatosoftware.com/files/microsoft.vc80.crt.zip").  Put the files from the .zip into your work directory and voilà!  I also included uni-bios.rom into my neogeo.zip.  That gives you the ability to play the home version with all the extra options.  You can get the universal bios from: [**http://unibios.free.fr/download/uni-bios-22.zip**]("http://unibios.free.fr/download/uni-bios-22.zip").  Hope this helps anyone that is stuck trying to convert .bin neogeo roms to .neo using NeoDSConvert and wine.

---

