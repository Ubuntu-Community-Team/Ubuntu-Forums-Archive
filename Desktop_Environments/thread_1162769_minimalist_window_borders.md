---
title: "minimalist window borders"
date: 2009-05-18
forum: Desktop Environments
---

### Post by zopanp on 2009-05-18
Hello,
I'm looking for a theme similar to the one that thomas gabriel is using in die hard 4 :

[ATTACH]114199[/ATTACH]

thanks

---

### Post by mcduck on 2009-05-18
I'd say the best way to get as close to that look as possible is to use Emerald, and then create simple window border theme & set the shadow color to light blue, with zero offset on the shadows to get a nice blue glow around the borders.

Window borders with no titlebar/buttons are no problem for Emerald, actually you should be able to find some themes quite like that in gnome-look.org.

---

### Post by zopanp on 2009-05-18
thanks but when i use the command :
```
emerald --replace
```
it does work but as soon as I close the shell then I don't have any border at all...


thanks

I found a way to exit the shell without losing the theme :

```
emerald --replace & disown -a & exit
```

But can anyone make a theme like Thomas gabriel or find one ?

thanks

---

### Post by mcduck on 2009-05-19
> **zopanp said:**
> thanks but when i use the command :
```
emerald --replace
```
it does work but as soon as I close the shell then I don't have any border at all...


thanks

I found a way to exit the shell without losing the theme :

```
emerald --replace & disown -a & exit
```

But can anyone make a theme like Thomas gabriel or find one ?

thanks

Just set Compiz to use Emerald as it's default decorator (instead of loading something else and then using temrinal commands to replace it..)

To do this install CompizConfig Settings Manager if you haven't already got it, then go to Window Decoration-plugin's settings and change the command to "/usr/bin/emerald". Compiz will now start Emerald as it's window decorator automatically.

Also, if you need to run that kind of commands manually (for example while testing stuff), you should press Alt-F2 and use the Run dialog to run the command. That way any processes started will automatically keep on running in the background if needed.

---

### Post by zopanp on 2009-05-22
thanks you,
But can anyone make a theme like Thomas gabriel or find one ?
please this is not indispensable but it would be nice.

thanks

---

### Post by hictio on 2009-05-22
> **zopanp said:**
> thanks you,
But can anyone make a theme like Thomas gabriel or find one ?
please this is not indispensable but it would be nice.

thanks

Ask, and Ye Shall Receive ;)

- [Die Hard 4.0 - Matthew Farrel's theme](http://www.gnome-look.org/content/show.php/Die+Hard+4.0+-+Matthew+Farrel's+theme+(E?content=66714)
- [Die Hard 4.0 - CyberPunk (TPC-SysOP)](http://www.compiz-themes.org/content/show.php/Die+Hard+4.0+-+CyberPunk+(TPC-SysOP)?content=90483)

Those two are Emerald themes, Google is a good friend in this cases too :)

---

### Post by zopanp on 2009-05-23
thanks for your two themes hictio, but i was looking for a theme that look like this ...:[ATTACH]114751[/ATTACH]

---

