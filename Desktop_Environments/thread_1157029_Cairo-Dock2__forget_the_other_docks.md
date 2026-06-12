---
title: "Cairo-Dock2 : forget the other docks"
date: 2009-05-12
forum: Desktop Environments
---

### Post by fabounet on 2009-05-12
here it is, the final release of Cairo-Dock2 is available in 32 and 64bits.
If you liked Cairo-Dock, you will love Cairo-Dock2, if you didn't like it, you should really get a try !

the easy way to install it : [http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en#7-Ubuntu]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en#7-Ubuntu")

then :
  Applications -> System -> cairo-dock
or
  Applications -> System -> glx-dock
according to your graphic drivers.

A list of news can be found here : [http://www.cairo-dock.org/mr_article.php?b=5&a=42]("http://www.cairo-dock.org/mr_article.php?b=5&a=42")

Enjoy, and for any question/remark, come to see us at cairo-dock.org ! :)

---

### Post by nacho32 on 2009-05-12
great stuff gonna give it a try

---

### Post by Jackelope King on 2009-05-12
Hi, I just installed this update, and it seems to have completely broken Cairo-Dock. When Cairo-Dock opens, it gives me the option to load with or without OpenGL. When I choose to use OpenGL, I my dock becomes a flickering box of bizarre icons. Animations sort of work as I move my cursor across the dock, but it frankly looks terrible. When I load the dock without using OpenGL, there's some improvement, but my dock (which I normally load with a transparent background) has an ugly black box for the background.

I'm running Intrepid with an ATI Mobility Radeon x700.

---

### Post by matttbe on 2009-05-12
The ATI drivers aren't very stable with OpenGL. It depends of the drivers !
But for your bug, can you post a message on [cairo-dock.org]("http://www.cairo-dock.org") ? Can you mention if you have KDE or Gnome, your Ati drivers, etc. ?

Thanks !

PS : no problem with Nvidia and Gnome ! ;)
PS² : Please, take cairo-dock repositories ! if there are some mistakes when you try to install cairo-dock, purge the older packages and reinstall the newer.
```
sudo apt-get remove cairo-dock* --purge
sudo apt-get install cairo-dock
```

