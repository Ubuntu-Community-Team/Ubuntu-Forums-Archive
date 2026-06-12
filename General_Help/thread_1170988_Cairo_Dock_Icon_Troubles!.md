---
title: "Cairo Dock Icon Troubles!"
date: 2009-05-26
forum: General Help
---

### Post by megamouthbolt on 2009-05-26
Help!

I was using Cairo-Dock quite happily for a while, and then I decided to customize it a bit. 

I changed the theme, and deciding I didn't like it, I changed it back.

Now, some of the icons are not changing back!

When I modify the launchers to change it back, I realized that the new dock REPLACED some of the default icons!

How do I get the default icon set back?

Note: Complete removal and re-installation did not help. Neither did removing the icons and moving the icons directly in from the application menu.

---

### Post by pastalavista on 2009-05-26
I would try ```
sudo apt-get remove cairo-dock --purge
```

The --purge is to remove config files too. After running it, check your home folder hidden files (use 'ctrl+h' to show/hide hidden files) and delete a folder named .cairo-dock or something similar... (the dot before the file name makes it hidden in case you didn't know)

then reinstall cairo-dock ```
sudo apt-get install cairo-dock
```

---

### Post by megamouthbolt on 2009-05-26
Thank you!

Now for the trouble of recovering my setting.. :P

---

### Post by fabounet on 2009-05-27
also, be sure to have writing permissions on ~/.config/cairo-dock

---

