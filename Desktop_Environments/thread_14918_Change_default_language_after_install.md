---
title: "Change default language after install"
date: 2005-02-10
forum: Desktop Environments
---

### Post by Tiede on 2005-02-10
I am in a sticky situation. Been using Ubuntu or a week or so, now... But today, i decided to reinstall. (Long story, don't ask  :-| )

This is my problem. When I installed the first time, I chose french as default language. yet although I chose the english keyboard layout on the following screen prompt , it still used the french keyboard layout at the welcome screen and then switch back to english layout only after  I login to gnome. It bothered me to have to type about 10 keys each time  i forget where in the french keyboard layout a letter is supposed to be.... For this and other problems (No sound from my SB Awe 64 Card, among others), I decided to redo the install. Well, my problem now is even worse: French is not listed in the languages on the bottom of the welcome screen. It only has English... And I can't seem to find where to go to change the language back to French... So now I am stuck with a mute english system... :-?  Is there a way I can install the french language after the installation and set it as default?

Any help is welcome...

---

### Post by mendicant on 2005-02-10
% sudo dpkg-reconfigure locales

---

### Post by Tiede on 2005-02-14
Thanks mendicant. I already reinstalled Ubuntu in French and sudo dpkg-reconfigure locales only seems to work for the language of the OS, not the keyboard layout by default...
Thanks for the answer though, it might help me later on.
Now, do you know if there is a way to set the keyboard language to English by default? I don't know what to put instead of locoales ;)

---

### Post by mendicant on 2005-02-14
I imagine there's some gnome configuration for that:

Try computer->Desktop Preferences->Keyboard

Then look under the Layouts tab for the available layouts.  I'm not sure if it affects gdm or not.

For the console, I seem to recall that there is something, but I don't remember exactly what it is.

---

### Post by Tiede on 2005-02-16
[QUOTE=mendicant]I imagine there's some gnome configuration for that:

Try computer->Desktop Preferences->Keyboard

Then look under the Layouts tab for the available layouts.  I'm not sure if it affects gdm or not.

For the console, I seem to recall that there is something, but I don't remember exactly what it is.[/QUOTE]
 mendicant... Computer->Desktop Preferences->Keyboard is exactly what I did to be able to use Ubuntu to write right now. Unfortunately, it does not affect the GDM....
Thanks for the answer, anyway.

---

### Post by smoeke on 2005-02-17
[QUOTE=Tiede]mendicant... Computer->Desktop Preferences->Keyboard is exactly what I did to be able to use Ubuntu to write right now. Unfortunately, it does not affect the GDM....
Thanks for the answer, anyway.[/QUOTE]

Look here:
[http://www.ubuntuforums.org/showthread.php?p=72622#post72622](http://www.ubuntuforums.org/showthread.php?p=72622#post72622)

---

### Post by Tiede on 2005-02-19
[QUOTE=smoeke]Look here:
[http://www.ubuntuforums.org/showthread.php?p=72622#post72622](http://www.ubuntuforums.org/showthread.php?p=72622#post72622)[/QUOTE]
 Thanks smoeke. Fits like a perfect glove!


Hello again sweet command line!!! :)

---

