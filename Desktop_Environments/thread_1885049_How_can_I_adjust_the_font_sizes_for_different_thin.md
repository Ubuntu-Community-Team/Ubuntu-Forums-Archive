---
title: "How can I adjust the font sizes for different things like in gnome?"
date: 2011-11-22
forum: Desktop Environments
---

### Post by BloomingNutria on 2011-11-22
I just installed Xubuntu 11.10 the other day, and I am completely in love with the aesthetics of it. It doesn't have all the options I am used to from gnome (or at least I have not found them), but I like the way it looks so much that I am willing to put in a bunch of extra work to make it act the way I want just to keep it around. 

The main problem I have, really, is that I cannot seem to figure out how to adjust the font sizes for different things. When I was running Ubuntu 10.04 (my only previous Linux installation), there was a really easy way to do this. All you had to do was go to Appearance Preferences > Fonts, and there was a list of 5 different font options:

Application font
Document font
Desktop font
Window title font
Fixed width font

From this menu, you could chose the actual font as well as the font size for each of these options. 

Is there any way I can get this kind of control in Xubuntu? The thing I most need to do is enlarge the text size in Thunar without blowing everything else up too. Come to think of it, a file manager with a zoom function that increased the size of the text as well as the icons (Thunar's does not seem to) would be pretty good too.

Thanks to everyone for sharing their knowledge.

---

### Post by 2F4U on 2011-11-22
What about using the zoom function accessible through the View menu.
Else, there is Settings -> Settings Manager -> Appearance -> Fonts and Settings -> Settings Manager -> Window Manager -> Style.

---

### Post by BloomingNutria on 2011-11-23
Hmm, unfortunately the zoom function in the view menu is the one I am talking about that does not change the text size, but only enlarges the icons. I did not know about the option to change the window title font, but it doesn't really help me get the text in the file manager larger without disproportionately enlarging everything else. For instance, when I set the default font in the settings manager to 22, which is where I need it to be to get the text in Thunar to the size I need it, the text in the downloads window in Firefox is ridiculously large--much larger than the text in Thunar. Similar things happen with other applications. I don't know why, but I never had this problem in Ubuntu when I changed the application font, which is what I thought the default font in Xubuntu would correspond to.

Is there any way I can get more control over the font sizes?

Thanks to all for sharing their knowledge.

---

### Post by neu5eeCh on 2011-11-23
I've been using Xubuntu since 11.04. I love it, but have never found an option to adjust fonts comparable to G2. Then again, I've never tried that hard. Lack of these options is, in part, what makes XFCE "snappier".

---

### Post by BloomingNutria on 2011-11-23
> **VTPoet said:**
> I've been using Xubuntu since 11.04. I love it, but have never found an option to adjust fonts comparable to G2. Then again, I've never tried that hard. Lack of these options is, in part, what makes XFCE "snappier".

Well I do like the snappiness, but I'd be willing to sacrifice a tiny bit of it to make this happen. There has to be a way to do it, maybe with an add on, or some sort terminal tweak those Linux gurus are always pulling out of their hats. Any know of anything like that? :)

---

### Post by Toz on 2011-11-23
> The thing I most need to do is enlarge the text size in Thunar without blowing everything else up too
Add to, or create if it doesn't exist, the hidden file **.gtkrc-2.0** in our home directory with the contents:
```

style "fonttweak"
{
   font_name = "Sans 16"
}
widget_class "*Thunar*View*" style "fonttweak"

```
Change the value of **font_name** to be whatever font/size combination you want and save the file. 

Either logout and back in again, or change your appearance theme to another and back again for it to take effect.

This font setting will only apply to Thunar (as [per the last directive in that code).

Reference link: [http://thunar.xfce.org/pwiki/documentation/advanced_settings]("http://thunar.xfce.org/pwiki/documentation/advanced_settings")

---

### Post by BloomingNutria on 2011-11-23
> **Toz said:**
> Add to, or create if it doesn't exist, the hidden file **.gtkrc-2.0** in our home directory with the contents:
```

style "fonttweak"
{
   font_name = "Sans 16"
}
widget_class "*Thunar*View*" style "fonttweak"

```Change the value of **font_name** to be whatever font/size combination you want and save the file. 

Either logout and back in again, or change your appearance theme to another and back again for it to take effect.

This font setting will only apply to Thunar (as [per the last directive in that code).

Reference link: [http://thunar.xfce.org/pwiki/documentation/advanced_settings](http://thunar.xfce.org/pwiki/documentation/advanced_settings)

This is perfect, thank you! One small problem however. I must be doing something wrong, because I tried it and nothing changed. The file **.gtkrc-2.0 **did not exist in my home directory, so I created it as a plain text file. I then inserted the code, saved it, and logged out and back in again. And it didn't work. 

Any idea what I did wrong?

Thanks again.

---

### Post by Toz on 2011-11-23
Did you specify a font that you have available on your system? Look at the Fonts tab of the Appearance settings manager to see a list of fonts.

Can you post back the contents of the ~/.gtkrc-2.0 file?

Also, have a look at ~/.xsession-errors to see if there is an error message being logged.

---

### Post by BloomingNutria on 2011-11-23
Here are the contents of the file:

                       #toc, .toc, .mw-warning { border: 1px solid rgb(170, 170, 170); background-color: rgb(249, 249, 249); padding: 5px; font-size: 95%; }#toc h2, .toc h2 { display: inline; border: medium none; padding: 0pt; font-size: 100%; font-weight: bold; }#toc #toctitle, .toc #toctitle, #toc .toctitle, .toc .toctitle { text-align: center; }#toc ul, .toc ul { list-style-type: none; list-style-image: none; margin-left: 0pt; padding-left: 0pt; text-align: left; }#toc ul ul, .toc ul ul { margin: 0pt 0pt 0pt 2em; }#toc .toctoggle, .toc .toctoggle { font-size: 94%; }body { font-family: 'Times New Roman'; font-variant: normal; text-indent: 0in; widows: 2; font-style: normal; font-weight: normal; text-decoration: none; color: rgb(0, 0, 0); text-align: left; font-size: 12pt; }table {  }td { border-collapse: collapse; text-align: left; vertical-align: top; }p, h1, h2, h3, li { color: rgb(0, 0, 0); font-family: 'Times New Roman'; font-size: 12pt; text-align: left; }         style "fonttweak"
    {
    [LEFT]   font_name = "Sans 30"[/LEFT]
    }
    [LEFT]widget_class "*Thunar*View*" style "fonttweak"[/LEFT]
    
   
  

                       
I do have Sans on my system. As for the xsessions error file, I do not really understand it, but here is the last part of it:


                          #toc, .toc, .mw-warning { border: 1px solid rgb(170, 170, 170); background-color: rgb(249, 249, 249); padding: 5px; font-size: 95%; }#toc h2, .toc h2 { display: inline; border: medium none; padding: 0pt; font-size: 100%; font-weight: bold; }#toc #toctitle, .toc #toctitle, #toc .toctitle, .toc .toctitle { text-align: center; }#toc ul, .toc ul { list-style-type: none; list-style-image: none; margin-left: 0pt; padding-left: 0pt; text-align: left; }#toc ul ul, .toc ul ul { margin: 0pt 0pt 0pt 2em; }#toc .toctoggle, .toc .toctoggle { font-size: 94%; }body { font-family: 'Times New Roman'; font-variant: normal; text-indent: 0in; widows: 2; font-style: normal; font-weight: normal; text-decoration: none; color: rgb(0, 0, 0); text-align: left; font-size: 12pt; }table {  }td { border-collapse: collapse; text-align: left; vertical-align: top; }p, h1, h2, h3, li { color: rgb(0, 0, 0); font-family: 'Times New Roman'; font-size: 12pt; text-align: left; }         Error: No running window found
    [LEFT](xfce4-settings-manager:5482): xfce4-settings-manager-DEBUG: geometry = (200,200)[/LEFT]
    
    [LEFT](Thunar:5059): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed[/LEFT]
    [LEFT](xfce4-settings-manager:5521): xfce4-settings-manager-DEBUG: geometry = (200,200)[/LEFT]
    
   
  
Thank you for your help.

---

### Post by BloomingNutria on 2011-11-23
Okay, I do not know what is going on here, but I did not type any of the nonsense you see above. I just tried to post the contents of the files you asked me about twice, and each time it looked fine on preview and then became gibberish when I submitted it. Why is this stuff being inserted into my posts? I have to leave the computer now, but I will do what I have to do to post a correct version of what those files contain tomorrow morning.

Thanks again.

---

### Post by BloomingNutria on 2011-11-24
Okay, I'm doing this from another computer now because when I tried to do it from my Xubuntu desktop an hour again, the same thing happened.

Here are the contents of the .gtkrc-2.0 file:

```


style "fonttweak"

{

  font_name = "Sans 30"

}

widget_class "*Thunar*View*" style "fonttweak"

```Here is the last part of the .xsession-errors file:

```


(Thunar:1433): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed

(thunar:1773): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-settings-manager:1840): xfce4-settings-manager-DEBUG: geometry = (200,200)

NOTE: child process received `Goodbye', closing down

Error: No running window found

(Thunar:1433): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed


```The Thunar 1433 error is new since last night.

Thank you for your help.

---

### Post by Toz on 2011-11-26
I honestly don't know why this isn't working for you. I've tried it on a number of different xubuntu installs and it worked each time for me.

Is your computer a straight install of xubuntu or is it upgraded from ubuntu? Are you running the xfce window manager (xfwm4) or another one?

---

### Post by BloomingNutria on 2011-11-26
It is a straight install of Xubuntu. I reformatted and repartitioned my drive before I put it on. The only thing not "out-of-the-box" about it is that I put my home folder on a separate partition, but that couldn't have anything to do with it, could it? I reformatted that partition as well, so there were no hidden files from Ubuntu still on it when I installed Xubuntu. As for what window manager I'm using, though, how do I find that out?

And why is my clipboard carrying around all that weird code so that I cannot copy and paste into this forum without putting gibberish into the post? Maybe I should just reinstall . . .

Thank you again for your help.

---

### Post by Toz on 2011-11-28
> **BloomingNutria said:**
> It is a straight install of Xubuntu. I reformatted and repartitioned my drive before I put it on. The only thing not "out-of-the-box" about it is that I put my home folder on a separate partition, but that couldn't have anything to do with it, could it? I reformatted that partition as well, so there were no hidden files from Ubuntu still on it when I installed Xubuntu. As for what window manager I'm using, though, how do I find that out?
If it's a straight install, then its xfwm4. You can check to see if its running by:
```
ps -ef | grep xfwm4 | grep -v grep
```

> And why is my clipboard carrying around all that weird code so that I cannot copy and paste into this forum without putting gibberish into the post? Maybe I should just reinstall . . .

Thank you again for your help.
If you remove the .gtkrc-2.0 file, do you still get the thunar error message in appear in your .xsession-errors file?

---

### Post by BloomingNutria on 2011-12-03
I tried to remove the file, but it would not let me open the folder as root to do it (even though I had been able to open it as root before). Then rebooted and my audio stopped working. I decided just to reinstall and try this same process on the new installation once I had everything set up the way I wanted it, but I ran into some booting problems on the new installation, which I am dealing with now. I will have to put this font issue on the back burner until I get my system running properly again. 

When I get everything set up, I will try this fix again and post the results. I suspect it will work fine once everything else is fixed.

I really appreciate the help you have given!

---

### Post by ManualSparrow on 2011-12-04
One thing you could try is using a different file manager, such as Marlin or PCManFM.

Also, I think you used HTML tags instead of Code tags in your earlier post, so it got all screwed up.

---

