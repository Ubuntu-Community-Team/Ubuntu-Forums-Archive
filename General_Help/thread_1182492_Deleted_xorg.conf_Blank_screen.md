---
title: "Deleted xorg.conf Blank screen"
date: 2009-06-09
forum: General Help
---

### Post by kunks112 on 2009-06-09
I was following the steps in thread for setting up dual moniters in ubuntu 8.04
```
http://ubuntuforums.org/showthread.php?t=846911
```

Where it said to back up xorg.conf then delete the text inside the file.

So i did this and when I go to repaste the item back inside, I got an error which was "failed to parse".

I couldnt delete the bad xorg.conf and replace it because it told be I didnt have the right privledges, so I restarted and tried to do repair, however I had no luck and all I see now is a blank screen.

Can I get some help please.

I do have a back up that is in the /etc/X11 folder

Thanks

---

### Post by kpkeerthi on 2009-06-09
Use sudo to restore the backup.

**Ex:**
sudo cp a.backup a.txt

---

### Post by seagullplayer77 on 2009-06-09
If you broke X, you might be able to get it back up and running by booting into recovery mode and doing an xfix. You'll lose all of your custom settings, but it might get you your display back.

---

### Post by kunks112 on 2009-06-09
neither worked

---

### Post by CatKiller on 2009-06-09
> **kunks112 said:**
> neither worked

That's not hugely descriptive of what you tried, or what the outcome was.

Did you reboot in recovery mode, select a root console, and then do ```
cp /etc/X11/whatever.you.called.your.backup.file /etc/X11/xorg.conf
``` since that would restore your backup file?

---

### Post by Tipped OuT on 2009-06-09
Go into recovery mode and choose to automatically restore xorg to it's defaults (look for an option like that, i forgot the exact name).

---

### Post by kunks112 on 2009-06-09
What I meant by neither worked is that neither worked.

I logged into recovery mode, into root, tried to reconfigure the xorg.cong. That didnt work.

I tried for it to repair Xconfiguration, however it needed a keyboard setting that I did not know what it was.

I fixed the issue, I re-installed Ubuntu, since I had just re-installed it anyway and was reconfiguring to my old settings.

Thanks for the help

---

