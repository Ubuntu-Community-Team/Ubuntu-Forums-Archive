---
title: "Gnome panel like GDesklets StarterBar"
date: 2007-02-13
forum: Desktop Environments
---

### Post by librano on 2007-02-13
hi everyone!

First I would like to mention that I am using Dapper Drake which is upto date.

I really like to have launch icons easily accessible for programs that i use often (as opposed to going through the menu everytime) Right now I have a ton of launch icons on my top gnome panel and I would like to 'clean things up a bit'. 

A nice thing would be something like StarterBar in Gdesklets. For those who dont know these are launch icons on the desktop with a bit of eyecandy. But on my system gdesklets with StarterBar uses up about 30 precious MB of RAM... out of 256. I'm not ready to sacrifice that much for a couple of launch icons.

What I would like to do is create a new Gnome panel make it big to about 50 pixels, slap on some transparency and have that with my icons sit on the desktop. However, being a panel,  it is always on top of my windows and the handles on the ends of it aren't transparent or removable.

Is there a way to dock/attach just that panel to the desktop so that all windows come above it? And how can I get rid of those handles? Is it possible to get some eyecandy on that panel? e.g. icon zooming.

Thanks for your help in advance.

---

### Post by lyceum on 2007-02-14
If I understand what you are trying to do, you can right click on the panel and switch on the auto hide in properties. Otherwise windows will pop up above it anyway. To get the icons there, just right click on the programs you want in your applications or systems files and choose "add to panel." You can also add the whole area to the panel, so you click and see all of your games, for example. 

Hope that helps.

---

### Post by librano on 2007-02-16
thanks lyceum for your reply.

unfortunately, that is not what i wanted to do. since a picture is worth a thousand words, i've taken some screenshots. i've made the images as small as possible so i dont eat up people's bandwidth. both come up to less than a megabyte. Here is what i want my desktop to look like.

[IMG]http://img186.imageshack.us/img186/6596/screenshotbb4.png[/IMG]

as you can see my top panel is pretty crowded and i wanted to move the launch icons to another panel. I have added a third panel in the middle of the desktop with my icons and enabled transparency. however, the handles at the ends of the panel remain opaque, something that takes away from the aesthetics of the panel.

now when i open a window... with this post for example,  the panel remains on top of the window. Here is a screenshot.

[IMG]http://img263.imageshack.us/img263/7417/screenshot1un3.png[/IMG]

i hope my problem is more clear now. i would like the third panel in the middle of the desktop to remain below all windows. and of possible make the handles transparent or remove them altogether. but i suppose removing the handles would remove the panel's clickable interface. also if i could add some kind of eyecandy to that panel like icon zooming on mouse-over that would be great.

i hope this is doable. or maybe it can be a feature in future releases :)

thanks for your help in advance.

[edit] i know i could just drop desktop icons. but the transparency bit around the icons looks cool... what can i say... i am an aesthetics freak :) plus this way, my launch icons are grouped together nicely on the desktop.

---

### Post by lyceum on 2007-02-16
That makes sence. You should be able to click on side (the part not transparent) and it should move to the side of the screen and disapear. I did not know you could put it in the middle like that. Very cool. I am going to have to try to do that myself. :) 

My recomendation would be to put all of your starter icons only on that bar to clear up the top bar. You can switch your Applications/Places/Systems into one Ubuntu logo by removing it and adding the other Ubuntu logo option in the "add to panel" (not sure what it is called, and not near my Ubuntu machine right now, sorry). Then move your stuff on the bottom bar to the top bar and git rid of your bottom bar. Then your floater can be the bottom bar. This is what I do, except that I use the gDesklets. Let me know if you want a screenshot. Also, When I get to my machine I will try to duplicate what you are doing to see if  can give any more help, but I can tell you that you cannot hide the bar, just move it.

---

### Post by librano on 2007-02-16
thanks again for the reply!

i kind of like the gnome layout with panels both at the top and at the bottom. the layout you described is kind of what i had when i used KDE on Mandriva with the taskbar at the top and icons and menu autohiding at the bottom. maybe i'll go with a vertical autohide panel on the side... i'll see whats a good compromise between functionality and looks.

you could post a screenshot if you like. its nice to see what others can do to maximise productivity. i might get an idea or 2... besides, my desktop hardly ever stays the same for more than a month or so :)

but i hope there's a way i can do this... if it requires config file editing... bring it on! thats when the fun begins :)

[edit] just tried the panel on the side solution... its eats up a few pixels on that side even when hidden... its not floating my boat... i'll stick with the crowded panel for now...

---

### Post by wxnker on 2007-02-18
I was using the attached "**before-setup**" until a few days ago. I had the side-gnome-panels on top though. I would think that this should be editable through some config-file, e.g. I did the opposite change and edited the **psi-tasklist desklet** to always be on top (Standard is not on top), but I'm not sure how to edit this for gnome-panels.

I changed the psi-taskbar settings with this tip from **Artificial Intelligence**:

[COLOR="Gray"]gedit psi-tasklist.display

Change:
<display window-flags="sticky, below">
to
<display window-flags="sticky, above">

restart Psi-tasklist[/COLOR]

Perhaps you can do something similar with the panels and set them to "below", but I'm not sure where and how.

If not then you could try using the "**Starterbar**" from **gdesklets**. It has _mouseover effects_, other _eyecandy_ and it can be configured to be _transperant_ etc. I used that some weeks ago but I do not have a screenshot. _Starterbar is NOT always on top_ and has a similar look as the gnome-panel on your screenshot. I believe, this could be a nice alternative for you.

I kinda like to experiment to find something that is effective and goodlooking so I change my desktop quite often. I have included screenshots of both my former desktop-style and the one I use now (with a drawer for ekstra launchers), which is more Windows XP like.

I suggest you take a look at the excellent "how to" by **Artificial Intelligence** here:
[http://www.ubuntuforums.org/showthread.php?t=77694&highlight=eyecandy](http://www.ubuntuforums.org/showthread.php?t=77694&highlight=eyecandy)

BTW: The small errors you see below the psi-taskbar on the "before.png" are not normally there. I was experimenting with a bottom gnome-panel which was auto-hidden when I did the screenshot. I really liked the psi-taskbar's look with shadows and stuff and perhaps I'll go back to using it just for the good looks, but for now I'm using the Win XP setup :D

The panel-item mentioned by "[COLOR="Red"]lyceum[/COLOR]" is called **Main Menu** and it works like the "Start" menu in Windows XP. It's the one I use in my new gnome-panel setup (after picture) instead of the optional **Menu Bar** that comes with Ubuntu's default panel.

Regards
Wxnker

---

