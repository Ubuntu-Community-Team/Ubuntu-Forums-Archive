---
title: "[SOLVED] The required GTK+ theme engine is not installed."
date: 2009-01-09
forum: General Help
---

### Post by J03y on 2009-01-09
Hello, recently I'm getting this error saying:

```

this theme will not look as intended because the required gtk+ theme engine is not installed
```

This is happening to me recently because the last time that I re-installed Ubuntu and installed the same gtk theme it did not give me any errors. Can anyone help me fix this problem? Thanks in advance. :(

---

### Post by IceReaver75 on 2009-01-09
you have to navigate to the folder the theme is installed in either /home/.themes(hidden) or user/share/themes and open the themes folder you are having problems with.  Open the gtk-2.0 folder and look for the gtkrc file.  Open that file with a text editor and click on find on the top and type in engine and look for all the words that have engine in them.  One of them is going to say:

style "unstyle"
{
engine ""
{}
} 

change that to something like:

style "unstyle"
{
engine "pixmap"
{}
}
or replace "pixmap" with any other engine you know you have installed on your system and it won't complain any more.

There must have been something that has changed with the way themes are written with intrepid cause I have found alot of themes to have that problem now on gnome-look.  I just go through those steps automatically when I download a theme now.

Sometimes you have to check the other rc files in the theme too, like the panel.rc or custompanel.rc if the theme happens to have one.

---

### Post by J03y on 2009-01-09
> **IceReaver75 said:**
> you have to navigate to the folder the theme is installed in either /home/.themes(hidden) or user/share/themes and open the themes folder you are having problems with.  Open the gtk-2.0 folder and look for the gtkrc file.  Open that file with a text editor and click on find on the top and type in engine and look for all the words that have engine in them.  One of them is going to say:

style "unstyle"
{
engine ""
{}
} 

change that to something like:

style "unstyle"
{
engine "pixmap"
{}
}
or replace "pixmap" with any other engine you know you have installed on your system and it won't complain any more.

There must have been something that has changed with the way themes are written with intrepid cause I have found alot of themes to have that problem now on gnome-look.  I just go through those steps automatically when I download a theme now.

Sometimes you have to check the other rc files in the theme too, like the panel.rc or custompanel.rc if the theme happens to have one.....when i changed it, it changed the whole configuration of the theme into the actual theme engine that I used to replace "pixmap".  And pixmap didn't work for me.

---

### Post by IceReaver75 on 2009-01-09
can you let me know what theme you are trying to use.  I can take a look and see what is going on in the gtkrc file for you if you would like.

---

### Post by J03y on 2009-01-09
> **IceReaver75 said:**
> can you let me know what theme you are trying to use.  I can take a look and see what is going on in the gtkrc file for you if you would like.Oops sorry about the late reply, hope its not too late, :). Its: [http://www.gnome-look.org/content/show.php?content=79463&forumpage=0](http://www.gnome-look.org/content/show.php?content=79463&forumpage=0)

---

### Post by dkev on 2009-01-09
Na, it's just a glitch. There's nothing actually wrong. Just ignore the prompt.

---

### Post by IceReaver75 on 2009-01-09
Alright I looked into the theme and I changed this in the gtrk file to this:

style "unstyle"
{
engine ""
{}
}

change that to something like:

style "unstyle"
{
engine "pixmap"
{}
}

And then you have to open the panel.rc file and go down to line 126 and change that engine "" to engine "pixmap"

after that the gtk theme "" should disappear but it might complain about a icon theme not being installed cause this theme calls for the Titanium icon theme.

If you dont download that icon theme you can open the index file inside the theme folder with 
sudo gedit and navigating to the index file and change the icon theme = line with a icon theme you have installed on your system.

everything should work after that.  Everything works on my system after changing those options in the theme folder.

---

### Post by BigSilly on 2009-01-10
> **IceReaver75 said:**
> you have to navigate to the folder the theme is installed in either /home/.themes(hidden) or user/share/themes and open the themes folder you are having problems with.  Open the gtk-2.0 folder and look for the gtkrc file.  Open that file with a text editor and click on find on the top and type in engine and look for all the words that have engine in them.  One of them is going to say:

style "unstyle"
{
engine ""
{}
} 

change that to something like:

style "unstyle"
{
engine "pixmap"
{}
}
or replace "pixmap" with any other engine you know you have installed on your system and it won't complain any more.

There must have been something that has changed with the way themes are written with intrepid cause I have found alot of themes to have that problem now on gnome-look.  I just go through those steps automatically when I download a theme now.

Sometimes you have to check the other rc files in the theme too, like the panel.rc or custompanel.rc if the theme happens to have one.

Thanks very much. This fixed a problem I was having with the Ice theme. :)

---

### Post by Sumerian on 2009-06-06
Hi, i have the same problem

the link of my theme is : [http://www.junauza.com/2008/08/10-beautiful-themes-for-ubuntu-intrepid.html](http://www.junauza.com/2008/08/10-beautiful-themes-for-ubuntu-intrepid.html)

the theme is called orange door hinge,

Thank You

---

### Post by amr2205 on 2011-07-11
> **BigSilly said:**
> Thanks very much. This fixed a problem I was having with the Ice theme. :)

Yeap, it did worked for me too!

---

