---
title: "Cd Change error when installing WoW"
date: 2007-09-17
forum: Gaming &amp; Leisure
---

### Post by kdarkentity on 2007-09-17
Im trying to install wow in either wine or crossover just as an experiment ... but during the installation process for both wine and crossover when i am prompted to eject the current disk and insert the next disk both wine and crossover dont allow me to eject the disk.

"Cannot eject the disk"

An application is preventing the volume 'WoWDisc1' from being ejected.

What can i do?

---

### Post by derekr44 on 2007-09-17
The very easiest way to install WoW on Crossover (I'm running it this way)

Create a temp folder in your Home folder (like /home/username/wowinstall)
Copy the contents of each install CD to that folder, saying yes to overwriting files... don't create a folder for each cd though... keep all files in the same folder
Run the Crossover installer, but instead of selecting the cd as the source, select the setup file in your /home/username/wowinstall folder

Grab a cup o joe or something, because the WoW install will go all the way through without asking for you to swap CDs 

:popcorn:

---

### Post by yabbadabbadont on 2007-09-17
Although I haven't tried this myself, I have read that there is a "wineeject" command that you run in another terminal in this situation.

---

### Post by jrocket on 2007-09-17
> **derekr44 said:**
> The very easiest way to install WoW on Crossover (I'm running it this way)

Create a temp folder in your Home folder (like /home/username/wowinstall)
Copy the contents of each install CD to that folder, saying yes to overwriting files... don't create a folder for each cd though... keep all files in the same folder
Run the Crossover installer, but instead of selecting the cd as the source, select the setup file in your /home/username/wowinstall folder


this works, except you don't need to copy the whole cd, just the .mpq files.  they'll take up most of the space of the cd, but each one is named different, so if you just copy the entire first cd with the install files, then the .mpq's from the rest of them it should work.

---

### Post by kdarkentity on 2007-09-18
Sweet i have it running in crossover!

---

### Post by Ivantheterrible on 2007-09-30
Where can I get Crossover? I only have wine atm...(1stPost)

---

### Post by yabbadabbadont on 2007-09-30
> **Ivantheterrible said:**
> Where can I get Crossover? I only have wine atm...(1stPost)

You can purchase it here:

[http://www.codeweavers.com/products/](http://www.codeweavers.com/products/)

---

### Post by Ivantheterrible on 2007-09-30
Not so hot on Purchasing...Ok i got the Trial version...but i have no clue how to install it...and the How To Install page doesnt work :(

---

### Post by danhenry on 2007-10-04
Simple. All you have to do is close the terminal that you ran wine from. You can then eject the cd and continue installing WoW. :).

---

### Post by kdarkentity on 2007-10-04
> **Ivantheterrible said:**
> Not so hot on Purchasing...Ok i got the Trial version...but i have no clue how to install it...and the How To Install page doesnt work :(

You mean you dont know how to install crossover right?, well if i remember correctly right click the demo installer, choose properties, and under the permissions tab check off allow exucting the file as a program, then try running it in the terminal

---

### Post by derekr44 on 2007-10-04
I got mine installed by typing in the console:

```
bash crossoverinstallerfilehere.sh
```

I downloaded the LOKI shell script and it installed great.

---