Cairo-Dock 2.0  :): [http://www.cairo-dock.org/communique/communique-en.pdf]("http://www.cairo-dock.org/communique/communique-en.pdf")

---

### Post by nacho32 on 2009-05-12
just installed it and it is excellent  running 9.04 64 bit no problems
Here is some screen shot video and other info on it
[http://webupd8.blogspot.com/2009/05/cairo-dock-200-is-here-linux-dock-menu.html]("http://webupd8.blogspot.com/2009/05/cairo-dock-200-is-here-linux-dock-menu.html")

---

### Post by Jackelope King on 2009-05-12
> **matttbe said:**
> The ATI drivers aren't very stable with OpenGL. It depends of the drivers !
But for your bug, can you post a message on [cairo-dock.org]("http://www.cairo-dock.org") ? Can you mention if you have KDE or Gnome, your Ati drivers, etc. ?

Thanks !

PS : no problem with Nvidia and Gnome ! ;)
PS² : Please, take cairo-dock repositories ! if there are some mistakes when you try to install cairo-dock, purge the older packages and reinstall the newer.
```
sudo apt-get remove cairo-dock* --purge
sudo apt-get install cairo-dock
```

Cairo-Dock 2.0  :): [http://www.cairo-dock.org/communique/communique-en.pdf]("http://www.cairo-dock.org/communique/communique-en.pdf")
Thank you. I've done so.

---

### Post by nacho32 on 2009-05-12
I like it but I get a spacer at the bottom by my VLC icon I can't remove? I know how to add a spacer but this one has no option to remove, any Ideas would be great.
[IMG]http://files.myopera.com/web4me/albums/752787/Screenshot.png[/IMG]

---

### Post by celticbhoy on 2009-05-12
how do i update from the beta?

---

### Post by nacho32 on 2009-05-12
> **celticbhoy said:**
> how do i update from the beta?

sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plug-ins

---

### Post by fabounet on 2009-05-13
this is an automatic separator between applet and launcher.
you can deactivate them in the "Icons" module
you can also allow to place applets between launchers if you prefer.

---

### Post by nacho32 on 2009-05-13
> **fabounet said:**
> this is an automatic separator between applet and launcher.
you can deactivate them in the "Icons" module
you can also allow to place applets between launchers if you prefer.
yeah I found that out , but thanks:p

---

### Post by celticbhoy on 2009-05-13
Just to check Fabounet, The version I installed was a beta from about 3 weeks ago, I have now added the repo and tried to update but it says it is allready the newest version. Have there been changes in the last three weeks?

---

### Post by Favux on 2009-05-13
Thank you fabounet and the rest of the Cairo Dock team.

Cairo Dock 2.0 is awesome!  I think I'll be playing with the various themes for quite a while.

---

### Post by andrea000 on 2009-05-13
Hello all,

I upgraded Cairo dock last night its a remarkable improvement 
from the last release but i cant find out how to round all 4
corners on the dock.I can round the bottom 2 but there rounded
to much.What i need help with is rounding all 4 corners just a
little on the dock and i like the black glass look but what will
it look like on a light background.

---

### Post by nilarimogard on 2009-05-14
[Here is a video and some screenshots with all the themes]("http://webupd8.blogspot.com/2009/05/cairo-dock-200-is-here-linux-dock-menu.html")

---

### Post by fabounet on 2009-05-14
yes celticbhoy a lot of news even in 3 weeks ^_^
I really recommend you to install this release, even if the beta was quite stable.
you can remove it and re-install it without loosing your themes (just in case, you can backup ~/.config/cairo-dock)

@andrea000 You should see in the "Background" module, you can setup the corner radius.
if you're using the 3Dplane view, the "far" corner are of course less rounded than the "close" corners.

---

### Post by xfearxnxloathing on 2009-05-16
OMG this dock PWNS!!  animations are silly f*n ridiculous!!! 

i <3 cairo-dock!!!!

---

### Post by janko on 2009-05-16
Really nice, but I've got a problem, when I run in opegGl mode I see an ugly black rectangle around the dock. Seems like it doesn't understand it has to be transparent. I have an intel GMA 950 Video, and Compiz runs quite well. Any idea?

---

### Post by xfearxnxloathing on 2009-05-16
> **janko said:**
> Really nice, but I've got a problem, when I run in opegGl mode I see an ugly black rectangle around the dock. Seems like it doesn't understand it has to be transparent. I have an intel GMA 950 Video, and Compiz runs quite well. Any idea?


try it without opengl and see if it goes away

---

### Post by teseglet on 2009-05-16
I tried it with Kubuntu. I have a Nvidia GeForce 6200 card.  Every time my cursor got near the dock there would be a millisecond dock shift a couple of centimeters and then back to normal... trying both the with and without GL version.  Very annoying so I purged the application.

---

### Post by janko on 2009-05-16
> **xfearxnxloathing said:**
> try it without opengl and see if it goes away

Yes without OpenGL it goes away, but I also loose all the fancy smooth animations! Maybe tomorrow I try searching in the cairo dock forums.
Thanks anywa.

---

### Post by andrea000 on 2009-05-16
> **fabounet said:**
> yes celticbhoy a lot of news even in 3 weeks ^_^
I really recommend you to install this release, even if the beta was quite stable.
you can remove it and re-install it without loosing your themes (just in case, you can backup ~/.config/cairo-dock)

@andrea000 You should see in the "Background" module, you can setup the corner radius.
if you're using the 3Dplane view, the "far" corner are of course less rounded than the "close" corners.

thank you fabounet

---

### Post by xfearxnxloathing on 2009-05-17
> **janko said:**
> Yes without OpenGL it goes away, but I also loose all the fancy smooth animations! Maybe tomorrow I try searching in the cairo dock forums.
Thanks anywa.


possibly try a removal and a reinstall, could have just been buggy.  

NOT trying to hi-jack the thread basis here but try AWN, it's pretty stable.

---

