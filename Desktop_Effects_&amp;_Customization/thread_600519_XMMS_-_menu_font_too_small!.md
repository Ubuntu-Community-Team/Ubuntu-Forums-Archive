---
title: "XMMS - menu font too small!"
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by perixx on 2007-11-02
The only problem preventing me from using XMMS is the damn GTK font which is unbearable tiny at 1024x768 resolution (apart from the even smaller frontend-GUI -- who would do such a trashy visual approach in 2007?!)!

How can I assign a better font (Helvetica or Verdana 14-16 point) to XMMS please?? I want to use XMMS because of the huge codecs-support...

I tried to install and use 'gtkfontsel', but no workie.

thanks for the help...


perixx

---

### Post by perixx on 2007-11-03
As far as I understand, the problem is that XMMS is using damn old GTK packages (for whatever reason)...

There must be a comprehensive way to set a new standard font- and size to that GTK package, isn't there ?

How could I do this, please ?

:cry:


perixx

---

### Post by perixx on 2007-11-04
*bump*

---

### Post by Cochise on 2007-11-04
you could try audacious its very similar

---

### Post by perixx on 2007-11-04
Hello Chochise...


- will audacious make use of all the plugins out there for xmms - also some weird ones like m4a, midi, flac, mod... ?

- can I use all the skins from xmms?

- can I switch off cddb, if it's there?

- I had it previously installed; where do I have to place the codecs or where is the config-file to tell the player where to look for the codecs?


perixx

---

### Post by FrankVdb on 2007-11-04
Why would you want to use XMMS? It's development stopped a long time ago.

Try Exaile. Looks a bit like Amarok, only faster.

---

### Post by perixx on 2007-11-04
> Why would you want to use XMMS? It's development stopped a long time ago.

Say, what ?!?


```
http://havardk.xmms.org/dist/cvs/
```


Umm... seems to be pretty much alive to me. The only problem - the dev's of xmms appear to be a little stubborn regarding to switching to GTK+2 (with much better graphics)...?

Besides, I don't want some fancy puffed multmedia center with all the bloat and a freakshow of rather annoying features like 'cover-grabbing', or 'cddb' or even 'submitting my favourite music titles from i-pod' and all that crap. 

All I want is a decently designed player that's stable, has a well-designed playlist-menu, auto-play's CD's and can handle almost every audio-format out there - plus maybe integrates into Firefox.

---

### Post by tgalati4 on 2007-11-04
Click on the "D" on the left side for Double Size.  Cheesy, but it works.

---

### Post by perixx on 2007-11-04
Tgalati, thx for the reply but I was actually looking for a real solution (you know, I already knew that trick)....

Sorry for being a little harsh, but you might have figured out by reading my post a little closer, what I really want to do -- changing the application's configuration- and context menu!

;]

perixx

---

### Post by perixx on 2007-11-04
*bump*

---

### Post by VictorR on 2007-11-04
Try the following steps:
1. Install at least one GTK 1 engine (as far as I know they are not included in Gutsy by default), say something similar to Ubuntu Human:
```
sudo apt-get install gtk-engines-industrial
```

2. download a theme which works with this engine, this, for example:
[http://gnome-look.org/content/show.php/Ubuntu+Dapper+GTK1+theme?content=47104]("http://gnome-look.org/content/show.php/Ubuntu+Dapper+GTK1+theme?content=47104")

3. you may try this, as suggested in the above theme description, to install it:
```
sudo tar jxvf gtk1_ubuntu_theme.tar.bz2 -C /
```

or, if it does not work
3a. just extract **gtkrc** file from the archive to your home folder and rename it to **.gtkrc.mine** (with the dot in front of its name).

4. you may add the following string inside the above file to set the font (shown in bold)
```

        text[NORMAL]      = "#000000"
        text[PRELIGHT]    = "#000000"
        text[ACTIVE]      = "#000000"
        text[SELECTED]    = "#000000"
        text[INSENSITIVE] = "#B3AFAB"


  ** fontset = "-adobe-helvetica-medium-r-normal-*-12-*-*-*-p-*-iso8859-1"**


  engine "industrial" 
    {
      contrast = 1.0
    }
}

```
it should be approximately 47th line.

Maybe you will have to restart X session (logout and login)

---

### Post by perixx on 2007-11-05
Wow, thanks VictorR! :]

I'll have to check this later on! I'm using Xubuntu 7.04 (Feisty) by the way - with Xubuntu-Theme / Clearlooks and Sans12 fonts / Window Systle Sassandra.

By using your method, will I affect those normal Xfce-appearance as well ? Or will it just change the GTK1-looks for applications that use it?


perixx

---

### Post by Cochise on 2007-11-05
xmms plugins and skin will work with audacious and you can turn off cddb in preferances. audacious is the same looks wise as xmms

---

### Post by VictorR on 2007-11-05
This should affect only GTK1 applications. I had the same problem with ancient look and ugly fonts in Lazarus, now it's much better.

BTW I use Beep Media Player, which accepts XMMS skins; not sure about diversity of codecs, but I found everything I wanted.

---

### Post by perixx on 2007-11-05
Thx for your hints !


Currently, I'm having the problem that XMMS won't recognize the installed 'xmms-mp4', 'modplug' and 'amid' plugins...


perixx

---

### Post by perixx on 2007-11-07
Why won't installing those codecs lead to actually itegrating them into xmms?
Someone knows more on that?

perixx

---

