---
title: "Workspace Switcher broken"
date: 2007-05-03
forum: Desktop Environments
---

### Post by otazman on 2007-05-03
My standard 7.04 workspace switcher is broken. It only displays the 1st panel and none of the others. I did have Beryl installed and I think it corrupted it. I have added more and less desktops, completely removed and replaced it with no results. Anyone have any idea how to fix it or rebuilt it? When I went to the Properties of the desktop switcher panel I received this error:
> 
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_7/prefs/display_all_workspaces' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/num_rows' specified for `/apps/panel/applets/applet_7/prefs/num_rows' stores a non-schema value

This location doesn't even exist?

Thanks, OT

---

### Post by eeefresh on 2007-05-03
I am having a similar problem.  I unistalled Beryl because it was screwing up my desklets, but now when I go to any workspace other than the first one, I lose my toolbars, desktop icons, etc.

---

### Post by RageRhinos on 2007-05-14
> **eeefresh said:**
> I am having a similar problem.  I unistalled Beryl because it was screwing up my desklets, but now when I go to any workspace other than the first one, I lose my toolbars, desktop icons, etc.

I have the same problem is there any help here?

---

### Post by smyrna112 on 2007-05-14
same here no menus on other workspaces! can some one please help!!!!

---

### Post by benditlikebecker13 on 2007-05-14
I am in a similar boat.  Installed Beryl and then started having problems (some windows wouldn't display contents) so I uninstalled Beryl and restarted.  Now when using the standard desktop effects in Gnome my workspaces are not there.  I only have one.

---

### Post by s1mple_M4N on 2007-05-16
Same problem here.
I had a fresh 7.04 install with desktop effects enabled. This worked well for a couple of weeks, then using the keyboard to switch desktops left me with a blank desktop and using the 3D cube left me on the same desktop. I have 4 desktops showing on the switcher in the taskbar.
Strangely enough, I just opened the GL Desktop Compiz config application and on the 'Workspaces' tab changed the Effect option from 'Cube & Rotation' to 'Plane and Slide'. This fixes the blank desktop problem for keyboard switching but disables the 3D cube.
Still some odd behaviour, but better than blank space.
I really like the wobbly effects and 3D cube, but is my Ubuntu experience better for having them enabled???
Look forward to having this solved.

RoyJ

P.S. If it helps - my PC: 2.4G pentium 4, 512MB generic RAM, 64MB nvidia Geforce4 MX440 SE video

---

### Post by 3dmaker on 2007-05-17
I think I found the problem.
Its the fault of the Ubuntu developers. Its an update that breaks beryl, and desktop effects. As everyone said, it worked fine for a while, then broke. For me it worked fine, because i just installed Ubuntu on this PC yesterday, and it broke yesterday. After the 18 updates it had to download and install.
And this does not happen on Fedora Core. So it must be a Ubuntu update problem.

---

### Post by z0phi3l on 2007-05-17
After every update I "reinstall" Beryl, cause I know Beryl doesn't like it when something gets updated.

---

### Post by ThomThom on 2007-05-21
How did you "reinstall" Beryl.

I just installed ubuntu 7.04 on my comp. I assume that "Desktop Effects" is Beryl?

What happened to me was:
* I installed Ubuntu
* Enabled "Desktop Effects" which gave me wobbly windows and a nice animation when I switched between workshop
* Installed Updates
* Resolution was wrong so I had to reconfigure the video stuff
* I then got an oddity where clicking and dragging the mouse on the desktop would create screenshots. That didn't happend with "Desktop Effects" was on. I found a solution for that.
* Restarted the system
* Then noticed that my workspaces was gone. I still get wobbly windows, but no workspaces (where are they configured?)

---

### Post by ThomThom on 2007-05-21
I right clicked and chose preferences. Added workspaces.
But now when it switches it doesn't do the cube rotation.
Also, the top menu bar and the bottom taskbar doesn't show on any of these workspaces.

---

### Post by poekie3000 on 2007-05-28
I have the same problem. My cube works just fine, but when i switch workspaces with my keyboard, all I get is my wallpaper and than compiz just hangs...


i'm using the desktop-effects (=compiz) that come with feisty, just the standard thing..

---

### Post by DigitalDaiquiri on 2007-05-28
I too am having the same problem.  I did a fresh install of 7.04 and everything worked fine for a few weeks.  I installed the "Compiz Settings Manager" .deb so that I could change and edit the desktop effects in more depth.  I have since uninstalled the settings manager, and reinstalled all of the compiz packages.  Currently if I try to enable the 3D cube in desktop effects my number of workspaces is decreased from 4 down to 1.  If I change the properties on my workspaces to display 4 workspaces again I get the error already mentioned in this thread where the Gnome desktop panels don't display.  I hope this information helps!

---

### Post by altair on 2007-05-29
Same problem here.. was working fine even after the updates.  I dont use beryl cuz i have an old pent 2 but I do use desktop effects which comes with feisty.  

I lost my workspaces when I thought I could improve my performance by un-checking the desktop cube effect.  Once I did that, a few minutes later, I noticed all my workspaces were gone.  Coincidently I also installed the flash plugin to Firefox.. so thats worth investigating too.   I've reset everything back to the way they were before but it still only shows one workspace.  I'll try restarting but it seems alot of us is having this problem so its doubtful that'll fix it... too bad feisty doesn't have its own version of system restore.  Any solution can [email]("mailto:thesummertriangle@gmail.com?subject=Ubuntu Workspace error") me please thanks.

---

### Post by poekie3000 on 2007-05-30
> **altair said:**
> Same problem here.. was working fine even after the updates.  I dont use beryl cuz i have an old pent 2 but I do use desktop effects which comes with feisty.  

I lost my workspaces when I thought I could improve my performance by un-checking the desktop cube effect.  Once I did that, a few minutes later, I noticed all my workspaces were gone.  Coincidently I also installed the flash plugin to Firefox.. so thats worth investigating too.   I've reset everything back to the way they were before but it still only shows one workspace.  I'll try restarting but it seems alot of us is having this problem so its doubtful that'll fix it... too bad feisty doesn't have its own version of system restore.  Any solution can [email]("mailto:thesummertriangle@gmail.com?subject=Ubuntu Workspace error") me please thanks.

that's a different problem I think. 
You're missing some workspaces after enabling your cube again. In my case, the workspaces are there, they just don't come up right if i switch between them, it results in a frozen desktop.

Your problem can be solved easily though.
You can add the missing workspace by opening the gnome configuration editor and typing '4' under the option  hspace of the compiz cube effect i think (don't have ubuntu here to give you the correct path..)

---

### Post by poekie3000 on 2007-05-31
just as sudden as it was broken, the problem solved itself (probably via updates ?)..

switching workspaces is running ok now..

---

### Post by clint1010 on 2007-06-05
I am having this problem also. New Fiesty install. I have been modifying my xorg.conf file to get the setup right for my video card (wasn't displaying window frames and window title bar), that all seems to be sorted now. But when I switch workspaces, I'm left with just the wallpaper, workspace panels are gone. Sometimes I am left with desktop icons, but not every time. I have just ran an update check, and I'm all up to date.

Is anyone still having this problem? or is there a fix I'm unaware of?

---

### Post by abhatt on 2007-06-12
I also have the same problem.  Desktop cube switching was working fine, and then I tried installing beryl today.  Something went wrong and I uninstalled beryl.  And now, the desktop cube switching refuses to work.  Any solutions?

---

### Post by abhatt on 2007-06-17
OK, I found a solution to the problem I was facing.  In gconf-editor, I changed the value of apps/compiz/screen0/options/hsize to 4 and apps/compiz/screen0/options/number_of_desktops to 1.  Everything seems to work now!

---

### Post by CaptainInsaneO on 2007-06-17
> **abhatt said:**
> OK, I found a solution to the problem I was facing.  In gconf-editor, I changed the value of apps/compiz/screen0/options/hsize to 4 and apps/compiz/screen0/options/number_of_desktops to 1.  Everything seems to work now!

Thank you SO much for this fix... this has been annoying me for about two weeks!! =D>

---

### Post by GumbyX on 2007-07-17
> **abhatt said:**
> OK, I found a solution to the problem I was facing.  In gconf-editor, I changed the value of apps/compiz/screen0/options/hsize to 4 and apps/compiz/screen0/options/number_of_desktops to 1.  Everything seems to work now!

:( This is not helping me. I have the settings that you speak of all set correctly. I am using beryl.  From what I can figure out on my own, its a problem with the actual workspace switcher changing the workspace on that single side of the cube (only way I can describe) instead of each workspace being on one side of the cube. Does anyone know of a fix for this, or even understand what I am talking about? I will be around for a while trying to find an answer online so please help out if you can. Thanks.

EDIT: Ga!! Just fixed it. Took me long enough to figure it out. Found the fix here: [http://ubuntuforums.org/showpost.php?p=2615655&postcount=4](http://ubuntuforums.org/showpost.php?p=2615655&postcount=4). Seems my "Number of Desktops got switche around for some reason. : shrugs: It works properly now and that is all that matters.

---

### Post by EvilRusk on 2007-07-25
> **abhatt said:**
> OK, I found a solution to the problem I was facing.  In gconf-editor, I changed the value of apps/compiz/screen0/options/hsize to 4 and apps/compiz/screen0/options/number_of_desktops to 1.  Everything seems to work now!

Thanks for this fix! I noticed the cube thing and missing desktops and was so annoyed, but this fixed it perfectly!

I'm just finding so many flaky things in Ubuntu that are really putting me off right now - please note I am not using exotic hardware. Such a shame as it was always such a sturdy distro.

---

### Post by Neffirithion on 2007-08-12
> **abhatt said:**
> OK, I found a solution to the problem I was facing.  In gconf-editor, I changed the value of apps/compiz/screen0/options/hsize to 4 and apps/compiz/screen0/options/number_of_desktops to 1.  Everything seems to work now!

Thanks dude!! fixed my problem too!!

---

### Post by halorin on 2007-08-21
Just thought I'd throw my two cents in. :)

I had a problem where only my first workspace had the top and bottom bars. What fixed it for me was turning off the desktop effects and then turning them back on. I have _no_ clue how or why that fixed it, as this is my first serious attempt at Linux, but it did. :)

---

### Post by ozzyprv on 2007-08-21
> **abhatt said:**
> OK, I found a solution to the problem I was facing.  In gconf-editor, I changed the value of apps/compiz/screen0/options/hsize to 4 and apps/compiz/screen0/options/number_of_desktops to 1.  Everything seems to work now!

Thank you!.

You helped me too.

EDIT: Shouldn't the thread title be changed to [SOLVED]....

---

### Post by djroze on 2007-08-22
Thanks for the fix - I can confirm that it worked for me too!  :)  Also, just a note in case anyone has trouble finding screen0; for me there's a "general" between the compiz menu and screen0...thanks again!  :)

---

### Post by JoLiSh on 2007-08-30
> **otazman said:**
> My standard 7.04 workspace switcher is broken. It only displays the 1st panel and none of the others. I did have Beryl installed and I think it corrupted it. I have added more and less desktops, completely removed and replaced it with no results. Anyone have any idea how to fix it or rebuilt it? When I went to the Properties of the desktop switcher panel I received this error:


This location doesn't even exist?

Thanks, OT

I Had this same problem, but I dont have a cube since My Ubuntu is the 6.06 version.
I tried to perform the solution.

> **abhatt said:**
> OK, I found a solution to the problem I was facing.  In gconf-editor, I changed the value of apps/compiz/screen0/options/hsize to 4 and apps/compiz/screen0/options/number_of_desktops to 1.  Everything seems to work now!

But I dont have the "compiz" directory, so I went to the directory the error points and edited the values manually. Now I have my workspace working fine.

Thanks for the tips on this problem.

---

