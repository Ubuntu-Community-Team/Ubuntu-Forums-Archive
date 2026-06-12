---
title: "wallpaper/background problems"
date: 2006-09-22
forum: Desktop Environments
---

### Post by bubi1980 on 2006-09-22
Hi,

I visited gnome-look.org to change my background. Here is my problem: i choose a wallpaper of the right resolution (like 1280*1024), and i click on it to open it in a new window. It opens like one picture, then i right click on it to get a menu, but in that menu there is no option "use it as background" or "set it as background".
What do i wrong?
please help me out, its all new for me
thx

---

### Post by heydabop on 2006-09-22
I guess you'll just have to save it to your computer, then set it as your background by going to desktop settings.

---

### Post by bubi1980 on 2006-09-22
In the desktop setting i cant do anything except change the background to 4 other ones (which came from the ubuntu install CD).  I tried to download lot of backgrounds to that directory (usr/share/background) but when i try to change/add wallpaper trough "desktop background" they just dont show up!
what now? :sad:

---

### Post by arkangel on 2006-09-22
save them  in  your own folder, you can create a folder for that matter 

then  on the  desktop  right click  change background  , press add wallpaper , navigate to your folder and choose them  

to write in /usr/share/background you need the rights  to do it 
start reading[ here]("https://help.ubuntu.com/community/RootSudo")

---

### Post by bubi1980 on 2006-09-22
ok, i downloaded some .png pictures to my folder called images. then i opened desktop preferences with right click "change desktop background", i clicked "add wallpaper", browsed to images folder, selected picture. clicked "open" and nothing happened!! the picture didnt even showed up in the list between the other ubuntu wallpapers!:sad: 
i dont know anymore what to do....

---

### Post by bubi1980 on 2006-09-22
one more thing i forgot to say, when i browse (with the "add wallpaper" option in de desktop preferences) to the folder where the downloaded pictures are and i open the folder, i just dont see anything its like empty, but when i click in the right corner in the window "show all files" then they appear.
could that be the problem?

---

### Post by arkangel on 2006-09-22
open nautilus , (file manager  )  click in home or places>>home  

and see the extension  , happened to me  in lookgnome.org  , sometimes it download with  php , html , asp extension , if that is not the case , and they are png or jpg or image format , post it back ,

EDIT: you can safely change the extension, linux does not care about the extensions

---

### Post by bubi1980 on 2006-09-22
I opened them, and checked them by right clicking on the pictures. They are jpg documents and png documents and it says also "MIME typed: application/x-extension-png".

so thats it, still not working:)

---

### Post by arkangel on 2006-09-22
well I dont know seems to be really trivial maybe you have mime file problem  (guessing)

try this , open a console and type
# cd ~/.local/share
# mv mime mime.bk 
you 've just changed  the  folder name mime to mime.bk

and logout and login again (do not restart )

and try  again   

NOTE to restore to the  previous state 
# cd ~/.local/share
# mv mime.bk  mime

---

### Post by arkangel on 2006-09-24
just for your curiosity :)  , verify you have this file 'backgrounds.xml'   in ~/.gnome2
the list of backgorund  should be in ~/.gnome2/backgrounds.xml  
#cd ~/.gnome2/
#gedit backgrounds.xml
    --please make a back up !! ---
#mv backgrounds.xml backgrounds.xml.bk

try playing  with it (add a wallpaper manually, remove the file )and see waht happens

---

