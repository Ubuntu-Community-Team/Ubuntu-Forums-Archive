---
title: "Breezy Issues..."
date: 2005-10-27
forum: Desktop Environments
---

### Post by mustang on 2005-10-27
Hello all,

I upgraded to Breezy about two weeks and I am incredibly impressed with it. My sound finally works, including the hi-resolution output jack on my Chaintech AV710. Monochome fonts finally look like normal windows fonts (sorry, I just absolutely hate anti-aliasing).

I made my best attempt to document all my problems. If you guys need anything else, please let me know. 

1. Video is much more pixelated in VLC and totem but not in XINE. Now I know all the hate totem gets around here but I can't stand video players with a seperate control window. 

I took screenshots below as evidence. NOTE: deinterlacing was not on in both players & I do have the totem-xine backend installed.

Totem: [http://members.cox.net/feesh2/Screenshot-3.png]("http://members.cox.net/feesh2/Screenshot-3.png")
xine: [http://members.cox.net/feesh2/Screenshot-1%20(copy).png]("http://members.cox.net/feesh2/Screenshot-1%20%28copy%29.png")

Another example:
Totem: [http://members.cox.net/feesh2/Screenshot.png]("http://members.cox.net/feesh2/Screenshot.png")
xine: [http://members.cox.net/feesh2/Screenshot-1.png]("http://members.cox.net/feesh2/Screenshot-1.png")

2. Now if you look at the bottom of my desktop from the pictures above, you can see I have two panels: one has all my icons, the other has the window list. I would like to have the panel with the window list above the one with all my icons. So I reposition it but whenever I boot up, Ubuntu likes to reposition the panels to like what you see in the images above. Is there anyway I can fix this?

3. When I click on a PDF or DOC file in firefox, it likes to open the firefox download manager and show the file in it and then proceed to open it with the default program associated with that extension. Is there anyway (like in windows) to have firefox directly open the document I select without opening a download manager?

4. When I middle click in firefox on anywhere except a link, it likes to open some random webpage through google. Is there anyway I can disable this? **SOLVED**

5. I just installed OpenOffice 2 with the help of this [guide.]("http://www.ubuntuforums.org/showthread.php?t=80392") Is it safe to remove OpenOffice 1 now? And I would do that by going into Synaptic right? **SOLVED**

6. Is there a guide on how to emulate itunes through wine? **SOLVED**

7. Is there anyway to make [nifty gmail checker]("http://www.ubuntuforums.org/showthread.php?t=74539&") remember my password for my gmail account so I don't have to type it in everytime I log in? 

8. When i launch gaim, it sometimes appears on the leftside of my screen and sometimes on the right (where i prefer it). Is there anyway to make it permanently start up on the right?

9. Whenever I copy something from a cd or dvd to my hard drive, the file on my hard drive never has execute permissions. How do I change it so that it always has execute permissions?

10. Is there anyway to replace the default "show desktop" icon?

Thanks folks...

---

### Post by Dr. Nick on 2005-10-28
Ill take a stab at a few of them


3. I dont think so, mine does it to.

4. Check here for a possible solution [http://ubuntuforums.org/showthread.php?t=75992](http://ubuntuforums.org/showthread.php?t=75992)

5. You should be able to remove Oo 1 by using synaptic with no ill effects as long as the cvs installed it to a different directory which it most likely did.

6. Why do you want to emulate itunes?
Here is a link for a howto buy music from itunes [http://ubuntuforums.org/showthread.php?t=79231&highlight=howto+itunes](http://ubuntuforums.org/showthread.php?t=79231&highlight=howto+itunes)
But if you just like the player, amaroK,Banhee,quod Libeet are all very nice music players, Rhythmbox isnt bad either.

10. The show desktop Icon is picked by the theme, look in your theme folder for the icon and try to reanme the one you want to use like the origional. Not sure how to do it, hopfully someone else knows.

---

### Post by mustang on 2005-10-28
[QUOTE=Dr. Nick]Ill take a stab at a few of them


3. I dont think so, mine does it to.

4. Check here for a possible solution [http://ubuntuforums.org/showthread.php?t=75992](http://ubuntuforums.org/showthread.php?t=75992)

5. You should be able to remove Oo 1 by using synaptic with no ill effects as long as the cvs installed it to a different directory which it most likely did.

6. Why do you want to emulate itunes?
Here is a link for a howto buy music from itunes [http://ubuntuforums.org/showthread.php?t=79231&highlight=howto+itunes](http://ubuntuforums.org/showthread.php?t=79231&highlight=howto+itunes)
But if you just like the player, amaroK,Banhee,quod Libeet are all very nice music players, Rhythmbox isnt bad either.

10. The show desktop Icon is picked by the theme, look in your theme folder for the icon and try to reanme the one you want to use like the origional. Not sure how to do it, hopfully someone else knows.[/QUOTE]

First off, thanks for the reply Dr Nick!

4,5 are solved!

There reason why I want to emulate iTunes is so I can see the charts, see what's new, etc. I had the SharpMusic iTMS client installed and it only enables you to buy and preview---nothing else. 

I tried looking for the .png for the show desktop icon and I couldn't find it. Hopefully someone will chime in on it.

---

### Post by Remmelas on 2005-10-28
9.  Kinda of a kludge, but you could add an executable 'umask=' option to the fstab options for your cdrom/dvd drive.  that way, all files would copy(and be) executable.  I'm not good at umasks, or i'd offer the umask=#

---

### Post by Dr. Nick on 2005-10-29
Well I just found out that they quit using the show-desktop.png method, but I still havent seen how to change it now.

I am not sure on itunes either, you can search the howto forum here but it may be difficult to use itunes because it requires quicktime to be running aswell
[http://appdb.winehq.org/appview.php?appId=1347](http://appdb.winehq.org/appview.php?appId=1347) discusses the state of itunes+wine, but from what I saw it didnt look to promising

For you pdf and doc files it may help some just to click the always do this for this type of file dialog and set it to open and not save. Only downside is if you wan to save it, in that case just save it from the program after it opens. The way it is done on windows is through plugins to the web browser.

Their has been some success doing it with pdf files in this thread [http://ubuntuforums.org/showthread.php?t=73428&highlight=open+pdf+firefox](http://ubuntuforums.org/showthread.php?t=73428&highlight=open+pdf+firefox)

---

### Post by Dr. Nick on 2005-10-30
number 2 and 8 may also be solved by saving the changes to your session, in gnome go to prefrences,sessions and check always save session or something similar, Im not in gnome right now so I cant check myself.

---

### Post by mustang on 2005-10-31
Thank you Dr Nick for the replies. I'm going to look into the wine-itunes emulation from the link you gave. Looks like it is indeed possible!

> For you pdf and doc files it may help some just to click the always do this for this type of file dialog and set it to open and not save. Only downside is if you wan to save it, in that case just save it from the program after it opens. The way it is done on windows is through plugins to the web browser.

I'm not sure what you mean here. Firefox automatically opens pdf files with evince. It's just slightly annoying that the download manager pops up with it.

If anyone else could help with the other issues, that'd be great!

---

### Post by mustang on 2005-10-31
[QUOTE=Dr. Nick]number 2 and 8 may also be solved by saving the changes to your session, in gnome go to prefrences,sessions and check always save session or something similar, Im not in gnome right now so I cant check myself.[/QUOTE]

Nope, still doesn't save the orientations of the panels...

---

