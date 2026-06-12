---
title: "HELP!!! emerald in Ubuntu 10.10 I cant switch back to default ubuntu THEME!!! HELP!!"
date: 2010-11-04
forum: Desktop Environments
---

### Post by pinnacle65 on 2010-11-04
I installed this into the console like this site said, It seemed like a good idea. 

> sudo apt-get install compiz compiz-plugins compiz-gnome  compiz-core emerald compiz-fusion-plugins-main  compiz-fusion-plugins-extra fusion-icon compizconfig-settings-manager[http://www.makeuseof.com/tag/5-tools-tips-sexier-ubuntu-interface/](http://www.makeuseof.com/tag/5-tools-tips-sexier-ubuntu-interface/)   

I found that on that site. It seemed like a good idea so I did it,  So I went to emerald Theme Manager and clicked edit themes and played around with those themes there. The Truglass theme. But not I saw that the themes look horrible. I want to go back to my default ubuntu theme!! What do I do!! its not leting switch back to my default theme thru the appearance preferences on my ubuntu. HELP!! Im desperate. I want to get this emerald theme out! its Horrible!!! HELP! THis is driving me nuts Ive been hours trying to figure this out and it just doesnt switch back to my default ubuntu theme! I want to use my default "ambiance" theme from ubuntu! 

[IMG]http://img339.imageshack.us/img339/4826/screenshotpuv.png[/IMG]

---

### Post by ajgreeny on 2010-11-04
I had a similar problem in 9.10, I think it was, where the emerald theme manager kept crashing, and did not actually do anything I asked of it.  I came to the conclusion that it was too much trouble and uninstalled emerald and the theme manager.

For the moment if you don't wan't to remove emerald completely, you can just remove the command **emerald --replace** from the compizconfig-settings-manager **Window Decoration** plugin, if it is enabled there, and replace it with **compiz --replace** or **/usr/bin/compiz-decorator**.  That should give you vanilla compiz with no emerald.

As I understand things, emerald is not being developed further, at the present time, though I have not checked this out at all.

---

### Post by pinnacle65 on 2010-11-04
> **ajgreeny said:**
> I had a similar problem in 9.10, I think it was, where the emerald theme manager kept crashing, and did not actually do anything I asked of it.  I came to the conclusion that it was too much trouble and uninstalled emerald and the theme manager.

For the moment if you don't wan't to remove emerald completely, you can just remove the command **emerald --replace** from the compizconfig-settings-manager **Window Decoration** plugin, if it is enabled there, and replace it with **compiz --replace** or **/usr/bin/compiz-decorator**.  That should give you vanilla compiz with no emerald.

As I understand things, emerald is not being developed further, at the present time, though I have not checked this out at all.


That didnt work!!! the other thing is when I double click the window, Instead of minimizing or maximizing it , it scrolls into itself into a single bar without the window, you double click it again and it spits the window contents back out. Im pissed! I want my ubuntu themes and effects and everything to be back to default factory settings!!!!!!!!!!!!!!

---

### Post by ajgreeny on 2010-11-04
The window blind effect that you speak of, is one of the options of metacity as well so check that you have not enabled it in *gconf-editor* settings.

Look in **apps->metacity->general->action_double_click_titlebar toggle_shade** and change the last bit to **toggle_maximise**

---

### Post by mcduck on 2010-11-04
> **pinnacle65 said:**
> That didnt work!!! the other thing is when I double click the window, Instead of minimizing or maximizing it , it scrolls into itself into a single bar without the window, you double click it again and it spits the window contents back out. Im pissed! I want my ubuntu themes and effects and everything to be back to default factory settings!!!!!!!!!!!!!!

It will work, you just have to log out and back again to see the change.

The double-click on title bar will change back to your old behavior as well, as the default decorator and Emerald have their own settings for this.

---

### Post by shantiq on 2010-11-13
two ways to get back to "normal ubuntu"

1.  alt f2   or terminal and enter    ```
metacity --replace
```

this remove compiz as the main window manager and brings back metacity


2.   **other way and i think more elegant**   since you have installed fusion -icon   is to go to applications/systems tool/compiz fusion icon     and then find the icon on top bar   square blue with white arrow

right-click on it then go to select window manager and click on metacity


as you can see it is easy to return to compiz too

which you can also do with compiz --replace using the alt f2 or terminal route

do not give up on compiz   it is the t-i-t-s   and so is[ beryl]("http://beryl-themes.org/")/emerald   as opposed to default metacity/gtk


play around mayhaps


go to the fusion-icon again   this time click on emerald theme manager  and find many more [here]("http://beryl-themes.org/")   simply import into the theme manager and refresh

there are really nice ones like [pint-reduex]("http://beryl-themes.org/content/show.php/Pint-Reduex+for+Ambiance+theme?content=133732") and many others

---

