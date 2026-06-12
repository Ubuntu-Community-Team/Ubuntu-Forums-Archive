---
title: "missing aplication search and file and folder search from side bar"
date: 2011-05-24
forum: Desktop Environments
---

### Post by Dleacy on 2011-05-24
Hello all, installed natty a few weeks ago and im loving it so far. However ran into a self created problem today.

I installed the screenlet widget application through Ubuntu Tweak, didnt really see the point of it and so removed it through software centre. The problem is is that im now missing the search files and folders and the application search shortcuts from the side bar.

Im not sure if its ubuntu tweak or the uninstallation screenlet has done this but if someone can help that would be awesome as i use these search options daily.

Cheers all in advance!!!

---

### Post by Copper Bezel on 2011-05-24
Does [this]("http://ubuntu4beginners.blogspot.com/2011/05/hide-applications-andor-files-folders.html") help?

Edit: No, actually, that probably won't help. Poking around for something.

Edit Again: Going to have to leave this to someone with firsthand experience. [This]("http://www.wmlcloud.com/linux/add-remove-unity-launcher-items-with-unity-launcher-editor/") doesn't directly address your problem, either. I don't understand how anything you did could have affected Unity-related files in /usr, but editing the menu for just your user account shouldn't allow you to remove those two items, which apparently can't be toggled off for individual users.

---

### Post by mc4man on 2011-05-24
Open up synaptic, search unity-pl
Make sure the 2 packages in screen are installed

If they are installed then run this 
```
gedit /usr/share/unity/places/*.place
```

Make sure in the [Entry:Files] section in both files that this isn't there
ShowEntry=false

(in the 'applications.place' file > section [Entry:Runner] ShowEntry=false is there by default and should be left there

---

### Post by Dleacy on 2011-05-25
Brilliant thanks. Oddly enough they reappeared after a few restarts but its good to know to check this in the future and that I can hide them if, not that I'd ever want to!

Thanks again!

---

### Post by whalogreg on 2011-10-18
So, mine are missing as well. I'm running 11.10 which doesn't have the folder /usr/share/unity/places

Any idea where i should start?

---

