---
title: "Multiple Workspace Configuration"
date: 2008-03-08
forum: Desktop Environments
---

### Post by derbouka on 2008-03-08
Hello!

One thing that I like most on Ubuntu, is the Multi-workspaces! I'm kind of addicted to workspaces and in Ubuntu I think that this should be extended and should have more relevance( since I think is really good for productivity).
Basically I like to dedicate each workspace to a different kind of activity that I do, and using the CTR+ALT+[LEFT/RIGHT KEY] to change between them.
I do this by trying to open different set of applications in each of them manually, but there'r little customization available for Ubuntu user's...
I would like to be able to set different backgrounds, shortcuts, menus, environments(like set one specific workspace to be a remote-destop application or a Virtualization application), etc, but this is not possible( at least I don't know how).
So my question( even though this is more like a suggestion), is there any application in gnome that allows you to customize each workspace?

Best regards

---

### Post by jken146 on 2008-03-08
If you are using compiz-fusion then I believe you can choose a different wallpaper for each workspace.  Install compizconfig-settings-manager first.

---

### Post by arvevans on 2008-03-08
derbouka

If using Gnome, then:
[INDENT]system>>preferences>>appearance

system>>preferences>>art manager>art

system>>preferences>>preferred applications

system>>preferences>>screensaver

system>>preferences>>sessions

system>>preferences>>windows

system>>administration>login window and graphics>[/INDENT]

Is that enough to get you started?

Arv
_._

---

### Post by derbouka on 2008-03-08
Yes I can change wallpaper using compiz in my laptop, but I can't use compiz in my company PC cause I don't have a 3D graphic card there...
Well, having different wallpapers is nice to be able to identify each workspace, but I think that should be more customization available so we can take advantage of it to be more productive.
Another thing is that we shouldn't need to install compiz to have this feature available :S

---

### Post by derbouka on 2008-03-08
> **arvevans said:**
> derbouka

If using Gnome, then:
[INDENT]system>>preferences>>appearance

system>>preferences>>art manager>art

system>>preferences>>preferred applications

system>>preferences>>screensaver

system>>preferences>>sessions

system>>preferences>>windows

system>>administration>login window and graphics>[/INDENT]

Is that enough to get you started?

Arv
_._
arveans, yes I know those applications, but they change the settings for all workspaces. Is there a way, to use them just for one specific workspace?

---

### Post by skullmunky on 2008-03-10
also, In KDE:

for wallpaper: System Settings -> Desktop; you can choose which desktop the wallpaper's for from the menu.  

to keep a certain app on a specific desktop:

open the app
R-click on the window title bar
select Advanced->Special Application Settings
in the "Geometry" tab,  check the "Desktop" optio.  Change "Do Not Affect" to "Force".  Choose a desktop from the menu on the right.

Actually this thread's maybe a good place to put something related that I'm really curious about - is it possible (in either Gnome, or KDE, or e17, or Other ... ) to have each desktop show different icons?  So I could, for instance, clutter Desktop 1 with a lot of work-related text files, Desktop 2 would be covered in files related to projects I'm working on, Desktop 3 is where I'd have random stuff downloaded from the web, etc.  Imagining how this would work, I could see each Desktop showing a different directory, or alternately an extra catalog file or something.  I'd really love to have this feature or write it ... 

You might wonder Why, since it sounds like an invitation to bad file management habits.  Here's my theory : a lot of people have a hard time finding things on their computers.  That's why they just throw everything on the desktop.  People don't naturally think in terms of hierarchical compartmentalization, especially beyond 1 or 2 layers.  The intent of the gui desktop is to leverage visual spatial memory, but this also tends to be confounded by deep tree traversals.  Hence the importance of features like search integration, google integration on the desktop, etc.  But having a wide open space to use to arrange things would also be nice.

---

### Post by smartboyathome on 2008-03-11
I don't think it is possible right now, since you would have to have each instance be its own desktop, and imo this would probably take tons of ram (especially with GNOME + Nautilus).

---

### Post by derbouka on 2008-03-14
> **smartboyathome said:**
> I don't think it is possible right now, since you would have to have each instance be its own desktop, and imo this would probably take tons of ram (especially with GNOME + Nautilus).
I've been searching a bit about this idea and here it's some collection of different topics about this:
[LIST]
[*][idea #4512: Ability to set different wallpaper/background for each virtual desktop]("http://brainstorm.ubuntu.com/idea/4512/")
[*][idea #452: Different Wallpaper on Different Workspaces]("http://brainstorm.ubuntu.com/idea/452/")
[*][idea #901: DIfferent desktop icons for each workspace.]("http://brainstorm.ubuntu.com/idea/901/")
[*][idea #3830: Workspaces]("http://brainstorm.ubuntu.com/idea/3830/")
[*][Different desktop icons in each workspace]("http://gnomesupport.org/forums/viewtopic.php?t=13152")
[*][Bug 356922 &#8211; Possibility to have different icons in different workspaces]("http://bugzilla.gnome.org/show_bug.cgi?id=356922")
[/LIST]

I really think that this is important and I believe that I'm not the only one thinking this way. Of course it would need more RAM and it would take more resources, but it would enhance user's desktop experience.

Best regards

---

### Post by smartboyathome on 2008-03-14
I read those, but right now there is absolutely NOTHING which can do this. Someone will have to program this to work with a desktop environment.

---

