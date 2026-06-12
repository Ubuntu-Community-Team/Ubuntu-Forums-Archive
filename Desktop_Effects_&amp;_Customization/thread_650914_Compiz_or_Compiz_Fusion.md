---
title: "Compiz or Compiz Fusion"
date: 2007-12-26
forum: Desktop Effects &amp; Customization
---

### Post by Sistum Id on 2007-12-26
I installed Ubuntu 7.10 Gutsy Gibbon and from what I read Compiz comes installed. But I also read that Compiz Fusion is that one that is already installed when you install Ubuntu 7.10 Gutsy Gibbon. 

I managed to get Compiz up and running  but noticed after I "unlocked" Compiz there is Compiz and Compiz Fusion. I thought it was one thing and when people said Compiz I thought it a short cut. 

So now I want to know whats the difference between Compiz and Compiz Fusion? Are there more effects, faster, easier? Also if Compiz Fusion offers more then how hard would it be to upgrade from Compiz? Ive read other threads on upgrading but it seems to cover people running Fiesty and not Gusty. Thanks

---

### Post by chewearn on 2007-12-27
Here:
[http://wiki.compiz-fusion.org/CompizFusionVsCompiz](http://wiki.compiz-fusion.org/CompizFusionVsCompiz)

---

### Post by Sistum Id on 2007-12-27
Ah thanks for that, that site didnt help but it did take me to another site explaining the menus for CCSM and I found what I was looking for!! Thanks alot! 

1 more question, when I have the 3d cube and its moving around the lines are jagged. Is that normal or is that cause I have a very low end old gpu card?

---

### Post by chewearn on 2007-12-27
> **Sistum Id said:**
> Ah thanks for that, that site didnt help but it did take me to another site explaining the menus for CCSM and I found what I was looking for!! Thanks alot! 

1 more question, when I have the 3d cube and its moving around the lines are jagged. Is that normal or is that cause I have a very low end old gpu card?

What GPU do you have?

---

### Post by Sistum Id on 2007-12-27
> **AstalaVista said:**
> What GPU do you have?

Laptop Nvidia 5200Go.


What is the difference between GLX and XGL?

---

### Post by chewearn on 2007-12-27
> **Sistum Id said:**
> Laptop Nvidia 5200Go.

That's not too bad.  You could probably minimize the jagged lines by messing with some settings (though I'm not sure which).


> What is the difference between GLX and XGL?They are two completely different things.

