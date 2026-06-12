---
title: "Unknown GNOME error"
date: 2005-06-24
forum: Desktop Environments
---

### Post by N'Jal on 2005-06-24
My Gnome desktop has just got it's knickers in a twist, i use GNOME 2.10 and my system menu has lost it's menu entries for both admin and config, when i say lost it's entries, there is no text and the application are missing so i have two folders where config and admin should be, but's there's no text nor any apps in the folder. I wish i could have taken a screen shot but this has not been possible.... I know ASCII MOCK UP!!!!
```

|Applications|Places|System|
                    |-----------------------|
                    |                      >|            (Config SHOULD be here)
                    |                      >|            (Admin SHOULD be here)
                    |-----------------------|
                    |Take Screenshot        |
                    |Help                   |
                    |About GNOME            |
                    |About Ubuntu           |
                    |-----------------------|
                    |Lock Screen            |
                    |Logout                 |
                    |-----------------------|

```
Hope this helps get the point accross.

---

### Post by N'Jal on 2005-06-25
Sorry but i need to bump this thread myself as an answer mean's i avoid a reinstall. I REALLY don't want to reinstall.

---

### Post by Xian on 2005-06-25
Before you went through a new install I would first check if this is a local config issue. One way to do this would be to create a new user and start a gnome session under that name. If the menu appers to be normal in that session, then I'd start looking at your normal username's gnome config folders in your /home directory.

---

### Post by byen on 2005-06-25
uhh!did it happen after you ran an update? my menu and synaptic menu got screwed up after i ran an update. had to downgrade again to get it working. can you backtrack on what was updated if that was the case?

---

### Post by N'Jal on 2005-06-26
I can confirm that it only happen's as my main user, i created another account and the menu displays as it should, however where are these files i have to edit and what might i have to edit?

No i don't belive this happened because of an update, apparently it's happened to a couple of people, if someone can show me a solution I'll stick it in the howto section, if you want.

Thanks for the help so far :D

---

### Post by N'Jal on 2005-06-27
... anyone?

Edit: Bump

---

### Post by N'Jal on 2005-06-28
Again i need to bump this, as an answer mean's i can simply ghost my hard drive without needing to reinstall.

---

### Post by yarri on 2005-06-29
Hej!

     I have exactly the same problem with my system. It just appeared yesterday. I don't know the reason, but it happend after I downloaded updates - I remember there was kernel-686. 
Anyone can help? I really love to work in ubuntu and I don't want to return to windows, but this little bugs make me really unhappy!

---

### Post by N'Jal on 2005-06-29
I can say removing ~/.config does nothing either i was suggested to try that. It does not work. 

Um i really don't think it was due to an upgrade and definatly not because of the 686 kernel because despite my computer being a P4 686 kernels will not boot.

EDIT: More information to add after typing gnome-control-center and the command prompt (maybe fix a setting) and  im greated to a blank window with nothing in it. It gets worse...

---

### Post by jsemczyk on 2005-06-29
It was working yesterday, I upgraded (dbus and some stuff) and got exactly the same error, no preferences or administration menu. I create a new user login in a new gnome session and the menus are there.

Same as you, I get a blank window with the gnome-control-center.

---

