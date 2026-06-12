---
title: "embedded terminal help"
date: 2009-09-09
forum: Desktop Environments
---

### Post by ithinkitschad on 2009-09-09
Hey I followed [this guide]("http://webupd8.blogspot.com/2009/05/ubuntu-embed-terminal-into-you-desktop.html") for an embedded terminal using compiz. But for some reason when I change the width and height it doesn't seem to make a difference, it covers more than my screen. I'm sure I foolishly missed something simple, any help would be appreciated. My resolution is 1680x1050. I attached a screenshot so you can see what I'm saying. 

Thanks,

---

### Post by ithinkitschad on 2009-09-09
Hey I followed [this guide]("http://webupd8.blogspot.com/2009/05/ubuntu-embed-terminal-into-you-desktop.html") for an embedded terminal using compiz. But for some reason when I change the width and height it doesn't seem to make a difference, it covers more than my screen. I'm sure I foolishly missed something simple, any help would be appreciated. My resolution is 1680x1050. I attached a screenshot so you can see what I'm saying.

---

### Post by ithinkitschad on 2009-09-09
:( Anyone?

---

### Post by nandemonai on 2009-09-10
> **ithinkitschad said:**
> Hey I followed [this guide]("http://webupd8.blogspot.com/2009/05/ubuntu-embed-terminal-into-you-desktop.html") for an embedded terminal using compiz. But for some reason when I change the width and height it doesn't seem to make a difference, it covers more than my screen. I'm sure I foolishly missed something simple, any help would be appreciated. My resolution is 1680x1050. I attached a screenshot so you can see what I'm saying. 

Thanks,

You copied the commands from that howto exactly?

This in particular: 

```
gnome-terminal --window-with-profile=trans777 **--geometry 67x35+220+50** &
```

That geometry line should set the size of the terminal.

---

### Post by ithinkitschad on 2009-09-10
> **nandemonai said:**
> You copied the commands from that howto exactly?

This in particular: 

```
gnome-terminal --window-with-profile=trans777 **--geometry 67x35+220+50** &
```That geometry line should set the size of the terminal.

Yeah I copied it exactly. And I've tried tweaking "**67x35+220+50**" many different ways. Although it doesent make too much sense to me because I dont think thats pixels. Do you know what I should set it to if my resolution is 1680x1050?

---

### Post by mcduck on 2009-09-10
What kind of command are you using to start the terminal? Keep in mind that the size you give to the terminal with the "--geometry" is not defined in pixels (like your display resolution is) but instead in characters. So if you try to set the geometry to 1680x1050 you get a terminal window with 1050 rows and 1680 characters on each row. Definitely much bigger than your screen.. ;)

---

### Post by mcduck on 2009-09-10
Seems that some admin merged the treads.. :)

Anyway, the command is wrong. The geometry option should have an equals sign instead of a space::
```

gnome-terminal --window-with-profile=trans777 --geometry=67x35+220+50 &
```

---

### Post by ithinkitschad on 2009-09-10
Yeah I figured it couldn't be pixels if the example was 67x35.


> **mcduck said:**
> Seems that some admin merged the treads.. :)

Anyway, the command is wrong. The geometry option should have an equals sign instead of a space::
```

gnome-terminal --window-with-profile=trans777 --geometry=67x35+220+50 &
```

No, that didn't seem to do it. Although i was pretty excited when I tried it. Any other ideas? Thank you for your help.

---

### Post by mcduck on 2009-09-10
> **ithinkitschad said:**
> Yeah I figured it couldn't be pixels if the example was 67x35.




No, that didn't seem to do it. Although i was pretty excited when I tried it. Any other ideas? Thank you for your help.

Not really, since that *is* the command used to set the terminal size. :D It definitely works, I'm using pretty much similar setup all the time.

Well, you could make sure that you have no other application (like Devilspie or the Window Rules-plugin in Compiz) that tries to set some other size for the terminal windows.

If you really can't get the command to work you could try using the Window Rules-plugin in Compiz do define the size although I think it tries to set te size in pixels which might or might not work for terminals..

---

### Post by ithinkitschad on 2009-09-10
> **mcduck said:**
> Not really, since that *is* the command used to set the terminal size. :D It definitely works, I'm using pretty much similar setup all the time.

Well, you could make sure that you have no other application (like Devilspie or the Window Rules-plugin in Compiz) that tries to set some other size for the terminal windows.

If you really can't get the command to work you could try using the Window Rules-plugin in Compiz do define the size although I think it tries to set te size in pixels which might or might not work for terminals..

That worked perfect, I used the Window Rules plugin. I was able to specify the size and it works perfectly. Thanks for all your help.

---

