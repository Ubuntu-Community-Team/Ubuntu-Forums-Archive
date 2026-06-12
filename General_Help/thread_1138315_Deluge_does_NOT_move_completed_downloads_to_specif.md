---
title: "Deluge does NOT move completed downloads to specified folder"
date: 2009-04-26
forum: General Help
---

### Post by jdackle on 2009-04-26
Hi everyone,

Using deluge 1.1.6 from the [http://ppa.launchpad.net/deluge-team/ubuntu](http://ppa.launchpad.net/deluge-team/ubuntu) repo on Ubuntu 8.04 Hardy Heron (but this NEVER worked on earlier releases of deluge).

This is my deluge preferences for downloading:
_Transfer to:_ $HOME/Transferências/torrents
_Move completed to:_ $HOME/Transferências
_Copy .torrents files to:_ *Unchecked! Greyed folder displays: $HOME*
_Automatically add .torrents from:_$HOME/Transferências *(but if this is unchecked, the problem persists)*

The $HOME/Transferências folder is actually a symlink to a folder in a NTFS partition: /media/Users/Myuser/Downloads (which Vista referes to as E:\Myuser\Transferências).


Now when downloading, the dowloading file/folder is correctly being downloaded to $HOME/Transferências/torrents.
HOWEVER, on completion, the file is NOT moved to the level-up $HOME/Transferências folder.

I have tried creating a "*COMPLETED*" folder inside $HOME/Transferências/torrents (just to check whether the problem would be with moving the completed downloadas up in the directory-structure) BUT no luck with that (at least not with the already completed/seeding downloads; will have to wait for the next one to complete (allegedly in 2 hours) to check if it is moved upon completion).
I'll post the results for this later.

In the meantime, I don't really belive this will fix it, so... Any clues appreciated.

TIA

---

### Post by jdackle on 2009-04-26
Right... the most recent download did not get moved into the *COMPLETED* folder. I.e. that did NOT solve the problem. :(

Appreciate your thoughts. ;)

---

### Post by lovinglinux on 2009-04-26
It works here. The only problem I have with Deluge right now is that UPnP isn't working.

Are you using full allocation or compact allocation? I use full.  I don't know if this could make a difference, but you could try.

You could also try saving it to a folder without special characters in the name.  I don't know if this has any impact , but I prefer to use only folder names in English instead of Portuguese, to avoid problems.

---

### Post by jdackle on 2009-04-26
I'm using full allocation too, so it shouldn't be it.

I didn't think the non-english characters would be a problem, as the "Download to" folder is a sub-folder of one with non-english characters.
Still, I made a new symlink named *Downloads* and set Deluge to move the completed downloads there.

Will post the result when I have it. 

Thanks for the tips, lovinglinux! :)


P.s.: Falas português?

---

### Post by lovinglinux on 2009-04-26
> **jdackle said:**
> I'm using full allocation too, so it shouldn't be it.

I didn't think the non-english characters would be a problem, as the "Download to" folder is a sub-folder of one with non-english characters.
Still, I made a new symlink named *Downloads* and set Deluge to move the completed downloads there.

Will post the result when I have it. 

Thanks for the tips, lovinglinux! :)

It doesn't matter if they are sub-folders, because the path itself will have special characters since they are under another folder with one.

The symlink might help, but I recommend trying with a normal folder and sub-folder without special characters.

> **jdackle said:**
> 

P.s.: Falas português?

Sim falo português. Sou Brasileiro. 

I didn't reply in Portuguese because it's against the forum policy.

PS: instead of waiting the torrent to complete, you could select the torrent, right-click on it and select the "Move" option and see if it works.

---

### Post by cariboo on 2009-04-26
Can you copy a file to the folder on your NTFS drive?

---

### Post by jdackle on 2009-04-26
FIXED!

Indeed, the problem was the folder with the non-English character. The above mentioned new symlink fixed it for me. ;)


> **lovinglinux said:**
> It doesn't matter if they are sub-folders, because the path itself will have special characters since they are under another folder with one.
That's what I thought! But it DOES matter! My downloading files were SUCCESSFULY being saved to a sub-folder of a "non-English folder".
Moving the completed download to the above non-English one was NOT working and does NOT work!

But... cause identified, problem solved. ;)

> **lovinglinux said:**
> The symlink might help, but I recommend trying with a normal folder and sub-folder without special characters.
Both my prior folder with non-English characters ("Transferências") and the new folder in English ("Downloads") ARE SYMLINKS to a folder in another (NTFS) partition. That did not hurt the sollution stated above.

> **lovinglinux said:**
> Sim falo português. Sou Brasileiro. 

I didn't reply in Portuguese because it's against the forum policy.

Yes, that was wise - I didn't know it's actually against forum policies (though it does make perfect sense - and there are localized versions of this forum anyways; I prefer this one though: there are more English speaking Ubuntu users than Portuguese ones... :P).
I do like to know when I'm speaking to someone who speaks Portuguese - call it pride-in-language if you will. ;)

> **lovinglinux said:**
> PS: instead of waiting the torrent to complete, you could select the torrent, right-click on it and select the "Move" option and see if it works.
Well, it got completed in the meantime, so... :D

> **cariboo907 said:**
> Can you copy a file to the folder on your NTFS drive?
Thanks for the reply, cariboo907. Yes, I can. And as already discovered, that was NOT the problem.
It was a good point though! Thanks! :)

---

### Post by lovinglinux on 2009-04-27
> **jdackle said:**
> FIXED!

Indeed, the problem was the folder with the non-English character. The above mentioned new symlink fixed it for me. ;)

That's what I thought! But it DOES matter! My downloading files were SUCCESSFULY being saved to a sub-folder of a "non-English folder".
Moving the completed folder to the above non-English one was NOT working and does NOT work!

But... cause identified, problem solved. ;)

Weird. Anyways, problem solved. Great!

> **jdackle said:**
> Yes, that was wise - I didn't know it's actually against forum policies (though it does make perfect sense - and there are localized versions of this forum anyways; I prefer this one though: there are more English speaking Ubuntu users than Portuguese ones... :P).
I do like to know when I'm speaking to someone who speaks Portuguese - call it pride-in-language if you will. ;)

Yep, I also prefer this forum. Sometimes I feel kind of guilty to not help more those who speak Portuguese in the localized forums and can't speak English. I also like to say something in Portuguese when I see someone here that speaks it. It's not against the forum policy to exchange small bits of text in other language to identify yourself as fellow speaker, as long as you don't abuse and reply everything using other language. But I don't like to do this anyway, because I might serve as a bad example to others.

---

### Post by jdackle on 2009-04-27
> **lovinglinux said:**
> Yep, I also prefer this forum. Sometimes I feel kind of guilty to not help more those who speak Portuguese in the localized forums and can't speak English. I also like to say something in Portuguese when I see someone here that speaks it. It's not against the forum policy to exchange small bits of text in other language to identify yourself as fellow speaker, as long as you don't abuse and reply everything using other language. But I don't like to do this anyway, because I might serve as a bad example to others.

Couldn't have said it better myself!

Obrigado. :)

---

