---
title: "wrong file association"
date: 2006-09-29
forum: Desktop Environments
---

### Post by reckless2k2 on 2006-09-29
I accidently picked the wrong default program execution for a file format in Firefox. Problem is that I told it to execute with this program every time so now I'm not asked again. It does not show in download actions in the Firefox preference menu to correct. How can I correct this? I searched around about:config as well with no luck.
Thanks.

---

### Post by dannyboy79 on 2006-09-29
i thought you could right click on that file TYPE within nautilus and change the action of the file type there. i could be wrong I am not in front of my ubuntu dream

---

### Post by wpshooter on 2006-09-29
I think you right hand click on a file of that type and then it is on one of the tabs across the top.  I forget exactly what it is named but seems to me that it is one of the ones over toward the right.

---

### Post by reckless2k2 on 2006-09-29
Maybe I'm not saying this right. I'm trying to open a .cgi from an embedded page. I told firefox to automatically open it with totem by accident. Now, whenever I click on the link it auto opens in totem. I don't have the option to change it to RealPlayer because I told firefox to always open with totem without asking. If I save the file/link to desktop, it runs in realplayer without issue. My problem is that if I link directly in firefox, it opens in totem. I want to switch it back to correctly open in realplayer directly through firefox. 

Most of the time, the file association shows up in download actions in preferences in firefox. In this case, it does not. I believe I have to do something in ./firefox or reset/change the environment variable?

---

### Post by Kateikyoushi on 2006-09-29
You have to change it in firefox.

Edit >> Preferences >> Content Tab, there click manage in the file type area.

---

### Post by reckless2k2 on 2006-09-29
It's not under the content tab. That's for blocking images, sites, java, and how fonts appear. You minght be referring to the downloads tab in the download actions section. There's a button that says view and edit actions but .cgi does not appear for me to change the default action.

---

### Post by Kateikyoushi on 2006-09-29
I checked now and seems in FF 1.5 it is under Download, I am using 2.0 where it is located on the content tab.

---

### Post by reckless2k2 on 2006-09-29
In that area, no file types appear for me to change as I stated before. Even if I set the default action to open and .mpg in totem, that doesn't appear in this area as well. There must be a file in .mozilla to change the mime type or somehow in about:config resetting the mimetype so I can pick again.

anyone?

---

### Post by reckless2k2 on 2006-09-29
Got it reading in mozilla site. Since it does not show in the downloads tab in 1.5, the file types can be reset by deleting or renaming the following file:

~/.mozilla/firefox/dvibi9j3.default/mimeTypes.rdf

Once you that and fire back up your browser, I hit the .cgi link, it asked me what I wanted to open it with again. That's how to reset it. Keep in mind that it resets all of the associations you made so you will have to remap each that you might've done. Simple ask question pick.

---

### Post by neon777 on 2006-10-03
Thank you! I almost quit tying to find a solvation for this...

---

### Post by CatKiller on 2006-10-03
Thanks. Glad you found it - there were a few people asking about this recently. I've just had a look, and you could potentially open the file in Gedit to just remove the MIME-type that you wanted.

EDIT: You really should change the tags that you've used on this thread. They are there to help people searching for information on related subjects, yet you've made no indication that this is a Firefox issue rather than a Linux one.

---

