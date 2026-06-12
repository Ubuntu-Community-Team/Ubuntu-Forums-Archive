---
title: "conky added from theme.."
date: 2011-01-01
forum: Desktop Environments
---

### Post by gmenfan83 on 2011-01-01
i downloaded the slicknesS black theme and there seems to be a pre installed conky that comes with it.....i can find the conky script in the extracted themes folder i downloaded and open it with gedit and either try to change the conky script from their or my own personal conky folder (which worked fine prior to this)but if i add a script from the theme conky folder or my own nothing happens.....here is my output after i type gedit ```
~/Conky/conkymain
```(which is my own conky folder)

(gedit:5111): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",

now this will bring me into g edit to edit my script but after i change and apply it nothing changes
edit:the script is actually 
gedit ~/Conky/conkymain

sorry screwed up while posting

---

### Post by stinkeye on 2011-01-02
I don't really understand what your trying to do, but for your information:

running "**conky**" will load your **~/.conkyrc** config

while

running "**conky -c /path/to/your/config"**
can be used to specify a config to run.


Therefore to run your **~/Conky/conkymain** config and see the changes 
you would need to use
```
conky -c ~/Conky/conkymain
```

---

### Post by gmenfan83 on 2011-01-02
> **stinkeye said:**
> I don't really understand what your trying to do, but for your information:

running "**conky**" will load your **~/.conkyrc** config

while

running "**conky -c /path/to/your/config"**
can be used to specify a config to run.


Therefore to run your **~/Conky/conkymain** config and see the changes 
you would need to use
```
conky -c ~/Conky/conkymain
```
thank you stinkeye,,,,i already have that down pat ,,,but whenever i load the conky with that script nothing happens anymore(it did prior to this theme)

i am sorry for the confusing post .....in short i added a theme that seems to have come with a conky......i found the conky script for the theme and deleted it since i use my own.....since then i cant load a conky from my own conky script folder or the themed one

hope i clarified a little more and again my apologies for the confusing post

update: i was able to get my script to apply ,,,i reloaded the theme and restarted my laptop then added my own script as i usually do and my conky was  applied and not the conky that came with the theme,,,,,,a question i still have though is when i type my path for my conky script through gedit i still get the gtk module path error (although i can still go on and load my conky)i am wondering what its all about,,,,is it because the themed conky was in a gtkrc folder that came with the theme??

---

### Post by stinkeye on 2011-01-02
The error is because the theme uses the ubuntulooks engine which I don't think is available for maverick.

A gtk engine is like the framework of a theme that sets the look & feel of the GTK widgets (buttons, progress bar, entry field, etc)
If you don't have the gtk2-engines-ubuntulooks package installed the theme will work,
but may not look as intended.

Can you post a link to the theme you downloaded?

---

### Post by gmenfan83 on 2011-01-02
> **stinkeye said:**
> The error is because the theme uses the ubuntulooks engine which I don't think is available for maverick.

A gtk engine is like the framework of a theme.
If you don't have the gtk2-engines-ubuntulooks package installed the theme will work,
but may not look as intended.

Can you post a link to the theme you downloaded?thank you for the explanation as it makes sense now ,,especially when i just went to that link again and i see it says gtk /theme.....is this a big deal since i am now able to add my own conky again?....heres the link
[http://gnome-look.org/content/show.php/SlicknesS-black?content=129873](http://gnome-look.org/content/show.php/SlicknesS-black?content=129873)

---

### Post by stinkeye on 2011-01-02
> **gmenfan83 said:**
> thank you for the explanation as it makes sense now ,,especially when i just went to that link again and i see it says gtk /theme.....is this a big deal since i am now able to add my own conky again?....heres the link
[http://gnome-look.org/content/show.php/SlicknesS-black?content=129873](http://gnome-look.org/content/show.php/SlicknesS-black?content=129873)

No, if your happy with the look of the theme just ignore it.
[-(\\:D/

---

### Post by gmenfan83 on 2011-01-02
> **stinkeye said:**
> No, if your happy with the look of the theme just ignore it.
[-(\\:D/
cool thank you for your help:p

---

### Post by stinkeye on 2011-01-02
> **gmenfan83 said:**
> cool thank you for your help:p
No problem.

P.S. There is no conky config file in the SlicknesS theme.
Many files are appended with **rc** and usually means it's a config or
preferences file.
eg conky looks for ~/.conkyrc to load your config

whereas 

if you open a terminal it will look for ~/.bashrc to load a config for how the terminal looks and behaves.

---

### Post by gmenfan83 on 2011-01-02
> **stinkeye said:**
> No problem.

P.S. There is no conky config file in the SlicknesS theme.
Many files are appended with **rc** and usually means it's a config or
preferences file.
eg conky looks for ~/.conkyrc to load your config

whereas 

if you open a terminal it will look for ~/.bashrc to load your saved preferences for how the terminal looks and behaves.
thank you for this explanation as well ...i have no idea where that conky came from and assumed it was part of the theme ,,,then i went browsing around in the theme folders and found the gtkrc file and thought that was a conky script....either way its working fine so i will leave it be

---

