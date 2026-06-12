---
title: "Website Wallpaper?"
date: 2010-03-22
forum: Desktop Environments
---

### Post by Alan James on 2010-03-22
I would like to have a website display as the desktop background on KDE but so far I have been unable to find a plasmoid or configuration option to do this. I use Google Calenders and would like to see my calender all the time without the need to bring up a web browser.  I am using KDE 4.3 and will be upgrading to KDE 4.4. when it is released. Is there any way of doing this?
 

 Thanks for the help.

---

### Post by Alan James on 2010-03-22
To further clarify, this is similar to Active Desktop on Windows XP.

[http://en.wikipedia.org/wiki/Active_Desktop](http://en.wikipedia.org/wiki/Active_Desktop)

---

### Post by Alan James on 2010-03-24
Does anyone have any advice at all. Even if you tell me it is possible that would be great.

---

### Post by GeneralZod on 2010-03-24
Does it 100% have to be a wallpaper, or would a large Plasmoid embedded into the desktop do? If the latter, there is a webbrowser Plasmoid available which might fit the bill.

---

### Post by Alan James on 2010-03-24
Thanks for the replay. I am primarily trying to display my Google calender and the webbrowser plasmoid wont allow me to login for some reason.
 

 I am curious about how hard it is to write this feature. KDE already allows one to use Marble as a wallpaper and have an interactive globe on their desktop. I wonder if it is possible to do the same thing, but use Konqueror instead. I will look more into doing it myself taking the source code of the webbrowser plasmoid combining it with the desktop.

 

 Again thank you for the reply.

---

### Post by GeneralZod on 2010-03-24
Have you seen this, BTW?

[http://kde-look.org/content/show.php?content=104182](http://kde-look.org/content/show.php?content=104182)

Re: writing it yourself - it shouldn't be too hard, I don't think - look into

[http://websvn.kde.org/trunk/KDE/kdelibs/kdewebkit/](http://websvn.kde.org/trunk/KDE/kdelibs/kdewebkit/)

which should integrate with KDE's cookie jar and wallet (it might be more suitable than stock QtWebkit).

Good luck! :)

---

### Post by Alan James on 2010-03-25
Thanks for the help. I will look into the links provided.

---

