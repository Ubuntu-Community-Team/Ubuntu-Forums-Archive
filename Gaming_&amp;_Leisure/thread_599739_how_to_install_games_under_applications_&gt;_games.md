---
title: "how to install games under applications &gt; games"
date: 2007-11-01
forum: Gaming &amp; Leisure
---

### Post by dhabell@yahoo.com on 2007-11-01
I have d/l a game I would like to install so I can open it when I go to applications > games.  Currently it is saved to my desktop as a tar.gz file.

also same question for another game but it has two parts.  They are .deb files.  The have the same file name but one has "data" in the file name and one does not.

Would you give me very easy instructions as I just installed linux for the first time and dont know what Im doing.  Although Im getting better with the terminal, I prefer to have instructions on how to do it both ways.  thanks

---

### Post by shad0w_walker on 2007-11-01
The .tar.gz file could be packaged in a number of ways. If you tell us what the game is we should be able to help you with the install. 

As for your .deb files, you should just be able to double click them and the package installer will open, just click install and put in your password when prompted. Make sure to install the data file first or you will probably get errors.

---

### Post by dhabell@yahoo.com on 2007-11-01
> **shad0w_walker said:**
> The .tar.gz file could be packaged in a number of ways. If you tell us what the game is we should be able to help you with the install. 

As for your .deb files, you should just be able to double click them and the package installer will open, just click install and put in your password when prompted. Make sure to install the data file first or you will probably get errors.

it's typhoon 2001, but a general how to for all types would be greatly appreciated!  thank you for the prompt reply!

---

### Post by dhabell@yahoo.com on 2007-11-01
also I tried to install super maryo chronicles.  I installed the data file first but when I installed the other part I got an error that reads "dependency is not satisfiable:libboost-filesystem1.33.1"

---

### Post by cogadh on 2007-11-01
> **dhabell@yahoo.com said:**
> it's typhoon 2001, but a general how to for all types would be greatly appreciated!  thank you for the prompt reply!
You would be better off searching for a specific how-to on the game you are trying to install. A tar.gz file is just an archive, like a .zip file in Windows. It might contain basic source code that you need to compile, or it may contain a fully compiled application that just needs to be extracted, or it might contain an automatic compile/install script... you get the picture? If you are looking for the easiest way to install something, look for a .deb file, like you found with Secret Maryo.

In the case of Typhoon 2001, just extract the files into their own directory in your home folder and run the "typhoon" executable (you might need to mark it as executable first).

As for your Maryo problem, you just need to install the libboost package. Search for it in Synaptic, it should find it.

---

### Post by dhabell@yahoo.com on 2007-11-01
> **cogadh said:**
> You would be better off searching for a specific how-to on the game you are trying to install. A tar.gz file is just an archive, like a .zip file in Windows. It might contain basic source code that you need to compile, or it may contain a fully compiled application that just needs to be extracted, or it might contain an automatic compile/install script... you get the picture? If you are looking for the easiest way to install something, look for a .deb file, like you found with Secret Maryo.

In the case of Typhoon 2001, just extract the files into their own directory in your home folder and run the "typhoon" executable (you might need to mark it as executable first).

As for your Maryo problem, you just need to install the libboost package. Search for it in Synaptic, it should find it.

thanks!  how do I know which one is the executable?  sorry for being so thickskulled...

---

### Post by cogadh on 2007-11-01
Not thick skulled at all, we all had these same kinds of questions at one time.

In the GUI you can ID the executables by their icon. With Ubuntu, it will have a blue diamond icon, Kubuntu has a gear shaped icon, not sure on the other flavors of 'buntu, don't really use them anymore.

EDIT - Almost forgot, your initial question involved a menu entry. Run "alacarte" in the terminal to launch the menu editor ("kmenuedit" if you use Kubuntu) and create a new menu entry for the game. The GUI for that is pretty self explanatory, but don't hesitate to ask if it gives you any trouble.

---

