---
title: "GTK/Human Icons in Beryl"
date: 2007-03-26
forum: Desktop Effects &amp; Customization
---

### Post by Falkon on 2007-03-26
I finally got Beryl running and I love it, but I really hate the ugly gray gnome theme and  icons.  Is there a way to put my old human icons, or any others, into the xgl/beryl desktop?

---

### Post by Lord Illidan on 2007-03-26
I think you need to run gnome-settings-daemon from a terminal.

---

### Post by Falkon on 2007-03-26
Well that works until I close the terminal.  Is there another way to do this, or maybe a script I could make to have that daemon run in the background on XGL startup? (without opening a terminal window)

---

### Post by Lord Illidan on 2007-03-26
Since you are running a seperate session for XGL, go to System -> Preferences -> Sessions -> Startup programs and add the command above.

---

### Post by reclusivemonkey on 2007-03-27
> **Falkon said:**
> I finally got Beryl running and I love it, but I really hate the ugly gray gnome theme and  icons.  Is there a way to put my old human icons, or any others, into the xgl/beryl desktop?

I'm not sure what you mean by this. Beryl should only change the Window Manager theme, not your GTK Theme or your Icons. You can select your icons and gtk theme (which appears as "Controls") in Preferences --> Themes. The human icons should be in "Icons", likewise the human theme in "Controls". The window manager themes are now handled by Beryl, so you can change these in the Beryl settings manager under Emerald. There is a orange human theme in there I believe.

If you are not satisfied with the themes on offer, you can take a look on gnome-look.org where you should be able to find something to your liking. HTH

---

### Post by Lord Illidan on 2007-03-27
> **reclusivemonkey said:**
> I'm not sure what you mean by this. Beryl should only change the Window Manager theme, not your GTK Theme or your Icons. You can select your icons and gtk theme (which appears as "Controls") in Preferences --> Themes. The human icons should be in "Icons", likewise the human theme in "Controls". The window manager themes are now handled by Beryl, so you can change these in the Beryl settings manager under Emerald. There is a orange human theme in there I believe.

If you are not satisfied with the themes on offer, you can take a look on gnome-look.org where you should be able to find something to your liking. HTH

That's not the issue. The issue is that when Beryl/XGL is set up as an xsession, it fails to load the gnome-settings. Changing the icons, etc will not do any difference.

---

### Post by kepos on 2007-03-27
> **Lord Illidan said:**
> I think you need to run gnome-settings-daemon from a terminal.

Thanks! :) :) :)

It worked for me. But, still i am curious why that happened in first place.

---

### Post by Falkon on 2007-03-27
Ok, I added gnome-settings-daemon to startup and it works great!  Thanks, Illidan.

---

