---
title: "Annoying little problem - cosmetic - folder icon"
date: 2018-01-17
forum: Desktop Environments
---

### Post by mrouilla515 on 2018-01-17
I have an little cosmetic problem which I can't find a solution. One of my home folder (video) has an "emblem" sign stuck with it. It looks like a document with a question mark. There is no emblem assigned even though it did once. I removed it a while ago, but now this is stuck. I tried other icons theme and they don't have it. I have check the theme itself (places) and the video icon is fine. The folder permissions are the same as the other home folders and I can read and write in it. Nothing particular there.
 
Is there a way/path to remove that fake emblem ?
Tx

---

### Post by speartip on 2018-01-19
Uploading a picture of exactly what you mean would help.
If I'm reading your problem correctly, it should just be a case of Right Clicking the folder icon, Properties, then Emblems & unticking the offending emblem.

---

### Post by mrouilla515 on 2018-01-19
No I which that would be that trivial. That "emblem" does not exist. It seems stuck there.

 [https://i.imgur.com/LTtxFqW.jpg](https://i.imgur.com/LTtxFqW.jpg)

---

### Post by speartip on 2018-01-19
So if it doesn't happen with other Icon Themes, then it's an issue with the Theme you are using. What is the Theme?

---

### Post by mrouilla515 on 2018-01-19
Funny some don't, some do, the newest ones mostly. I also though it was the theme but I install it on another machine (same Xfce 17.10) and it is fine there. Like I said I have check the theme movie icon and it is fine in the theme. The icon theme is Oranchelo (xfce-look.org).
Where are those links made emblem->folders ?

---

### Post by speartip on 2018-01-19
Try renaming your videos folder to something else, then create a new videos folder and see if the problem persists with your new folder.

---

### Post by mrouilla515 on 2018-01-19
Funny I renamed Vidéos to Vidéo-old, it is gone. If I create again the Vidéos folder, there is goes again. Any other name and it is fine. That's a curse folder !

---

### Post by speartip on 2018-01-19
Just a thing when you downloaded the Icon Theme, did you put it in your Home folder? or in /usr/share/icons? or did you install it as a ppa?

---

### Post by mrouilla515 on 2018-01-19
Download archive, extract and "sudo cp -R ***icon-folder*** /usr/share/icons"

---

### Post by speartip on 2018-01-19
What I would do as a last resort is change to a different icon theme, delete the folder from /usr/share/icons. Then reinstall it via the ppa from here. Then change the theme back and see if there's  any difference.
[https://github.com/OrancheloTeam/oranchelo-icon-theme](https://github.com/OrancheloTeam/oranchelo-icon-theme)

---

### Post by mrouilla515 on 2018-01-19
Bof, I just leave it that way. The ppa has no support for 17.10. 
Thanks.

---

### Post by speartip on 2018-01-20
> **mrouilla515 said:**
> Bof, I just leave it that way. The ppa has no support for 17.10. 
Thanks.

Possibly that's part of the problem. The theme hasn't been updated for nearly a year, & only seems aimed at the LTS versions.
When that's the case sometimes they're fine, sometimes not.
Like you say, if that's the only issue then it's no biggy.

---

