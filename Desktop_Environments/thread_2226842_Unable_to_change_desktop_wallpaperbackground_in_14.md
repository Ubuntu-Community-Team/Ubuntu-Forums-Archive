---
title: "Unable to change desktop wallpaper/background in 14.04."
date: 2014-05-29
forum: Desktop Environments
---

### Post by john_smith5 on 2014-05-29
Simply Desktop settings dialogue won't allow me to change the wallpaper.  When I browse my /Pictures folder from within the app individual file names are greyed out.  When I browse /Pictures using Thunar  and right click on file and select Set as Wallpaper it doesn't change the wallpaper either.  

If I try to change my About Me/Mugshot avatar it allows me to change that picture.  Whatever picture I select then appears in the  Desktop settings Background/Wallpaper dialogue box.  If I then select that picture it changes my wallpaper. (It fails to scale the image too but that is the least of the problem.)

It is a vanilla fresh install on very prosaic hardware (my old NC10 netbook) and I am not sure what to do. 

Any help appreciated.  I think I am finding it irksome because the rest of 14.04 is so good.  :D

---

### Post by Toz on 2014-05-29
Hello and welcome to the forums.
>  When I browse my /Pictures folder from within the app individual file names are greyed out.
This is because from that dialog you're supposed to select a folder. When the folder is selected, the wallpaper from that folder is displayed in the dialog and you can click on the wallpaper in the dialog to select it.
> When I browse /Pictures using Thunar and right click on file and select Set as Wallpaper it doesn't change the wallpaper either. 
Is xfdesktop running? 
```
ps -ef | grep xfdesktop | grep -v grep
```
...it would need to be as it manages the display of the wallpaper.

---

### Post by john_smith5 on 2014-05-29
Thank you for replying.

Yes xfdesktop is running.

And I am aware that the dialogue box is displaying the contents of folder which is switched using the dialogue box 2/3 down on the left hand side.  As I said above whatever I have selected as my Mugshot/avatar appears in the box.  If I switch to File system or Desktop the file/icon disappears as obviously I have switched directory.

I am going to have another think and test a few more things.

The reason why I am struggling is that it such a simple process there should be no difficulty.  Perhaps it is too simple?  :)

---

### Post by Toz on 2014-05-29
During your troubleshooting, open a terminal window and run the following command:
```
xfconf-query -c xfce4-desktop -m
```
...then try to change the wallpaper. Lets see which properties are being affected.

It would also be helpful if you listed all of the channel's properties:
```
xfconf-query -c xfce4-desktop -lv
```

I recall a time during the beta cycle where the wrong xfconf entries were being written to, but that was eventually fixed.

---

### Post by monkeybrain20122 on 2014-05-30
It works here. Yes in Desktop settings the individual pictures are greyed out , but if you click "Open" all the pictures in the parent folder  will be displayed in the desktop settings app's window, then just choose the wallpaper you want by clicking. So, you have to choose a folder instead of a picture in the dialogue, then choose the picture only after you have picked a folder. 

Note the folder in the screenshot is "Pictures" rather than "Backdrops". I only have one picture so only one is displayed. I guess you should put all the wallpapers in one folder then. 

Well I guess that is not very intuitive.

---

### Post by john_smith5 on 2014-05-30
> **monkeybrain20122 said:**
> It works here. Yes in Desktop settings the individual pictures are greyed out , but if you click "Open" all the pictures in the parent folder  will be displayed in the desktop settings app's window, then just choose the wallpaper you want by clicking. So, you have to choose a folder instead of a picture in the dialogue, then choose the picture only after you have picked a folder. 

Note the folder in the screenshot is "Pictures" rather than "Backdrops". I only have one picture so only one is displayed. I guess you should put all the wallpapers in one folder then. 

Well I guess that is not very intuitive.


Thanks monkeybrain.  But probably due to my lack of intuition I am struggling to follow your post.  I am going to follow Toz's instructions first and then I will try to follow your post again. TBH in the end it will be me and Xfce or Xubuntu of that I am certain. I would be happy with your suggestion if I could set the wallpaper just by clicking on a pic in a folder without going near the settings apps but I can't. Thanks again for taking the trouble to help. It is very much appreciated.

---

### Post by john_smith5 on 2014-05-30
> **monkeybrain20122 said:**
> It works here. Yes in Desktop settings the individual pictures are greyed out , but if you click "Open" all the pictures in the parent folder  will be displayed in the desktop settings app's window, then just choose the wallpaper you want by clicking. So, you have to choose a folder instead of a picture in the dialogue, then choose the picture only after you have picked a folder. 

Note the folder in the screenshot is "Pictures" rather than "Backdrops". I only have one picture so only one is displayed. I guess you should put all the wallpapers in one folder then. 

Well I guess that is not very intuitive.

I have had another go.  And yes you right.  I soon as I started to do the diagnostics I realiese what you are saying.  Thanks again.  I knew in the end it would be me being a plank and not the software.  :redface:

---

### Post by john_smith5 on 2014-05-30
@ toz

Thank your for your help.  I am sorry that I am an utter noodle.  :(

---