### Post by yarri on 2005-06-29
Ok, I admit, I am really frustrated. 
I have tried many things - deleting .config, changing files: /etc/xdg/menus/preferences.menu 
/etc/xdg/menus/settings.menu - I have no gnome-menus
I even deleted and reinstaled gnome-menus, -applets, -
panel (as described in  [http://www.ubuntuforums.org/showthread.php?t=40302&highlight=lost+menu](http://www.ubuntuforums.org/showthread.php?t=40302&highlight=lost+menu))

Nothing seems to work. Also writing "gnome-control-center" in terminal gives as a result empty window...
I have found this in the bugzilla
[https://bugzilla.ubuntu.com/show_bug.cgi?id=11607](https://bugzilla.ubuntu.com/show_bug.cgi?id=11607)
But I am to new in linux world so it does not help me much.
What I am supposed to do! Help!!!

---

### Post by N'Jal on 2005-06-29
Until one of us can source a solution i think the best thing to do would be to gather information on various aspects that don't seem to work. Then if the bug is not resolved simply add more information to the bug report, and reopen the bug for further investigation. 

If you discover more problems post them here for us to try out, see if they are realated. As far as i am aware gnome-theme-manager still work's (type it into the terminal) quite frankly im supprised that works while the control center does not.

---

### Post by gil-galad on 2005-06-29
Did you try a new user as someone suggested?  The reason he suggested it is that If it works on a different user then it is something wrong with your configuration, not the actual packages themselves.  And that also means it is fixable without having to reinstall.

Also make sure you have ubuntu-desktop installed, in case you accidently uninstalled any important packages.

---

### Post by N'Jal on 2005-06-29
Yes i tryed the new user deal and low and behold the entries are there, i believe i did post the result of this experiment on the previous page. Ubuntu-desktop is installed. Though i am lead to believe it's a meta package.

Please tell me you know where these setting's are, because i really don't know. Nor what to change

---

### Post by gil-galad on 2005-06-29
I see your earlier post now, sorry :)
I don't know what the exact problem is, but if you don't care about some of your settings....

rm -r .gconf*
rm -r .gnome*

Warning:  I don't know if this will cause massive problems!

---

### Post by N'Jal on 2005-06-30
To be honest i might as well try it, if it don't work so be it.

Wish me luck!

Edit: This fails, oh well.

---

### Post by jsemczyk on 2005-06-30
Now both menu disappeared, no blank line they just disappeared.

[QUOTE=gil-galad]I see your earlier post now, sorry :)
I don't know what the exact problem is, but if you don't care about some of your settings....

rm -r .gconf*
rm -r .gnome*

Warning:  I don't know if this will cause massive problems![/QUOTE]

I tried that and some more deleting ( .local .gtk* ) to get a fresh gnome homedir, and I can get my menu back but I cannot tell which directory will do the trick, need further investigations. try removing those files from a console as when you logout from gnome it might save some environment variables

I found how to reproduce this : use **smeg** to remove a menu item in the application menu. I don't now how this is related but it removes the 2 lines from my system menu.

EDIT  : Sorry, this is a totally different issue, using smeg, when I delete the preferences menu from my application menu the administration and preferences also disappear from the system menu...

---

### Post by apollo2011 on 2005-06-30
I am having the same problem...I just upgraded a ton of stuff after adding the backports repository and now the menus are gone.

All of you having trouble loading the Gnome Control Center is simply because you are not running it as root.  Type "sudo gnome-control-center" in a console and it should load.

Hope a fix for this is made...

---

### Post by apollo2011 on 2005-06-30
I got my menus back.  This problem is caused by a bug in Smeg.  If you remove a menu in smeg, it wipes out those two menus.  So when I added back the menu I had unselected, the menus came back.  I repeated this and the menus went away again and I got them back.

---

### Post by N'Jal on 2005-07-01
I HAVE been using smeg to remove some entries, will check and report the result.

---

### Post by N'Jal on 2005-07-01
This has too failed, i have reenabled the entries i removed, though i am sure there were more that i could have reenabled but smeg wouldn't let me. So perhaps a menu entry has been lost in the eyther.

---

### Post by yarri on 2005-07-01
Hi!

        I have tried "gnome-control-center". I run it on another computer - it works without "sudo". On my computer menu opens only with "sudo". I am wondering if there is similar command to acces administration menu? Do you know it? 
I tried trick with smeg but without effect. Possibly problem was coused by smeg but now I don't know how to repair it.

---

### Post by N'Jal on 2005-07-01
I have officially given in with the problem, i have reinstalled and right now am upgrading from the warty cd to hoary. I can't use a computer i can't access the admin tool for. 

I will keep wy eye's out for a solution.

---

### Post by yarri on 2005-07-01
:???: 
Ok! I have my menus back. Don't ask me how it happend. I don't know. I have added menu which I previously removed with smeg - nothing happend. I restarted gnome - still nothing. I switched to windows to play in some relaxing fpp. Now I boot again in Ubuntu - boom! I have my menus back. Just don't tell me it is not magic. I will not believe.

                                           Utterly confused but happy

                                                                     Yarri

---

### Post by N'Jal on 2005-07-01
Perhaps i should have just laid my hand's on it and prayed that might have had a better effect, and since i am still upgrading my system i think i might have been quicker installing gentoo :P.

For some reason my hoary CD didn't work, so install and upgrade from warty

---

### Post by Amaranth on 2005-07-04
Hi guys, this is more than likely caused by a bug in gnome-menus that a bug in pyxdg hits. See if 'rm ~/.local/share/desktop-directories/.directory' fixes it.

---

### Post by apollo2011 on 2005-07-06
[QUOTE=Amaranth]pyxdg[/QUOTE]

Did you mean smeg?  :-?

---

### Post by Amaranth on 2005-07-06
[QUOTE=apollo2011]Did you mean smeg?  :-?[/QUOTE]
No, I meant pyxdg. Smeg just tells pyxdg what to do, pyxdg is the one that creates the files.

---

### Post by apollo2011 on 2005-07-06
Well then smeg is sending bad commands....

---

### Post by N'Jal on 2005-07-06
I have pointed to this thread in the smeg thread's hopefully the smeg author will remedy this is the next smeg release.

---

### Post by Amaranth on 2005-07-06
Smeg isn't sending bad commands and has nothing to do with it. It has to do with the way pyxdg handles legacy menus. The author knows of the problem but like me he hasn't had much time to work on things lately.

---

### Post by espen on 2005-08-25
I solved this problem, for my case at least.

I opened file named /.local/share/desktop-directories$ gedit Settings.directory

I changed value of from ```
NoDisplay=true
``` to ```
NoDisplay=false
``` and 
then rebooted gnome-panel.

It worked for me, hope it works for you too.  :)

---

### Post by icheyne on 2005-08-31
[QUOTE=espen]I solved this problem, for my case at least.
I opened file named /.local/share/desktop-directories$ gedit Settings.directory
I changed value of from ```
NoDisplay=true
``` to ```
NoDisplay=false
``` and 
then rebooted gnome-panel.
[/QUOTE]

Unfortunately /.local/share/desktop-directories does not exist on my installation, so I'm stuck. I'm suprised people are still recommending smeg when it has this bug. :-?

---

### Post by N'Jal on 2005-08-31
Shit man, glad i posed this problem now. Soo many others have had it, well the good news is breezy will have the official GNOME menu editor built for gnome 2.12. So if you upgrade the problem might be solved. It's only a month or so away now.

---

### Post by Amaranth on 2005-09-01
[QUOTE=N'Jal]Shit man, glad i posed this problem now. Soo many others have had it, well the good news is breezy will have the official GNOME menu editor built for gnome 2.12. So if you upgrade the problem might be solved. It's only a month or so away now.[/QUOTE]
 Actually, breezy will have smeg as the default menu editor. Is anyone actually using breezy right now having this problem? If so, can you post the contents of ~/.config/menus/applications.menu?

---

