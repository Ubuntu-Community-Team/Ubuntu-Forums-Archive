---
title: "a Question in the compiz features :)"
date: 2010-12-25
forum: Desktop Environments
---

### Post by q8_legend on 2010-12-25
Is there is a way in compiz to open all the minimized windows in the taskbar  ??

Since I want to use the "scale" feature in compiz for all of the windows ... as what you already know is that, the "scale" feature only works for the open windows not the minimized ones... So i want a way to open all the minimized windows with a shortcut(using compiz or any thing else) and then use the scale feature again :)

---

### Post by q8_legend on 2010-12-26
up up up ...........

---

### Post by stinkeye on 2010-12-26
The only thing I'm aware of is a hack to the scale plugin.
See this thread [**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=1396068[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1396068")

You may need to install wmctrl...
```
sudo apt-get install wmctrl
```

---

### Post by q8_legend on 2010-12-26
its not working for me ... i don't know why!!!!

---

### Post by stinkeye on 2010-12-26
In the terminal run 
```
~/.scale.py
```
to see if script works for you.

Did you make executable?
To make executable...
```
chmod +x ~/.scale.py
```

---

### Post by q8_legend on 2010-12-26
Now it does works... The file wasn't in the right home folder also it wasn't marked as exutable file. because i don't know before how to make it... Now it does works


Thanks you man veryyyyyyyyy much.... it does works great :)

I guess, i will use it instead of the default scale in compiz :)


Man you are awesome :)

---

### Post by stinkeye on 2010-12-26
> **q8_legend said:**
> Man you are awesome :)
That's what I keep telling my self. ;)

Even though it was working without it, when I ran in terminal it said I also 
needed xwit
```
sudo apt-get install xwit
```


PS. You can also make files executable by right clicking on the file > properties > permissions and tick **execute**.


> up up up ..............and away!

---

