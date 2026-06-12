---
title: "Plz help..my window borders are missing,my windows are not moving."
date: 2011-07-02
forum: Desktop Environments
---

### Post by lalitha niharika on 2011-07-02
I upgraded ubuntu recently.I am using 11.04.I faced same problem after upgrade.Then I reinstalled compiz, after that I enabled wobbly windows and window decoration.then borders reappeared, windows were moving, everything was perfect.Now I just wanted to know about all compiz features.So in order to test each feature, I enabled few options.Then suddunly borders disappeared, my windows are not moving.I dont know what all I have enabled.I just ticked randomly.I dint know that it leads to problems.What should I do now?I tried removing and reinstalling compiz.But settings are not changing.:mad::(

---

### Post by ~!geek!~ on 2011-07-02
Follow this:
1 open ccsm 
2 go to preferences 
3 in profile&backend tab click on reset to defaults button 
4 Now  choose your favorite options wisely in ccsm.:)

---

### Post by steinerd on 2011-07-02
If the above option is unavailable to you then follow this [http://shallows.bounceme.net/tiki-index.php?page=Reset+Desktop+to+Default&structure=Ubuntu+Help&page_ref_id=17](http://shallows.bounceme.net/tiki-index.php?page=Reset+Desktop+to+Default&structure=Ubuntu+Help&page_ref_id=17)

or this [http://shallows.bounceme.net/tiki-index.php?page=Reset+Unity+Desktop+and+Icons&structure=Ubuntu+Help&page_ref_id=21](http://shallows.bounceme.net/tiki-index.php?page=Reset+Unity+Desktop+and+Icons&structure=Ubuntu+Help&page_ref_id=21)

Hope this was some help to you...

---

### Post by prshah on 2011-07-02
> **lalitha niharika said:**
>  borders disappeared, my windows are not moving.

It looks like the window decorator is crashing. 

To check/solve, press alt+f2, and give the command ```
gtk-window-decorator --replace
``` If that doesn't work as expected, then try ```
compiz-decorator --replace
``` or ```
x-window-decorator --replace
``` (You can change the order if you feel suitable).

If either of these commands give you back the title bar (and window decorations) then you have to find out why that particular decorator is crashing. Please post back if need suggestions on this.

If neither of these give you back your title bar then probably your entire window manager is affected; try ```
compiz --replace
``` or ```
metacity --replace
```

---

### Post by lalitha niharika on 2011-07-02
Thanks for quick reply.I did that.I clicked reset to default.Then screen got stuck!!now nothing is there on the screen.Not even turnoff button!then I switched off my ups.I started again, then also total desktop is blank.Now I am using my computer by changing it to classic no effects mode.:(

---

### Post by lalitha niharika on 2011-07-02
Now I did all metacity replace,compiz replace etc...then opened normal ubuntu.Then also its blank.Now I am scared to open that.I cant switch off ups again and again.Now again I logged in classic no effects mode.Plz help me to atleast to get back turn off tab!!

---

### Post by ~!geek!~ on 2011-07-02
> **lalitha niharika said:**
> Thanks for quick reply.I did that.I clicked reset to default.Then screen got stuck!!now nothing is there on the screen.Not even turnoff button!then I switched off my ups.I started again, then also total desktop is blank.Now I am using my computer by changing it to classic no effects mode.:(


now you may delete the old compiz settings by following the links in replies above. 
It will definitely work

 Even if that does not work:  create a new user, say test and login with this user and see if compiz working fine. Although I m pretty sure the links above will solve your problem.

---

### Post by bokgeneraal on 2011-07-02
[SIZE=2]**KDE 4.6**[/SIZE]
Have you tried kdm (kde 4.6 ) . It has most of the eye-candy of gnome with kwin instead of compiz. It is not totally crash free as is gnome. However, I find it to handle crashing better. To install kdm install kubuntu-desktop.

---

### Post by lalitha niharika on 2011-07-02
Thank you so much.:)I created new user, that account is absolutely fine.But now can I totally delete present account and make my new account as root account??Other problem is, files present in this account are invisible from new account.Is there any easy way of transferring them from this account to new account???

---

### Post by Krytarik on 2011-07-02
lalitha niharika, please see this troubleshooting guide:
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

If you prefer sticking with the new user, see this guide:
[http://ubuntu4beginners.blogspot.com/2011/06/make-duplicate-copy-of-user-account-in.html](http://ubuntu4beginners.blogspot.com/2011/06/make-duplicate-copy-of-user-account-in.html)

@steinerd: Please try to avoid recommending users to delete the settings of almost the entire Gnome environment and a lot of apps as far as possible.

---

### Post by lalitha niharika on 2011-07-03
Thank you so much for everyone...I am using new account now.:popcorn:Main problem is, when I enabled some compiz settings, in order to resolve conflicts, it disabled unity.Anyway I could not correct it even after enabling unity,replacing etc...but I am using new account.Now also I need to disable unity to enable cube.So I decided to sacrifice desktop cube.

---

### Post by Krytarik on 2011-07-03
Please see this guide on how to enable the Cube if using Unity:
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

Greetings.

---

### Post by lalitha niharika on 2011-07-04
Thank you sooooooooo much!!Its working:D:D

---

### Post by Krytarik on 2011-07-04
You're welcome! :)

---

### Post by lalitha niharika on 2011-07-05
again another problem!You gave me some link, I got cube successfully in ubuntu.So I tried to do same thing in ubuntu classic mode.then side bar appeared.By reading some articles, guides I came to know that it is because of unity.then I disabled unity in compiz.Now again my screen became blank.How can I get it back??alt+F2 is not working:confused:

---

### Post by lalitha niharika on 2011-07-05
I solved that problem by seeing your reply in other thread.So everything is back.Only problem is, my ubuntu classic is just like ubuntu.how to disable unity in this?

---

### Post by Krytarik on 2011-07-05
> **lalitha niharika said:**
> Only problem is, my ubuntu classic is just like ubuntu.how to disable unity in this?
Make sure you have the correct profile selected for either session in "CompizConfig Settings Manager -> Preferences (lower left)":
- classic Gnome: "Default"
- Unity: "Unity"

Then in classic Gnome, make sure the "Ubuntu Unity Plugin" is disabled in CCSM.

Greetings.

---

### Post by lalitha niharika on 2011-07-06
Thank you so much again:)

---

### Post by Krytarik on 2011-07-06
You're welcome, again! :-D

---

