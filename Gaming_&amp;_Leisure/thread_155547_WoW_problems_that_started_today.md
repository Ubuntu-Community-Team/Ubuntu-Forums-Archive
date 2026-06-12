---
title: "WoW problems that started today"
date: 2006-04-05
forum: Gaming &amp; Leisure
---

### Post by imlost on 2006-04-05
I went to log in this morning and was unable to. I have been running WoW on linux using Wine for about a month now. Ya, since this last patch I had a few problems getting back in game, mainly due to blizzards server problems but then everything was fine after that.

When I try to log into wow it goes to the connecting then flashes through some other ones and stops at one that says downloading and the screen flickers in and out. It does nothing from here and I end up having to xkill wow. I am getting nowhere right now and I really want to play.

Has anyone else come across this problem yet and can tell me what I need to do?

](*,) 

Someone please help before I lose it!

---

### Post by theh0g on 2006-04-05
If it says "downloading", then just download a patch manualy (google for it) and install it...and then retry. That's what I do at similar problem.
I had similar problems yesterday, it just stopped at "handshaking" or it threw out "unable to connect". There is nothing wrong with your client, but there sure are some bad problems with servers, not to mention huge lags and all. I remember reading somewhere they're getting new better servers, but I guess not everything went smoothly. I'm sure they'll fix this, but it really can be annoying, I know.

---

### Post by imlost on 2006-04-05
[QUOTE=theh0g]If it says "downloading", then just download a patch manualy (google for it) and install it...and then retry. That's what I do at similar problem.
I had similar problems yesterday, it just stopped at "handshaking" or it threw out "unable to connect". There is nothing wrong with your client, but there sure are some bad problems with servers, not to mention huge lags and all. I remember reading somewhere they're getting new better servers, but I guess not everything went smoothly. I'm sure they'll fix this, but it really can be annoying, I know.[/QUOTE]

But here is the problem... I can't find a new patch or hotfix. I have looked. Are you running WoW on linux using Wine? If so is it still running fine?

---

### Post by Toxicity999 on 2006-04-05
Well, when it says 'Downloading' on the progress of login it's not for a patch (It happens on every access.) I'm not sure what it is in fact... I noticed it after they started using the Protective loader.exe... so one can only Assume. If your up to date I don't know what to tell you... It doesnt work for me but then again it never has haha.

---

### Post by ZonedOut on 2006-04-05
imlost, I am having the exact same problem that you are having.  I have been playing WoW in Ubuntu since December without any problem.  Then last night all of a sudden I'm getting that error when I try to log in.  When I run the game in windowed mode, the screen just goes blank at that point.

---

### Post by imlost on 2006-04-05
So I copied all of the files in the WoW directory from my wifes computer that is running windoze and tried again, however I am still getting the exact same problem, I still get stuck at logging in and the screen flickers and I get nowhere from there. Someone please help!

:confused:

---

### Post by illurim on 2006-04-06
I'm suffering the same problem, however, I noticed that the flicker occurs between two mini-windows during the load:  "Download" and "Submitting non-personal system specification".

When I boot into windows, I get a slight jitter / lag between the "Download" and "Submitting non-personal system specification" mini-windows, but the game loads and works fine.

Something's changed, but what it is I don't know. My assumption is a .dll of some description?  No idea. When I got it to work in windows, I did a "date modified" sort of the WoW directory but no files had been altered, as near as I could tell.

Very frustrating.

---

### Post by illurim on 2006-04-06
Did some more research and found a fix by looking at the WineHQ site. Basically, make your WDB folder in /wherever/you/installed/wine/drive_c/Program Files/World of Warcraft/ read only (I switched permissions for all to read only) - this worked fine.

---

### Post by imlost on 2006-04-06
[QUOTE=illurim]Did some more research and found a fix by looking at the WineHQ site. Basically, make your WDB folder in /wherever/you/installed/wine/drive_c/Program Files/World of Warcraft/ read only (I switched permissions for all to read only) - this worked fine.[/QUOTE]

Thank you so much illurim for your help with this. I have to go to work right now but when I get back I will try this. I do not have world of warcraft in the /drive_c/Program Files/World of Warcraft folder becuase I am having a hard time creating a shortcut to wow.exe since I can not seem to use spaces in the shortcut path.

Anyhow right now I got to work on the fact that I was trying to get back into my windoze partition so I changed the lilo.conf to default to the windoze partition, which did not work, now I have to figure out how to change it back. I have no clue.

---

### Post by theh0g on 2006-04-06
[QUOTE=imlost]But here is the problem... I can't find a new patch or hotfix. I have looked. Are you running WoW on linux using Wine? If so is it still running fine?[/QUOTE]

[http://www.google.com/search?q=wow+patch+1.10+mirror](http://www.google.com/search?q=wow+patch+1.10+mirror)

---

### Post by ZonedOut on 2006-04-06
I can confirm that changing the WDB folder to Read-Only fixed the problem for me.  Thanks for the help.

---

### Post by illurim on 2006-04-06
[QUOTE=imlost]I do not have world of warcraft in the /drive_c/Program Files/World of Warcraft folder becuase I am having a hard time creating a shortcut to wow.exe since I can not seem to use spaces in the shortcut path.
[/QUOTE]

You should be able to resolve this by escaping the spaces, like this:

/drive_c/Program\ Files/World\ of\ Warcraft

Basically, you put a \ before every space and the system will not have an issue with the spaces.

---

### Post by imlost on 2006-04-07
so after much work on reinstalling Ubuntu and Wine I finally get WoW running, only glitch, I can not select anything. That's fine I can fix that tomorrow, so I reboot the computer and go to bed. When I got up this morning I find my computer hanging on the reboot at a certain part... Kernal Panic.

No matter how many times I reboot I always get a kernal panic, so now I am reinstalling... again.

I post here now only to try and keep my sanity, for I feel like I am about to lose it. I spend 2 days reinstalling and configuring my wine just to be back at square one after a single reboot. I love Linux and loth the idea of going back to Windblows but I fear that if this happens again I will he no choice.

---

