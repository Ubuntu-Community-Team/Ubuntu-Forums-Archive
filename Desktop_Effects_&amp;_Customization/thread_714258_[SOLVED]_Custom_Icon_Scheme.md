---
title: "[SOLVED] Custom Icon Scheme"
date: 2008-03-03
forum: Desktop Effects &amp; Customization
---

### Post by stooshbunutu on 2008-03-03
So I have a clash. I like some I cons in one theme and some other Icons on another theme.

Is there a way to make my own custom theme and Icon set with all the ones I want?

I have searched other threads but everyone seems to have some kind of common knowlage that I don't.

Could someone break it down for me to make it easy.

Cheers

---

### Post by rune0077 on 2008-03-03
The simple but dirty way: Your icon themes can be found in /yourhomedirectory/.icons. Just browse to your currently used theme and overwrite the icons you don't want with the new ones that you do want. Just remember that the new icon must have exactly the same name as the one your removing. Also, most themes specify icons of several different sizes, in which case you need to replace all of them. Hope that makes sense.

---

### Post by stooshbunutu on 2008-03-03
How can I browse with and edit my system files that require root privaleges?

Is there nothing easier? I opened the main file with sudo gedit and there is streams and streams of gobldy gook. Any kinda GUI or simpler method?

Cheers anyhow

Regards

---

### Post by stooshbunutu on 2008-03-04
Is there any way I could opena file browser, with root permissions so I can make edits in the icons directory.

Or is there a way I can login as root, I cant work out how to

---

### Post by Distro Jockey on 2008-03-04
**sudo nautilus**
from a terminal should do the job

---

### Post by rune0077 on 2008-03-04
> **stooshbunutu said:**
> Is there any way I could opena file browser, with root permissions so I can make edits in the icons directory.

Or is there a way I can login as root, I cant work out how to

Alt+F2, then type "gksu nautilus". 

It's probably better to copy the folder into .icons in your home directory, then do the changes there. That way, you won't mess up the original icon theme.

As far as I know, you have to do this manually, since there aren't any software for making icon-themes.

---

### Post by stooshbunutu on 2008-03-04
Good hit about *gksu nautilus*

I copied and pasted the "Human" theme and renamed "Human (copy)" as "stooshtheme" I then used *sudo gedit /usr/share/icons/stooshtheme/index.theme* and renamed it at the top from "Human" to "stooshtheme".

Is is now a simple but lengthy process of replaying the images I don't want with the images I do (keeping the name and size exactly the same) in every size folder?

If so how would I make and svg or is that a simple export in GIMP?

Sorry to be nooby and over cautious but I am treading in uncharted waters for me and so I dont want to mess things up.

Cheers again

---

### Post by rune0077 on 2008-03-04
> **stooshbunutu said:**
> Good hit about *gksu nautilus*

I copied and pasted the "Human" theme and renamed "Human (copy)" as "stooshtheme" I then used *sudo gedit /usr/share/icons/stooshtheme/index.theme* and renamed it at the top from "Human" to "stooshtheme".

Is is now a simple but lengthy process of replaying the images I don't want with the images I do (keeping the name and size exactly the same) in every size folder?

If so how would I make and svg or is that a simple export in GIMP?

Sorry to be nooby and over cautious but I am treading in uncharted waters for me and so I dont want to mess things up.

Cheers again

Gimp can't do svg's as far as I know. You'd probably need Inkscape for that, but I'm not into all the graphics tool so maybe someone else can advice you in this. It isn't necessary to have svg's, though, since Gnome can use both svg's and png's. 

Other than that, yes, it's just doing a lot of copy-rename-paste and you should be set to go.  Also, you should be sure to open the file called Index.theme in your theme folder and make appropiate changes to the entries in it (mostly, you'd probably just need to change the name of the theme to your own so it won't conflict with the original human theme).

---

### Post by stooshbunutu on 2008-03-11
to complete the process the folder needs then to be compressed into a .tar.gz to be installed as a theme under appearances, cheers all who helped

---

