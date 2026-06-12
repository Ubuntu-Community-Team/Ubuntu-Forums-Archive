---
title: "Confusion about Compiz, Emerald and how they work"
date: 2011-04-12
forum: Desktop Environments
---

### Post by group256 on 2011-04-12
Dear all,

This evening, I tried to install Emerald on my Ubuntu 10.10 to get some vista look on my windows decorations. After installing the Emerald Themer, I did run the command "emerald --replace" and I did get a transparent windows decoration however there was no way for me to change it.

I tried, double click, single click, triple click and so on on Emerald themer but I could not change my windows Decoration.

I played around with ccsm, still didn't manage to solve the problem.

Does anyone have any idea what the problem is??

Meanwhile, I would like to ask those involved in development of Gnome to give me a quick intro on how actually all these work. I am really confused about how they actually decorate and control. Once I engage Emarald now my "windows Move" configuration set in Compiz start to work but if I run "metacity --replace" then none of those animations work. Although before installing Emerald they worked with metacity.

Please, any help and guidance is much appreciated.

Thank you and sorry for the long description.

---

### Post by stinkeye on 2011-04-12
Metacity is the default window manager and controls the window, titlebar and borders.(emerald does not work with metacity)

Compiz is a compositing window manager which needs either **gtk-window-decorator** (gives the titlebar and borders the same look as your Metacity theme) 
or **emerald** to draw the titlebar and border.


When running compiz you can change to **emerald** as the window decorator with
```
emerald --replace
```


or
Change to **gtk-window-decorator** with
```
gtk-window-decorator --replace
```


Once emerald is running you can change the theme in Emerald Theme Manager 
by just selecting it.

---

### Post by Copper Bezel on 2011-04-12
> Once I engage Emarald now my "windows Move" configuration set in Compiz start to work but if I run "metacity --replace" then none of those animations work. Although before installing Emerald they worked with metacity.

If you didn't change your default decorator, logging out and logging back in will return your Metacity-styled decorations. You could also kill emerald, run metacity, and run compiz --replace again.

---

### Post by group256 on 2011-04-17
Thank you everyone.

stinkeye, I did what you said, the only thing it does is brings back my normal metacity window decoration. The problem with me is that currently, when I run the 
```
compiz --replace
```

What I get is one single ugly window decoration which I can not change. I am also unable to use Emerald themer to import any themes into it and it pops the error:
> Error calling tar.

I really don't know what is wrong.

---

### Post by Copper Bezel on 2011-04-17
You'll get that message if the file you're selecting from the Import dialog isn't a valid Emerald theme archive, but if it's a valid theme, it should import.

---

### Post by stinkeye on 2011-04-17
> **group256 said:**
> Thank you everyone.

stinkeye, I did what you said, the only thing it does is brings back my normal metacity window decoration. The problem with me is that currently, when I run the 
```
compiz --replace
```

What I get is one single ugly window decoration which I can not change. I am also unable to use Emerald themer to import any themes into it and it pops the error:


I really don't know what is wrong.

So if you hit alt+f2 and run 
```
compiz --replace
```
(Verify you have compiz running by rotating the cube.)

Followed by 
```
emerald --replace
```
you don't get emerald themed titlebar and borders?


Also check in Emerald Theme manager that the appropriate Engine is installed.

---

### Post by group256 on 2011-04-17
Thanks again both you guys for your quick replies.

OK, regarding the cube, yes, it works. All I get, I've captured, please take a look at the attachments.

I have so many different engines by the way. Don't know where they came from!

By the way, under my Visual effects tab, none of the radio buttons are chosen.

---

### Post by stinkeye on 2011-04-17
Try setting your compiz settings back to default with 
```
gconftool-2 --recursive-unset /apps/compiz
```
Warning this will reset any changes you have made in ccsm.


Then alt+F2 
```
compiz --replace
```

then
```
emerald --replace
```


Now open Emerald Theme Manager
and see if you can change the theme from the themes tab.


As a last resort open synaptic and completely remove emerald then install emerald.

P.S.
fusion-icon provides an easy way to change window manager/decorators with a
notification area icon.
Once installed you will find it in Menu > System Tools > Compiz fusion icon.
sudo apt-get install fusion-icon

---

### Post by group256 on 2011-04-19
Nope, still no difference. I am still stuck with the ugly window decorador. I really have no idea how to fix this.

I tried on my friend's laptop, worked on first try with no problem. Don't know what is wrong with mine.

Could it be due to some programs or software I've installed???

---

### Post by stinkeye on 2011-04-19
Try deleting your **.emerald** folder in your home directory (ctrl+h to show hidden files) and then
go to synaptic and reinstall emerald. **[COLOR="Red"]Edit[/COLOR]** #-o I've already said that ,eh.
Only other thing I can think of is a GFX card issue.
```
lspci | grep VGA
```
will give your Gfx.
Sis GFX used to have problems.

...and another thing you could try is, creating a new user account and see 
if emerald works in that account.

---

### Post by group256 on 2011-04-19
Stinkeye, 

Thank you so much. Yes, I removed the .emerald folder and now I imported the themes and it's actually working!!!

Let me mention here for those who having the same problem, it seemed that somehow my .emerald folder permission was set to "root". So I had to login to root in order to remove the folder and then add my themes. (That's why probably themes couldn't be imported).

Anyway, thanks again and I'm setting this as solved.

---

