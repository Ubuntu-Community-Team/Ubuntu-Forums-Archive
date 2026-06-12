---
title: "gDesklet starterbar"
date: 2006-02-07
forum: Desktop Environments
---

### Post by m3ck4rn on 2006-02-07
Hello!
I'm playing around with gDesklet... 
I found plugin, starterbar.
It is cool, but it vould be way much cooler if the black area would be transparant...:cool: 
[img]http://spacelabfilm.ath.cx/gDesklet.png[/img]

Is it possible to get it to be transparant?

---

### Post by byen on 2006-02-07
What happens when you right click on the gdesklets icon in the taskbar and do >configuration>Xcomposite manager>translucency (try unchecking it) and restart gdesklets...
hope it helps.

---

### Post by cbudden on 2006-02-07
I asked myself this question recently and found the answer.  If you want the boarder line to stay, but the rest to be transparant, create a transparant image in The Gimp, or just use mine - ( [http://static.flickr.com/21/96931371_1668b9aee9_o.png](http://static.flickr.com/21/96931371_1668b9aee9_o.png) ), and in the properties of the desklet, use that as a background.  If you want the border to go aswell, we need to edit the desklet file. 

```
sudo gedit /usr/share/gdesklets/Displays/starterbar-desklet/starterbar.display 
```

Then find this section:
```

 <!-- the panel with borders 

  <frame watch="x=iconbar:panel-x, y=iconbar:panel-y,
                width=iconbar:panel-width, height=iconbar:panel-height"
         border-width="4, 4, 4, 4"
         border-uris="gfx/bg-w.png, gfx/bg-n.png, gfx/bg-e.png, gfx/bg-s.png,
                      gfx/bg-nw.png, gfx/bg-ne.png,
                      gfx/bg-se.png, gfx/bg-sw.png">
    <group id="panel" bg-color="#3a416ba0" width="100%" height="100%"
           watch="bg-uri=iconbar:background"/>
  </frame>
  -->

```
Notice I have extended the whole section to be a comment (the --> at the end of the section rather than after "The panel with borders".  Save the file and restart the desklet and it should be all gone.

HTH

Chris


EDIT

Oops, the image you posted didn't load the first time, so the fix may not work.  Try restarting the desklet or changing your wallpaper to something else and then back again.

---

### Post by m3ck4rn on 2006-02-08
[QUOTE=byen]What happens when you right click on the gdesklets icon in the taskbar and do >configuration>Xcomposite manager>translucency (try unchecking it) and restart gdesklets...
hope it helps.[/QUOTE]

That worked fine! 
thank you.

now I found another problem...
when I start Firefox from there. it start with the page [http://www.arizona.edu/](http://www.arizona.edu/)
even if my startpage is something else.

---

### Post by arctic on 2006-02-08
Edit the starter entry for firefox. It will tell you that the executable is /sbin/firefox/%u or something like that. Simply remove the garbled stuff behind "firefox" in that line.

---

### Post by aliencds on 2006-02-08
how sdo you even get this gdesklet?

---

### Post by m3ck4rn on 2006-02-09
It works fine now thank you all.
I like this one very much :)

I don't know exaktly how I got it... I found a link to it somwere in this forum i belive. and installed it... but that was a while ago... I havn't use gDesklet until now.

---

### Post by jasay on 2006-02-09
[QUOTE=aliencds]how sdo you even get this gdesklet?[/QUOTE]Install gdesklets it you haven't from synaptic/apt.  Starterbar *might* be in gdesklets-data.  If not, [grab this.]("http://gdesklets.gnomedesktop.org/files.php?func=gd_downloadfile&gd_filename=starterbar-desklet-0.31.3.tar.gz&gd_fileid=742")  Then open gdesklets and drag the package into it.  Check [gdesklets.gnomedesktop.org]("http://gdesklets.gnomedesktop.org") (old) and [www.gdesklets.org](www.gdesklets.org) (new but not all up and running) for other desklets.

Edited for clarity and correct url.

---

### Post by lmivan on 2007-06-14
> **byen said:**
> What happens when you right click on the gdesklets icon in the taskbar and do >configuration>Xcomposite manager>translucency (try unchecking it) and restart gdesklets...
hope it helps.

Hi,

when I change translucency option and restart gdesklet, the starterbar's background is black!. In the check there is a text: "It does not work with GTK 2.8 for technical reasons". 

I run ubuntu feisty fawn and beryl works ok, so why I can't get this background transparent?.

Regards, Iván.

---

### Post by rvperez on 2007-09-20
I can't get transparency in Gdesklets I had it but i lost it before install someone, I had trying desk like cube with "beryl" but transparency of gdesklet dissapear

Thank you very much

---

### Post by dkaddict on 2007-11-02
For what it's worth I thought I may as well show how I amend the file relating to the gdesklets 'starterbar' desklet.

The reason behind my saying the following is because the method explained by cbudden stops the starterbar from loading any background should one wish to use one. I am not knocking that method, it works perfectly if you want a transparent background and nothing else. The way that I will show gets around this problem because it doesn't involve commenting anything out in the starterbar script. In short, it stops the border being drawn and at the same time allows the user to load an image for the starterbar background.

here's how it is done>>>

open a terminal and enter>>>

```
sudo gedit /usr/share/gdesklets/Displays/starterbar-desklet/starterbar.display
```

*as you can see, it opens the same file as per the other method.

When gedit opens, again scroll down to the section which looks like this>>>

```
<!-- the panel with borders -->

  <frame watch="x=iconbar:panel-x, y=iconbar:panel-y,
                width=iconbar:panel-width, height=iconbar:panel-height"
         border-width="4, 4, 4 4"
         border-uris="gfx/bg-w.png, gfx/bg-n.png, gfx/bg-e.png, gfx/bg-s.png,
                      gfx/bg-nw.png, gfx/bg-ne.png,
                      gfx/bg-se.png, gfx/bg-sw.png">
    <group id="panel" bg-color="#3a416ba0" width="100%" height="100%"
           watch="bg-uri=iconbar:background"/>
  </frame>

```

find the line which reads>>>
```
border-width="4, 4, 4, 4"
```

and change all of the 4s to 0 (that's a zero not an o):confused:

so that it looks like this>>>>

```
border-width="0, 0, 0, 0"
```

That's it. Now close gedit and restart the gdesklets daemon (right click on icon in system tray and choose 'Stop daemon'. Restart gdesklets and that background will be removed. Because the code for the background image hasn't been commented out, however, it remains possible to choose an image for the background if one chooses to do so.

Hope it may be of some help.

Peace

dk

---

### Post by Quash on 2007-11-19
> **lmivan said:**
> Hi,

when I change translucency option and restart gdesklet, the starterbar's background is black!. In the check there is a text: "It does not work with GTK 2.8 for technical reasons". 

I run ubuntu feisty fawn and beryl works ok, so why I can't get this background transparent?.

Regards, Iván.


There is a very very near transparent png included in gdesklets.  Worked for me.  its in usr/share/gdesklets/themes

from there you can pick and choose which one you want.  I think I picked the light alpha bg

Im running 7.10 without the compiz crap.  gDesklets gets the job done

---

### Post by BLTicklemonster on 2008-03-24
Time to resurrect an old thread. Hot dang, thanks folks!!! I've messed with awn, and it's too buggy for me. I like gdesklets' starterbar just fine, thank you very much, though I think some more could be done with it.

Here's what I just did. Created a 128x128 gradient, black foreground to transparent, used it for my background, then removed the border.

[[IMG]http://img248.imageshack.us/img248/6408/gradientnobordergeskletuo1.th.jpg[/IMG]](http://img248.imageshack.us/my.php?image=gradientnobordergeskletuo1.jpg)

Now to see if I can figure out how to edit the background script to allow me to use a curved background. Is it possible to make the background use three images? 1 would curve from the left, 2 would be solid across the starterbar, and 3 would curve to the right. Yeah, over my head...

---

### Post by BLTicklemonster on 2008-03-26
Okay, I made a transparent image, and used it for the background, then edited the script to get rid of the border. Upon reboot, the border's there again, and it's reverted back to the old background. I edited the /home/bill/.gdesklets/* script as well as the /usr/* script. What do I do?

---

