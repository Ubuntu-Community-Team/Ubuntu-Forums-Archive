---
title: "&quot;Home folder&quot; opens in media player instead of nautilus"
date: 2011-02-10
forum: Desktop Environments
---

### Post by sbos on 2011-02-10
Hello. I'm using Ubuntu 10.10 x64. Suddenly I found that if I click on "Home folder" in the "Places" (top menu) then this folder is being opened in deadbeaf instead of nautilus. I wonder why. How to fix that?

---

### Post by Copper Bezel on 2011-02-10
Open a Nautilus window, right click any folder, select "open with other application," select "use a custom command," type nautilus, and be sure to check "Remember this application."

---

### Post by sbos on 2011-02-10
Thank you, that works!

---

### Post by Jesuswashomeless on 2011-10-07
Same problem. I have tried this fix but don't see any option to remember. Please advise.

---

### Post by Copper Bezel on 2011-10-07
Yeah, that was a fidgety solution anyway. We can fix the problem more directly - open the file ~/.local/share/applications/mimeapps.list, find the entry for inode/directory, and remove whatever application is listed before Nautilus in that line.

---

### Post by Jesuswashomeless on 2011-10-12
Not sure how to open that file. Sorry I am rally new thanks.

---

### Post by meatytaco on 2011-10-12
I believe you can open it with gedit or nano. Probably will have to "sudo gedit" or "sudo nano" to be able to overwrite the file. IMHO, gedit is much more user friendly :) hope this helps out

---

### Post by Copper Bezel on 2011-10-12
Ooh - no, you wouldn't want to use sudo with this. Just 

```
gedit ~/.local/share/applications/mimeapps.list
```

---

### Post by meatytaco on 2011-10-13
You wouldn't -have- to use sudo or you -shouldn't- use sudo? If youre not supposed to, why not? Just curious, cause if I'm editing any kind of file I sudo before. Usually just in case it doesn't want me to write it

---

### Post by Copper Bezel on 2011-10-13
Yeah, don't throw sudo around all willy-nilly. It's only needed for system files, and if you use it to edit config files in your home directory, you can change their permissions so that the apps in question can't edit their own preferences anymore.

Also, if you're using a graphical app like gedit, launch it with gksu, rather than sudo, for similar reasons. Otherwise, it can have a similar effect on gedit's *own* settings.

Edit: At Krytarik's suggestion, I'm adding this [_link_]("http://www.psychocats.net/ubuntu/graphicalsudo") on further possible consequences of using sudo with graphical apps. I'd oversimplified a bit, and it's not always problematic, but it can sometimes bork your account entirely, so be sure to use gksu.

---

### Post by meatytaco on 2011-10-13
I see I see. Good to know actually. :)

---

### Post by Copper Bezel on 2011-10-13
Yeah, you have to be careful working with elevated permissions. I oversimplified it a bit, and at the suggestion of another user, Krytarik, check out [_this link_]("http://www.psychocats.net/ubuntu/graphicalsudo") - using sudo in place of gksu can actually have worse consequences, so don't do it! = )

---

### Post by meatytaco on 2011-10-13
Alrighty, I'll check that out.

---

### Post by meatytaco on 2011-10-13
Wow... okay. lol... so in short, anything that is graphical, use gksudo, anything that is handled in the terminal use sudo. Scary thing is, this is the first I've actually heard of the gksudo command... although I've only been using Ubuntu for around a month. I used to use slackware quite a few years ago, maybe it wasn't a necessity then? I dunno lol.

---

### Post by Copper Bezel on 2011-10-13
Yeah, privilege elevation differs between distros, and they all have slightly different policies.

---

### Post by meatytaco on 2011-10-13
So to the OP, if you do need elevated privileges to save the file, use gksudo ;)

---

### Post by mc4man on 2011-10-14
No need for gksudo to edit that file, as mentioned in post 6 is proper

If you're on lucid you may want to keep in mind that in 10.04.2 a SRU patch to nautilus was applied that shouldn't have been. Haven't checked to see if it was reverted in 10.04.3

It wouldn't affect how you fix this though would prevent adding anything additional  to the context menu on folders

---

