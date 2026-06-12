---
title: "Dekorator problem"
date: 2006-03-04
forum: Desktop Environments
---

### Post by heretic9 on 2006-03-04
I tried installing dekorator using the deb from kde look, it installs fine but when I try to install a theme it complains that its not a valid theme. I tried compiling it from source but I get the same problem. Anyone have a solution for this?

---

### Post by Jucato on 2006-03-05
How are you exactly trying to install a deKorator theme file?
Also, take note of the deKorator version that you have and the version that the theme was made for. There might be a conflict there.

---

### Post by heretic9 on 2006-03-05
Its dekorator version 0.3. The theme I tried was blender 0.3, I also tried a couple of others as tests but got the same results. I tried installing the the theme by clicking on add theme in kcontrol and pointing it to the tarball of blender and I tried extracting the tarball in the theme folder. After extraction the theme did not appear under the themes tab. When pointing it to the tarball, it complains that its not a valid theme.

---

### Post by Jucato on 2006-03-05
deKorator themes are not installed through the Theme Manager in KControl.
I'm presuming here that blender 0.3 is a deKorator theme?
I'm not sure if this is still the way it's done in deKorator 0.3 (I'm still using 0.2)
- Go to the Window Decorations settings (KControl > Appearance and Themes > Window Decorations)
- In the Window Decoration main tab, choose deKorator
- then go to the deKorator Themes tab, at the bottom click on Install New Theme (no need to extract the tarball)
- once the new theme is installed, select it, then click "Set Theme Path's" at the bottom.
- then click Apply (you might have to scroll down a bit to see it)

Hope that helps.

---

### Post by heretic9 on 2006-03-05
> - In the Window Decoration main tab, choose deKorator
- then go to the deKorator Themes tab, at the bottom click on Install New Theme (no need to extract the tarball)

Thats exactly when i'm doing. It allows me to browse and I select the tarball then it pauses for a second then says that its not a valid dekorator theme. It never shows up in the theme list below. Maybe I should try 0.2.

---

### Post by Jucato on 2006-03-05
I think there's a problem with that particular Blended theme, the one found in KDE-Look. Try the blended theme that can be found in this sight (this is where I got the one that worked, as well as deKorator 0.3 :D )

[http://www.cheetux.org.il/~motyr/deKorator/0.2andUp-themes/]("http://www.cheetux.org.il/~motyr/deKorator/0.2andUp-themes/")

---

### Post by heretic9 on 2006-03-05
Thanks a lot for that link, worked as advertised  :p

---

### Post by rejser on 2006-04-05
Having another deKorator problem. I've installed it, installed a couple of themes, but when trying to use I loose my boarders. No error log.

---

### Post by dresnu on 2006-05-21
> I loose my boarders
Same problem here.

---

