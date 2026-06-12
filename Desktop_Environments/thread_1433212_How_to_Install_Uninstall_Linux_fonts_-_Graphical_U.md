---
title: "How to Install /Uninstall Linux fonts - Graphical User Interface / Bash"
date: 2010-03-18
forum: Desktop Environments
---

### Post by Mauror on 2010-03-18
Hi,

Am a newbie on GNU/Linux, where I found the most amazing OS I  could ever imagine..
I loved new fonts, so I  installed a lot, without thinking they could be toooo many!

That's  how I managed myself to install and uninstall Linux Fonts, using the  graphical user interface (GUI): 
(note: My OS are Kubuntu 9.10 and Linux Mint 7 AMD64  edition, in a Toshiba Laptop, but this HowTo is valid for many other  OS)

First,I downloaded some "*.ttf" files (such as "serif.ttf",  but some of them compressed into a "tar" archive) from the [Ubuntu Artwork  page]("http://gnome-look.org/index.php?xcontentmode=39&PHPSESSID=7b92c751086a9c06b8d8df458c8ab070").

Then,  I extracted ONLY the ".ttf" files from the "tar.gz" files, and put my  favorites in a single folder named "Downloaded Fonts", in my desktop.

Then  I opened the File Browser in my computer, and went to "File System".  Inside this folder, I opened the folder "usr", BUT using the right  button of my mouse, and selecting from the menu: "open as root". 

Opening  this folder as root user, you can navigate to the folder "share" and  then enter the folder "fonts" and open it. 

tip: To open Nautilus or  Dolphin as root you can also type in Terminal the following:```
sudo Nautilus
``````
sudo Dolphin
```Open the folder with the new fonts, which I  named "Downloaded fonts"..

With the two folders opened, just  "copy and paste" to the fonts folder, or "Delete" from it the fonts you  won't use. 
These fonts will be available to use on applications and...  **¡¡ In OPENOFFICE too  !!**

:arrow: DONT' FORGET!   NEVER delete System's native fonts!



[SIZE=2]**USING THE BASH CONSOLE (LOTS FASTER!)**[/SIZE]

Once  created "Downloaded Fonts" in my Desktop, with the favorite *.ttf files  inside,
Go and open the Terminal
Type: ```
sudo mv /home/user/Desktop/"Downloaded Fonts"/*.ttf /usr/share/fonts
```After  you enter your user password, this code will "move" automatically all  the fonts directly into the "fonts" folder of the system. And that's  all.
Just remember to change the word "user" for your own username...


I  hope you continue enjoying Linux as much as I do!

---

### Post by mrboojive on 2010-03-22
A simpler alternative to this is to create a directory in your home directory called ".fonts" and place the downloaded fonts there. Then (to update the system's cache of fonts), use a console to run the command```
fc-cache -fv
```The fonts will still be available to all of your applications, and this way you're not risking messing stuff up with sudo. Basically it's not a good idea to fudge around with your root directories like that unless you absolutely have to.

---