From Wikipedia:
[http://en.wikipedia.org/wiki/GLX](http://en.wikipedia.org/wiki/GLX)
**GLX** (initialism for "Open**GL** Extension to the **X** Window System") provides the [binding]("http://en.wikipedia.org/wiki/Binding_%28computer_science%29") connecting [OpenGL]("http://en.wikipedia.org/wiki/OpenGL") and the [X Window System]("http://en.wikipedia.org/wiki/X_Window_System"): it enables programs wishing to use OpenGL to do so within a window provided by the X Window System.

[http://en.wikipedia.org/wiki/XGL](http://en.wikipedia.org/wiki/XGL)
**Xgl** is an [X server]("http://en.wikipedia.org/wiki/X_Window_System") architecture designed to take advantage of modern graphics cards via their [OpenGL]("http://en.wikipedia.org/wiki/OpenGL") drivers, layered on top of [OpenGL]("http://en.wikipedia.org/wiki/OpenGL") via [glitz]("http://en.wikipedia.org/w/index.php?title=Glitz_%28software%29&action=edit").

---

### Post by Sistum Id on 2007-12-27
Do I need to uninstall GLX to install XGL?

[http://ubuntuforums.org/showthread.php?t=127090]("http://ubuntuforums.org/showthread.php?t=127090")

Would that help me install XGL?

Or something easier cause wow thats alot of steps...

---

### Post by chewearn on 2007-12-27
> **Sistum Id said:**
> Do I need to uninstall GLX to install XGL?

[http://ubuntuforums.org/showthread.php?t=127090](http://ubuntuforums.org/showthread.php?t=127090)

Would that help me install XGL?

Or something easier cause wow thats alot of steps...

You already have gutsy and nvidia, you don't need to do the steps there.  Your compiz already set-up and working.

---

### Post by Sistum Id on 2007-12-27
I want to use gxwd themes and from what I read I think I need XGL installed. Right?

---

### Post by chewearn on 2007-12-27
> **Sistum Id said:**
> I want to use gxwd themes and from what I read I think I need XGL installed. Right?

[http://en.wikipedia.org/wiki/Cgwd](http://en.wikipedia.org/wiki/Cgwd)

> **Emerald Window Decorator** (formerly known as **cgwd**, which stands for **C**ompiz **G**eneric **W**indow **D**ecorator), is a [window decorator]("http://en.wikipedia.org/wiki/Window_decorator") for the [Compiz]("http://en.wikipedia.org/wiki/Compiz") [compositing window manager]("http://en.wikipedia.org/wiki/Compositing_window_manager") written by Quinnstorm.


So, you install emerald instead:
```
sudo aptitude install emerald
```

no need to mess with xgl or glx.

---

### Post by Sistum Id on 2007-12-27
> **AstalaVista said:**
> [http://en.wikipedia.org/wiki/Cgwd](http://en.wikipedia.org/wiki/Cgwd)



So, you install emerald instead:
```
sudo aptitude install emerald
```

no need to mess with xgl or glx.

Do I still get to do my 3D cube? Do I need to uninstall anything as well?

---

### Post by chewearn on 2007-12-27
> **Sistum Id said:**
> Do I still get to do my 3D cube? Do I need to uninstall anything as well?

No need to uninstall anything.  To get 3D cube, you need to install CCSM:

```
sudo aptitude install compizconfig-settings-manager
```

Then, you will get a new menu entry "Advanced Desktop Effects Settings", under System > Preferences.  Here, you can set the various effects, including 3D cube.

---

### Post by chewearn on 2007-12-27
Oh, and for Emerald, you also get a menu entry: Emerald Theme Manager.

---

### Post by Sistum Id on 2007-12-27
Yeah thanks, i got the Emerald Themer running but...maybe its noobish but how do I apply it. I got one imported but can apply it...

---

### Post by chewearn on 2007-12-27
> **Sistum Id said:**
> Yeah thanks, i got the Emerald Themer running but...maybe its noobish but how do I apply it. I got one imported but can apply it...

Everytime you click on a new theme (in the Theme Manager), it should be applied immediately.

---

### Post by Sistum Id on 2007-12-27
What if it doesn't?

---

### Post by chewearn on 2007-12-27
> **Sistum Id said:**
> What if it doesn't?

If you haven't restart since installing emerald, try that.

Else... I have seen this problem before, but could not solve it.  Here is an unanswered thread with same problem:
[http://ubuntuforums.org/showthread.php?t=609894](http://ubuntuforums.org/showthread.php?t=609894)

---

### Post by Sistum Id on 2007-12-27
Slowly getting there LOL. Ok now the top and bottom title bars are still bland...is that normal?

---

### Post by chewearn on 2007-12-27
> **Sistum Id said:**
> Slowly getting there LOL. Ok now the top and bottom title bars are still bland...is that normal?

Yeah, compiz don't change that for you.  You use the "regular" window theme to change.  However, compiz can make it transparent.  Use CCSM, go to General Options, Opacity Settings tab, Add an item call "dock" (you need to type into the box), then set the opacity to your liking.

---

### Post by Sistum Id on 2007-12-27
I found this theme I wanna install and am not to keen on how to install on ubuntu

Its says to do this

1. Open a terminal
2. cd to the directory the script is in.
3. type "sh INSTALL" without quotes
4. Follow instructions once it is finished.

I got step 1, but step 2 and 3 throw me off. Any help thanks

---

### Post by chewearn on 2007-12-27
> **Sistum Id said:**
> I found this theme I wanna install and am not to keen on how to install on ubuntu

Its says to do this

1. Open a terminal
2. cd to the directory the script is in.
3. type "sh INSTALL" without quotes
4. Follow instructions once it is finished.

I got step 1, but step 2 and 3 throw me off. Any help thanks

First off, you should be careful when running scripts off the internet; this is a common way where a linux machine can be compromised (since viruses and spywares are almost impossible to infect a linux machine).

Second, can give the link to this theme.

Third:
step 2: cd to the directory...
This mean change directory.  Simply type the command "cd <dir>" in the terminal (without quotes). Replace <dir> with the actual directory.

step 3: type "sh INSTALL"
Basically, what is say.  Type it in the terminal.

---

