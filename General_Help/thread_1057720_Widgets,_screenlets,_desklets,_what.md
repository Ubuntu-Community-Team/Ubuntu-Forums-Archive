---
title: "Widgets, screenlets, desklets, what?"
date: 2009-02-02
forum: General Help
---

### Post by Another Monkey on 2009-02-02
I am just wondering about desktop widgets under Gnome.  I see various screenshots of other people's desktops with funky widgets doing their thing, and am just wondering how they achieve it.

Screenlets seem to be no longer under active development (their website is just a holding page) and a bit buggy; gdesklets seem very basic (and their site is down as well, so I can't find out much more) - I also don't like the way each desklet appears as a new window in the panel.

If people use widgets/desklets, what framework do they recommend?

Cheers.

---

### Post by Jacob Collstrup on 2009-02-02
I use compiz with the cube and all that. The compiz fusion webpage is still up and active I think. On top of that I use awn (Avant windows navigator) so I have a small Mac-like bar at the buttom of my screen. I think compiz has a few widgets and screenlets, but they're docked to the desktop, so it doesn't follow to the other desktops when you rotate the cube.

Jacob

---

### Post by Alfons81 on 2009-02-02
Hi,

I'm using screenlets, and are working good with compiz-fusion. You can download sceenlets software manager from Synaptics.

I could recomend you to download watermark screenlet, it could messure temperature on your computer, active processes...

You are right, it semms that the oficial site of screelenlets is not working as: screenlets.org. But you can find them using the screenlet name on google. For example for watermark: 

[http://linux.softpedia.com/get/Desktop-Environment/Screenlets/WaterMark-37215.shtml](http://linux.softpedia.com/get/Desktop-Environment/Screenlets/WaterMark-37215.shtml) 

If you are using compiz-fusion, I recomend you to treat your screenlets as a widget ( you could do it by right-clik-preferences), and then open the simple compizconfig settings manager, edges tab, and enable the position mouse for see or hide your widgets. Then you will have a clean desktop.

Sorry because of my English, but I hope it could be usefull for you.

---

### Post by Another Monkey on 2009-02-02
Thanks for the replies.  I am running compiz-fusion, so I will try screenlets again.

I am still trying to understand the differences between metactiy, compiz, beryl, compizfusion, emerald etc.  All very confusing to a newbie like me.  I have yet to find documentation that explains it in a clear manner.

---

### Post by Alfons81 on 2009-02-02
If you have thoose kind of doubts, it could be very interesting to visit the first sticky thread on Threads in Forum : Desktop Effects & Customization 

[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

It is very clear and recomend you many good things to do with your compizfusion.

Also talks about screenlets and where you could find them...I forgot it before:

[http://gnome-look.org/?xcontentmode=6700](http://gnome-look.org/?xcontentmode=6700)

In gnome-look also you could find great window borders ( note that they didn't change beryl name for the actual name emerald )then for download your window borders I think you have to go on Beryl. 

Good luck and thanks for answering

---

### Post by DrMelon on 2009-02-02
Compiz Fusion is the latest in both the Compiz and the Beryl projects; they both joined together to make Compiz Fusion. So that's those three dealt with :P.

Emerald is for theme purposes - you can re-theme Ubuntu with it. So you can have shiny window frames and so on, with different colours.

---

### Post by sixpounder on 2009-02-02
> **Another Monkey said:**
> Thanks for the replies.  I am running compiz-fusion, so I will try screenlets again.

I am still trying to understand the differences between metactiy, compiz, beryl, compizfusion, emerald etc.  All very confusing to a newbie like me.  I have yet to find documentation that explains it in a clear manner.
Allright, let's make this a little more clear ;)
Your windows are (basically) composed of two macro-parts:
- Window border
- Window content
To manage them, you must use a Decoration Manager (for window borders) and a Window Manager (for window content)

compiz/compizfusion is a window manager, wich means that it takes care of drawing the contents of your windows. In its general settings, you may specify a Decoration Manager Engine to handle window borders and decorations. Default on ubuntu is gtk-window-decorator. It consists of two themes, Cairo decorations and Metacity decorations and both use GConf to store their settings. In other words, the changes you make in the appearance settings will be applied to those decorations as well as on window content (gtk themes).

Emerald is an alternative Decoration Manager wich you can use with compiz by specifying the emerald --replace command in the compiz settings manager. It has a separated theme manager that you can use to change and manage your window decoration themes.

Hope this can help

---

### Post by Another Monkey on 2009-02-02
Cheers Sixpounder, that is very concise and clear indeed.

Thanks.

---

### Post by Another Monkey on 2009-02-03
I started playing around with screenlets again last night, the "watermark" one is pretty good and I 'll check some others out.

Interestingly, compizfusion does not appear to be a requirement.  I can't run that under virtualisation (which is how I am learning about Linux), but I can run screenlets OK.  I have set metacity as a compositing managers, so I guess that is why.

---

### Post by fabounet on 2009-02-03
you can also try Cairo-Dock, which can detach its applet on the desktop, and place them on the Widget Layer
the advantage is to have a single application for both, and to have real 3D desklets with the 2.0
but there are fewer desklets than in Screenlet so you may have to mix both.

---

### Post by binbash on 2009-02-03
> **Another Monkey said:**
> I started playing around with screenlets again last night, the "watermark" one is pretty good and I 'll check some others out.

Interestingly, compizfusion does not appear to be a requirement.  I can't run that under virtualisation (which is how I am learning about Linux), but I can run screenlets OK.  I have set metacity as a compositing managers, so I guess that is why.

Watermark is cool.HOWEVER screenlets is a dead project...

---

### Post by pritamps on 2009-02-03
Nowadays Google Gadgets is available for Linux as well in all its glory and that seems to be under active development still ;-) It looks good...

---

