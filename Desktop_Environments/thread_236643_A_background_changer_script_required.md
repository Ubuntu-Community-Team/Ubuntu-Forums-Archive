---
title: "A background changer script required"
date: 2006-08-15
forum: Desktop Environments
---

### Post by true_friend on 2006-08-15
after a great struggle i concluded that the applications available for gnome in regard to change desktop background are:
Do not install dur to certain problems like libraries not found, or compilers not available or some bugs in ubuntu.
If install can not be run there are always some errors.
If run can not be configured like wp_tray if configured do not work prperly like 'chbg'.
so i decided to use scripts for this purpose. after search and hours of reading related threads i concluded:
The sripts have errors
If they are correct they have deffcienceis like:
If a script get wallpaper from a custom directory it can not change it after a specified time. or it may not randomize them.
If a picture has ability to randomize after some time it do not have a custom location to get wallpapers.
Some times script usese cron to randomize picture after 1 hour. newbie like me do not want to go deep in these details.
so a simple script is required which can:
Change my background from a custom directory
Randomize and remember the last background so avoid repetition at every startup. or make a loop and complete it while remembering it not starting loop from beginiing at every new boot.
Could be added to startup session by command. 
Could be assigned a specific time to change wallpaper.
So can anyone help me in this regard. because i can not write such script:-? :-? :-? :-? :-? .
waiting for some help and advace thanks it would be great help for all linux newbies.
Edit: file picking ability is also affected if there is a space like ab c.gif like file so it should be seen also.
(hay folks why u do not think for a custom application in gnome just like kde has.
hours of search and hours of discussion + programming's result is this there are a few scripts and applications which does not satisfiy the user :mad: )
Regards
True_Friend

---

### Post by moma on 2006-08-15
This is a beginning. (GNOME oriented)

$ [COLOR="Green"]PICTURE="/usr/share/backgrounds/space-01.jpg"[/COLOR]

$  [COLOR="Green"]gconftool-2  --set --type string /desktop/gnome/background/picture_filename "$PICTURE"[/COLOR]

# Background style: Zoomed
$ [COLOR="Green"]gconftool-2  --set --type string /desktop/gnome/background/picture_options zoom[/COLOR]
------------------------------------------------
For other background options, start 
$ [COLOR="Green"]gconf-editor [/COLOR]
and browse to  /desktop/gnome/background/
--------------------------------------------------

For the rest of the road, ABS is your friend.
[http://howtos.linux.com/guides/abs-guide/index.shtml](http://howtos.linux.com/guides/abs-guide/index.shtml)

---

### Post by kerry_s on 2006-08-15
Huh? System> preferences> Desktop Background. Are you missing this in your system? Of course this only set's a background, it doesn't have no randomize feature. Are you trying to do like a picture frame?

---

### Post by true_friend on 2006-08-15
i can not understand this programming. thats why i requested a script. have ability randomization, custom folder, time period and running at startup ( i think cron can be used by specifying time about 15 minutes but i do not know its commands also) :(
and thnx for replying and starting for a script. thnx a lot.
but still along way to go8)

---

### Post by RajivNair on 2006-08-19
People check this out:-

[http://www.gnomefiles.org/app.php/Desktop_Drapes](http://www.gnomefiles.org/app.php/Desktop_Drapes)

---

