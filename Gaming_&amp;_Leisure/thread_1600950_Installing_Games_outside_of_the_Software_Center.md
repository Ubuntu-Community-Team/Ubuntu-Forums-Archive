---
title: "Installing Games outside of the Software Center"
date: 2010-10-19
forum: Gaming &amp; Leisure
---

### Post by H3R3T1K on 2010-10-19
I'm trying to install True Combat: Elite, an Enemy Territory mod. [http://www.truecombatelite.com/](http://www.truecombatelite.com/)

I downloaded the ET Linux install file first. It's a file that has a ".run"-ending. If I double click it, it gives me this error:

"gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again."

What's the correct way to install the game?

---

### Post by Cresho on 2010-10-19
with these you may need to change permissions.right click on this file and go to properties.  click on permissions tab and put a checkmark for execute.  you can now double click on it and it will show work like an exe in windows.

---

### Post by Valthar on 2010-10-19
I can't even get the download link for the linux version to work for me. Been like that for a while.

---

### Post by Cresho on 2010-10-19
if the above don't work, open terminal after you fixed permision and 

#cd /home/user/Downloads.
#./game.run

make sure you replace user with your name, don't use the# sounds at start of terminal (basically tells the line not to work) and replace game with the name of your file and add the .run.

---

