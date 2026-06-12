---
title: "Remove the little arrow from Main Menu icon on panel..."
date: 2006-06-26
forum: Desktop Environments
---

### Post by mhancoc7 on 2006-06-26
Is there anyway to remove the little black arrow from the Main Menu icon. I have added the Main Menu icon to my panel and have successfully changed the icon to a custom one using the Configuration Editor. Now I just need to get that little arrow to go away to complete my customization. Is this possible? 

Thanks in advance for all your help...

Jereme

---

### Post by aysiu on 2006-06-26
Do you have a screenshot of the arrow you're talking about?

---

### Post by mhancoc7 on 2006-06-26
Here is a screenshot. The arrow that I am concerned with is the one on the Main Menu (start button). I also pointed out the ones on the Drawer launchers as well. I would love to get rid of them all together.

Thanks , Jereme

---

### Post by Anduu on 2006-06-26
I notice you are using a custom theme on your bar...are those arrows there using the default theme?

---

### Post by mhancoc7 on 2006-06-26
Yes, they are. The little arrows are always added to the Main Menu panel launcher and the Drawer Object panel launchers regardless of the theme. I figured there must be a way to edit a config file or something to get rid of them.

Thanks, Jereme

---

### Post by aysiu on 2006-06-26
I don't know if there's any way to get rid of that arrow...

---

### Post by mhancoc7 on 2006-06-26
Yeah, I figured this might be something that would not be possible.

I was just hoping that there was some way to edit a config, xml, or some other file that controled the appearance of the Main Menu.

Thanks, Jereme

---

### Post by aysiu on 2006-06-26
It appears even in KDE, believe it or not...

---

### Post by mhancoc7 on 2006-06-26
Well I edited my Ubuntu Start button to make the arrow a little less annoying. I have attached the latest screenshot and the new Ubuntu Start button png. I would still like to get the little arrow to go away, but this will do for now.

Thanks , Jereme

ps I also attached some other Ubuntu Start button pngs for anyone that may want them.

---

### Post by mhancoc7 on 2006-06-27
Ok, I found this link on another forum post.

[http://forums.gentoo.org/viewtopic.php?t=121973]("http://forums.gentoo.org/viewtopic.php?t=121973")

I tried it, but I just get a command not found error at the very beginning.

Any ideas?

Thanks, Jereme

---

### Post by scxtt on 2006-06-27
gconf is the configuration editor, "System Tools --> Configuration Editor" ... commenting out code for the source of the menu seems like an awful lot of work for something trivial like that ...

---

### Post by mhancoc7 on 2006-06-27
I agree, but I really want to get it to go away. Do you know what needs to be commented out?
Thanks, Jereme

---

### Post by scxtt on 2006-06-27
the directions say:

[quote=from the article]

3. Locate and comment out the call for the arrow

```

button = g_object_new (PANEL_TYPE_MENU_BUTTON,
                               "menu-path", menu_path,
                               "custom-icon", custom_icon,
                               "use-menu-path", use_menu_path,
                               "use-custom-icon", use_custom_icon,
                               [color=red]/* "has-arrow", TRUE, * / <<< (this is what you are commenting out)[/color]
                               NULL);
```[/quote]

---

### Post by mhancoc7 on 2006-06-27
Yes, I see that. I am not able to run the emerge command that is explained in the Gentoo forum post. I am trying to figure out if I can edit a config file on my system to get the effect or if I can do something similiar to the Gentoo forum post in Ubuntu. I know that this is a very trivial thing, but I just want to get it done.
Thanks, Jereme

---

### Post by mhancoc7 on 2006-06-28
Ok, I think I am going to give up on this. It is just a silly little thing anyway.

On the bright side this attempt has lead me to the creation of my new "Ubuntu Human XP" theme. You can check it out here:
[http://ubuntuforums.org/showthread.php?t=205005&highlight=ubuntu+human+xp]("http://ubuntuforums.org/showthread.php?t=205005&highlight=ubuntu+human+xp")

Hope you enjoy!

Jereme

---

### Post by dfego on 2006-07-02
You can't use the emerge command because it's a Gentoo command similar (to my understanding) to our apt-get.  It retrieves a source package and installs it.

---

### Post by mhancoc7 on 2006-07-02
Yeah, I finally figured that out. I felt a little dense for not thinking of that first.
Jereme

---

