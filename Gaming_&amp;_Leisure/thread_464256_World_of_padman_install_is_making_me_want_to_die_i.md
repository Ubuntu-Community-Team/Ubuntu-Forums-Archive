---
title: "World of padman install is making me want to die irl"
date: 2007-06-04
forum: Gaming &amp; Leisure
---

### Post by Grundalizer on 2007-06-04
ok so i got worldofpadman.run saved to my desktop

/home/god/Desktop/worldofpadman.run

i ran it in terminal, some kid told me to do
 chmod x+ worldofpadman.run

then i ended up doing ./worldofpadman.run and it said verifying archive and brought up the install screen.  

the path it said was /usr/local/games/WoP

i hit Yes and it said, no write permission

i didn't know wtf to do from there so i tried /home/god/usr/local/games

it installed then asked me if i wanted symbolic links or somthing at some usr/local/bin and i said yes and it again said no write permission.  i hit no do not install symbolic things and so it carried out installation.  i think it finished but there is no icon in the applications/games section so i can't find it.

how the heck can i reinstall it to that first path and get write permission, and how can i uninstall it now that it is already in?

---

### Post by Sockerdrickan on 2007-06-04
"World of padman install is making me want to die irl"
Sorry but I just had to say that i LOL'D hard

---

### Post by aaronc222 on 2007-06-04
By default only root has the ability to write to the /usr folder/directory.
Therefore you want to install programs using 'sudo'.
Instead of just running './worldofpadman.run', you would run 'sudo ./worldofpadman.run'

---

### Post by Contrast on 2007-06-25
Should I take this to mean that WOP only installs files in /usr/local/games/worldofpadman? I'm about to install it, but I want to make sure it will be easy to uninstall in the event I want to get rid of it. I had installed RealPlayer with Real's binary installer a while back only to find out it had scattered files all across my system and there was no way to get rid of them all without manually hunting them all down.

---

### Post by hikaricore on 2007-06-25
To be honest you can install it anywhere you want, and almost all modern binary installers come with
an uninstall script in the same directory you installed the application into.

---

### Post by Contrast on 2007-06-25
That's exactly what I was hoping to hear. Thanks a lot. :-)

---

### Post by smartbei on 2007-07-30
I am trying to uninstall WoP and am not able to. I found the uninstall script in  /usr/local/games/WoP. sudo ./uninstall gives me:
> 
Could not find a usable uninstall program. Aborting.

What now?

---

### Post by KingHanco on 2007-07-31
smartbei

sudo rm -rfd /usr/local/games/WoP

This will delete the game permit.

---

### Post by s_spiff on 2007-10-19
ok.. i cant seem to get my instlal working! posted my problem, but noone helped out.. :(
so here is another request...some one help!!!
problems posted here
[http://ubuntuforums.org/showthread.php?t=573168&highlight=padman](http://ubuntuforums.org/showthread.php?t=573168&highlight=padman)

---

