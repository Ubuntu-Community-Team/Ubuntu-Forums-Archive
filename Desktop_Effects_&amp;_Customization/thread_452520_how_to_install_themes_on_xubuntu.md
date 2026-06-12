---
title: "how to install themes on xubuntu?"
date: 2007-05-23
forum: Desktop Effects &amp; Customization
---

### Post by bosshoof on 2007-05-23
Hi
i want to know how to install themes on xubuntu? 

as i want to have a Vista-like  theme for my desktop

knowing that  Beryl doesn't work fine with me

---

### Post by crimesaucer on 2007-05-23
I use the Terminal to move the theme into my /usr/share/themes directory. Then it shows in my User Interface Settings.

assuming that you have downloaded and unpacked the correct Vista theme directory into your home folder, and have the correct theme engines installed for that Vista theme.

```
sudo mv VistaTheme /usr/share/themes
```

then to check, change directories to your /usr/share/themes directory

```
cd /usr/share/themes
```

now...

```
ls
```

and make sure it's there. It should be, and now open up your User Interface Settings where you can select themes and select your VistaTheme as your new theme.

---

### Post by bosshoof on 2007-05-23
what is the best source to download themes from?

links please 

and in your opinion : what are the best themes ; also need links plz

thanks in advance

---

### Post by crimesaucer on 2007-05-23
For xubuntu, look here: [http://www.xfce-look.org/](http://www.xfce-look.org/)

They have Vista themes if that is what you like. 

I have a theme in there called Xfce-milk: [http://www.xfce-look.org/content/show.php/Xfce-milk?content=58257](http://www.xfce-look.org/content/show.php/Xfce-milk?content=58257)

---

### Post by bosshoof on 2007-05-23
when i extract the theme files i downloaded <size=about 75 KB>
the result is a folder with size 4KB :(

so please  tell me how to correctly unpack the theme files

---

### Post by crimesaucer on 2007-05-23
right click on that folder and select "properties" and look at the Size.

---

### Post by blogmaster on 2007-05-25
> **crimesaucer said:**
> I use the Terminal to move the theme into my /usr/share/themes directory. Then it shows in my User Interface Settings.

assuming that you have downloaded and unpacked the correct Vista theme directory into your home folder, and have the correct theme engines installed for that Vista theme.

```
sudo mv VistaTheme /usr/share/themes
```

then to check, change directories to your /usr/share/themes directory

```
cd /usr/share/themes
```

now...

```
ls
```

and make sure it's there. It should be, and now open up your User Interface Settings where you can select themes and select your VistaTheme as your new theme.


i followed the way u said but i got no theme at System>Preferences>Themes even the theme folder has been correctly copied... what is wrong???

---

### Post by meborc on 2007-05-30
try creating a folder named ".themes" in your home folder (the . in front means it is usually hidden, to see it in nautilus/thunar hit ctrl+H) then copy the tar ball, gzip whatever to that folder... then right-click and select extract here

this should do it

and blogmaster - you probably are running gnome (ubuntu not xfce and xubuntu) as you are trying to look in system>themes, you can just download the tarball to your desktop... open system>themes and DRAG+DROP the file on the desktop to the themes window... this will then install the theme to the system and you are free to delete the file from the desktop

good luck all :)

---

### Post by ap9er on 2007-06-02
Yeah, for themes you put it in home/yourusername/.themes and extract the theme there (the theme should have its own folder inside this directory).

Similar for icons you'd follow the same method but have it in the .icons folder

---

