---
title: "I *need* a default KDE with trashcan on desktop etc..."
date: 2006-03-31
forum: Desktop Environments
---

### Post by Nezumi on 2006-03-31
Hi,  I have spent the afternoon trying to Google for this but have come up empty handed.

I'm really enjoying Kubuntu 5.10 but cannot stand the 'improvements' the devs' have made with regards to default behaviour for Konq' and the lack of icons such as 'Home' and 'Trashcan' on the desktop.

If I can have a KDE the way that the KDE devs intended then I'm ready to 'switch' from XP.  But. I *must* have standard functionality!

I realise this is a lame question but I'm fairly new to *nix.  I'm guessing I need to edit a .conf file someplace...

NOTE:  Dear Kubuntu devs, kindly allow for the restoration of a standard KDE quickly and easily.  This is _very_ annoying.  I shall of course post this request to the correct place.

Many thanks to anybody who is kind enough to help me.  You will have the warm glow of satisfaction of knowing that their is one less copy of XP in the world ;-)

---

### Post by aysiu on 2006-03-31
The Google search that worked for me was...

*site:kde.org trash desktop icon*

That turned up these instructions, which work (I just tested them): > Add trash icon to your desktop

   1. Right click on the desktop
   2. Select "Create New > Link to Location (URL)..."
   3. On the KDesktop dialog, enter:
         1. File name: trash
         2. Enter link to location (URL): trash:/ 
   4. Click on OK 

And to change the icon when the trash is empty:

   1. Open a konsole
   2. Write: echo "EmptyIcon=trashcan_empty" >> ~/Desktop/trash.desktop
   3. Check if the file looks like in Trash trash.desktop example file. 

---

### Post by GeneralZod on 2006-03-31
You can also undo the damage done to Konqueror by following these steps:

[http://www.kubuntu.org/faq.php#konqueror](http://www.kubuntu.org/faq.php#konqueror)

Also, you can get the Home icon by replacing "trash" with "home" in Aysiu's post :)

---

### Post by Nezumi on 2006-03-31
Just a few bytes to say thanks for the help guys.  I think a lot of the problem is that I'm not used to a DE that's so darn powerfull!

It'll all come with time... :)

---

