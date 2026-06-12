---
title: "GTKRC changing browser auto suggest drop down style"
date: 2013-09-16
forum: Desktop Environments
---

### Post by personificator_me on 2013-09-16
Hi all. I've been scratching my head out for a few days on the elusive auto complete suggest box that comes up with FF and chrome. Can anyone help me out? I just need to make the black text white.
I'm pretty sure its a GTKRC issue as if I switch the theme, the text changes color changes in both browsers.

Thanks for any help at all!!

[IMG]http://s17.postimg.org/luom8dbtr/auto_suggest_style.png[/IMG]

---

### Post by vasa1 on 2013-09-16
> **personificator_me said:**
> ... I switch the theme ...
So what is the name and source of the theme you want to use? Is it a "dark" theme?

---

### Post by personificator_me on 2013-09-16
Yep, Blue-Joy [http://gnome-look.org/content/show.php?content=73387](http://gnome-look.org/content/show.php?content=73387) .  Seems to work well for everything else, just not those darn autofill lists.

---

### Post by vasa1 on 2013-09-16
> **personificator_me said:**
> Yep, Blue-Joy [http://gnome-look.org/content/show.php?content=73387](http://gnome-look.org/content/show.php?content=73387) .  Seems to work well for everything else, just not those darn autofill lists.
From your link:
> Because this is a black theme it has some colored text bugs in Firefox 2
(Firefox 3 does not have this problem). 

In Firefox, some pages have white background with white text,to fix this
go to (in Firefox) Edit>Preferences>>Content ,click on colors,
Uncheck the "Use system colors" check box
Then restart Firefox.

To have white text in the Firefox menubar you must modify userChrome.css 
Add the following code to your userChrome.css file. 
userChrome.css is located at: /home/{YOUR USERNAME}/.mozilla/firefox/{YOUR PROFILE ID}/chrome/userChrome.css

Also, I see that that theme is from 2008. It's generally not a good idea to use such old themes.

---

### Post by personificator_me on 2013-09-16
Thanks for the info. I've already done the steps in your post. I know its old, I just figured there must be a way to style that autofil widget in gtk. Thanks again for your help.

---

### Post by personificator_me on 2013-09-16
Just as an update to anyone else coming here, it looks like the autofil widget on both browsers uses the panel background color but ignores the panel text color. Thats why it looks fine in most themes except for dark ones, because they usually have a lighter panel color. (I've tried the latest dark themes and they still have the same problem)

Anyways, if anyone knows the actual gtk widget that I can customize the text color for those, that would still be helpful.

---

