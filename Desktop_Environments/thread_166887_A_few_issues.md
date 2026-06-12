---
title: "A few issues"
date: 2006-04-27
forum: Desktop Environments
---

### Post by Matt Houston on 2006-04-27
Hey, 

After months of using Ubuntu I almost uninstalled it and went back to windows due to a few irritations, but came back to my senses and thought I would discuss my concerns first.

1) Firefox crashes, all the time. Seems to happen mostly when viewing a page with imbedded video, I'm using mplayer. It also seems to crash often when I try and save a picture on a site to my harddisk.

2)Eye of Gnone picture viewer. Is there a setting somewhere so I can just tab through a folder of pictures without having to open and close each on individually, I can't find one.

3)DVD's, when I pop one in my DVD drive it doesn't play automatically, and if I double click the drive it open it up in the file browser and shows me the files directories on the DVD.

4)DVD's again, when I have a disk in the DVD drive the eject button won't work, I have to right click the icon on the desktop and eject.

5)If I right click the wastebasket and 'empty wastebasket' it doesn't do anything. I have to go into the wastebasket and delete the files manually.

6)Whenver I open an app or the file browser it always opens unmaximised, been looking for a setting to change this but can't find anything.

Are these kind of things just something you have to live with if you use Ubuntu? Any ideas would greatly appreciated.

---

### Post by az on 2006-04-27
[QUOTE=Matt Houston]Hey, 

After months of using Ubuntu I almost uninstalled it and went back to windows due to a few irritations, but came back to my senses and thought I would discuss my concerns first.

1) Firefox crashes, all the time. Seems to happen mostly when viewing a page with imbedded video, I'm using mplayer. It also seems to crash often when I try and save a picture on a site to my harddisk..[/QUOTE]

Can you run the Dapper live cd and install mplayer and the mozilla plugins from there and see if the problem still happens?  Alternatively, you can use totem with the xine backend and that works fine.


[QUOTE=Matt Houston]
2)Eye of Gnone picture viewer. Is there a setting somewhere so I can just tab through a folder of pictures without having to open and close each on individually, I can't find one..[/QUOTE]
In the graphics submenu, there is an image viewer.  It can brwse folders and even make a slideshow.  It works even better in Dapper.  Other alternatives (for slow systems) include gqview.  It is in universe.


[QUOTE=Matt Houston]
3)DVD's, when I pop one in my DVD drive it doesn't play automatically, and if I double click the drive it open it up in the file browser and shows me the files directories on the DVD..[/QUOTE]

In the preferences menu you can set the action of inserting disks.  It should already be set to just play the DVD out-of-the-box....  


[QUOTE=Matt Houston]
4)DVD's again, when I have a disk in the DVD drive the eject button won't work, I have to right click the icon on the desktop and eject..[/QUOTE]

Right.  Not all optical drive hardware can safely do that.  Here at work using a windows system, I can reliable crash this windows2000 computer by ejecting a cd while it is being read.

Some people were looking into the differnt ways that HAL (Hardware Abstraction Layer) can handle that...


[QUOTE=Matt Houston]
5)If I right click the wastebasket and 'empty wastebasket' it doesn't do anything. I have to go into the wastebasket and delete the files manually..[/QUOTE]

If you have stuff in your trash that is not writable by your user, you cannot delete it unless you have the proper permissions.  Is this the case?  


[QUOTE=Matt Houston]
6)Whenver I open an app or the file browser it always opens unmaximised, been looking for a setting to change this but can't find anything

Are these kind of things just something you have to live with if you use Ubuntu? Any ideas would greatly appreciated.[/QUOTE]

Any app should open the same way you closed it.  

Quite the quirky desktop you have!  It's not supposed to work that way!

Do you have only ubuntu repositories enabled?  Did you install any foreign software?  What happens if you create another user and log in to that account?  Can you reproduce these bugs?

---

### Post by Matt Houston on 2006-04-28
Thanks for the reply.

1)  I don't think it is particularly a video issue as it happens when I save pictures/photos as well. I was thinking switching to swiftfox which presented it's own set of problems, more about that later.

2)Nice one, solved that. Only think I don't like about that viewer is when you open a picture it opens the entire folder instead of just the image you select, but it will do.

3)System >removable drives and media>multimedia>video DVD discs right? I have ticked play DVD disks when inserted, the cmmand I have is mplayer %d. Not working. Somehow I managed to kill my ability to open music cd's as well now:

```
Couldn't display "cdda:///dev/hdb"
```

same thig when I try my second drive.

4)Cool, actually I remember reading that somewhere, thanks. 

5)Sounds about right, how do I kill them?

6) Total mystery.

And I just remembered whenever I log in my home and computer icons have always rearranged themselves. 

I am seriously considering a re-install, maybe I will wait for the next realease.

---

### Post by Sef on 2006-05-01
Do a clean install with Dapper.  I'm using Beta 2 now, and it has fixed all the problems almost that I have had.

---

