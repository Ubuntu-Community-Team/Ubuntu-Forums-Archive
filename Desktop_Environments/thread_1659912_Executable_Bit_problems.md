---
title: "Executable Bit problems"
date: 2011-01-04
forum: Desktop Environments
---

### Post by MarkVS on 2011-01-04
When I installed Ubuntu a while ago, the first thing I installed was Google Chrome, (the best browser ever!) and next on my list was Wine. I have Win XP on another partition, and wanted to run some of the simpler programs on Ubuntu. But as some of you may have guessed, the "executable bit" was not enabled on these .exe files, so they could not be run. I clicked on the link, read about it, and my heart sank. Ubuntu security was perfect up to this point, but now I could not enable this "bit" (if I click on it, it just unchecks right away).

I have searched long and hard, but have found no way to let me run my programs. I tried some lines in Terminal, but they would not switch the bit over. It's not as if these are programs that I got offline; these are programs I have had on Win XP for years. I need a way to enable the bit permanently. Or I could just turn off the whole executable bit security, but then I would lose all the security of Linux (and I don't know how). Any help would be GREATLY appreciated.

---

### Post by cipherboy_loc on 2011-01-04
Open up the terminal (Applications -> Accessories -> Terminal), and cd to the directory holding the .exe files:

```
cd ~/EXEs/
```
if you have the .exe files in your home directory under the EXEs directory.

then:
```
sudo chmod +x ./*.exe -R
```
to mark them all as executable, recursively (to account for other sub-directories).


Hope that makes sense,
Cipherboy

---

### Post by MarkVS on 2011-01-04
Thanks for responding, Cipherboy

I tried the code in my XP directory, but it came up with a response:


"chmod: cannot access `./*.exe': No such file or directory"

I tried /*.exe, *.exe and just .exe but still no luck. Am I just in the wrong folder, or is it not looking in subfolders?

I also tried it in the Program Files folder and still no luck, and when I tried it in some other folder with a program directly in it, it just did nothing at all.

---

### Post by mc4man on 2011-01-04
If you wish, for whatever reason not sure, to run a .exe from your xp partition then simply use wine instead of 'wine windows program loader'

To do just r. click on any .exe > open with > other application > use a custom command. For the command just - 
wine
This will create a new 'open with' option named wine which will not be afflicted w/ the silly cautious launcher 

(if using maverick when doing the above the 'Remember this...' option will be enabled and will switch the default to wine for d. left clicks on .exe's

---

### Post by MarkVS on 2011-01-04
Thanks mc4man

It worked, I knew there had to be a way around it. Thanks so much. Ubuntu can now do everything. :p

---

