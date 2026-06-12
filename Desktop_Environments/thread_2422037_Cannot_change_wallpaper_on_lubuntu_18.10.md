---
title: "Cannot change wallpaper on lubuntu 18.10"
date: 2019-07-01
forum: Desktop Environments
---

### Post by maxicchars on 2019-07-01
I have just installed lubuntu 18.10 on an old netbook and am having a look at linux.
I thought I'd start by doing something simple: changing the desktop background.
I found a picture and converted it to png format (I read somewhere that lubuntu can only show png format pictures as wallpapers) and copied it to /usr/share/lubuntu/wallpapers/ using the sudo cp command.
I right-clicked on the desktop background and selected "Desktop preferences" from the menu that appeared.
Under the heading "Wallpaper image file" it says /usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png
I click on the browse button and select Jupiter.png.
I click on the open button and it returns to the previous screen
Under the heading "Wallpaper image file" it now says /usr/share/lubuntu/wallpapers/Jupiter.png
As there is no save, apply or OK button I click on the x in the top right of the screen
It returns to the desktop.
I right-click on the desktop background and select "Desktop preferences" from the menu that appears.
Under the heading "Wallpaper image file" it says /usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png again
At no point has the background wallpaper picture changed and I have seen no error messages.
What am I doing wrong?


Hope someone can help me


Maxic

---

### Post by Dennis N on 2019-07-01
Right-click on desktop:

Desktop Preferences > Wallpaper image file > browse to file > select file and click on open.

Don't see save, apply or ok? Re-check you dialog. It should look like the attached screenshot - buttons at bottom. OK button worked to change it immediately.

I keep wallpaper files in Pictures for convenience.

---

### Post by maxicchars on 2019-07-01
Thx for your reply and for posting a picture.
The last line with the OK, cancel and apply buttons was "missing".
It did not fit on the screen and there was no scrollbar so that I could scroll down.
As I was unable to "shrink" the window I had assumed there was nothing more lower down.
After seeing your picture I searched and found the <alt><left mouse button>drag command and was able to find the "missing" buttons, and now it does what I wanted.

Thanks again

maxic

---

