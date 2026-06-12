---
title: "Missing icons"
date: 2006-07-10
forum: Desktop Environments
---

### Post by Owdy on 2006-07-10
I removed some icon themes manually. Now im missing some system icons, like panel-force-quit.png etc. What package i need to reinstall to get those back?

---

### Post by Owdy on 2006-07-10
This is totally messed up. Look my icons :(

---

### Post by dpm on 2006-07-10
Try reinstalling the **ubuntu-artwork** and **gnome-themes** packages for the default dapper theme. That should give you all the default icons. If not, you can also try to install the **tangerine-icon-theme**, on which the ubuntu artwork was originally based, IIRC. All of these are available from the ubuntu repos.

But as I see from your screenshot you are using some other theme, which you should probably install afterwards to get any additional icons it might provide.

Cheers.

---

### Post by Owdy on 2006-07-10
I have tryed those. Same issue with Human theme. Gnome icon theme works, default human not. I miss icons in strange places, see attacment.

---

### Post by dpm on 2006-07-10
> **Owdy said:**
> I have tryed those. Same issue with Human theme. Gnome icon theme works, default human not. I miss icons in strange places, see attacment.

The thing is, you are not using the default Human theme, the default Human icons are orange, not blue as in your screenshot.

I think you should just reinstall whatever customised icon theme you are using.

How did you reinstall **ubuntu-artwork**? Reinstalling that and given that you are saying that the gnome icons are ok, the default Human theme should work, if I'm not mistaken.

Once the default is working, I would concentrate on trying to reinstall your customised version of the Human icon theme.

---

### Post by Owdy on 2006-07-10
> **desp said:**
> The thing is, you are not using the default Human theme, the default Human icons are orange, not blue as in your screenshot. I have tryed with default theme also. It isnt working.


>  How did you reinstall **ubuntu-artwork**? With synaptic. edit: and with 'sudo aptitude reinstall ubuntu-artwork'.

> Reinstalling that and given that you are saying that the gnome icons are ok, the default Human theme should work, if I'm not mistaken.All other icon theme works but ubuntu default and that blue varation of it does not..

---

### Post by Owdy on 2006-07-10
Weirdest thing is, not all icons are missing, just some of them  :confused:

edit: and those icons are in /usr/share/icons/Human/48x48/places etc,

---

### Post by dpm on 2006-07-10
Hmm, I think I cannot be of further help here. Sorry.

On a side issue, I have long given up using the default Dapper theme. It was broken some weeks before release and it still remained inconsistent afterwards.

If everything else fails, you could try using the Tango icon theme. It is available from the ubuntu repos (**tango-icon-theme**), it is quite consistent and it seems to be quite a dynamic and well designed project: [http://tango.freedesktop.org/Tango_Desktop_Project](http://tango.freedesktop.org/Tango_Desktop_Project)

---

### Post by Owdy on 2006-07-10
[]("http://tango.freedesktop.org/Tango_Desktop_Project")I really would like to use Human theme. Does anyone know what file says what images files must use, like folders use this etc? Some file is messed, because some of those images works and some dont. Example web folder image works, common folders doesnt.

---

### Post by Owdy on 2006-07-11
edit: fixed with reinstalling whole Dapper...

---

### Post by domo on 2006-11-18
I had excatly the same probleme.
Don't know how it appear as I always use a custom theme.
But when I create a new account, I saw this folder icons missing.

Try the different things from this post, but without chance.

I finally manage to solve that by replace
```
/usr/share/icons/Human/index.theme
```
by
```
/usr/share/icons/gnome/index.theme
```

I don't know exactly what's wrong with this file by that solve my problem.
I'm happy if tis can help someone.

---

