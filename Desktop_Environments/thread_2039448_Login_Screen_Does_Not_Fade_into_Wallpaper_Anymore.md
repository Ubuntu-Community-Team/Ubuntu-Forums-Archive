---
title: "Login Screen Does Not Fade into Wallpaper Anymore"
date: 2012-08-08
forum: Desktop Environments
---

### Post by GreenRaccoon on 2012-08-08
Yeah sorry, I didn't really know how to title this. On the login screen of my Ubuntu 12.04, what it USED to do (the default setting) is that it would show the purple screen and then fade into my desktop. However, I changed the login screen wallpaper through Ubuntu Tweak, and now, instead of fading from the purple screen into the wallpaper, it just flashes from the purple screen to the wallpaper.

I've tried a few things, but I'm stuck. I tried going back into Ubuntu Tweak and resetting it to my user wallpaper, but that didn't fix it. I also tried editing the "/usr/share/glib-2.0/schemas/50_unity-greeter.gschema.override" file and removing the "background =..." part, but that didn't help either. I ran "gsettings reset com.canonical.unity-greeter draw-user-backgrounds" to double check, but that didn't work either. (I tried running that last one both through dconf-editor under my main user AND under the lightdm user)

This is a weird issue. I can't find anything about it on the Internet. Maybe I'm typing the wrong things into Google. I don't have to run anything like I have to run "sudo update-grub" after editing GRUB configuration files, do I?

---

### Post by GreenRaccoon on 2012-08-08
Oh, I figured it out. I just reset the background to "/usr/share/backgrounds/warty-final-ubuntu.png". I don't know why I didn't think of that earlier. #-oI did it through dconf-editor under the lightdm user, but I'm sure you can do it through Ubuntu Tweak too.

---

