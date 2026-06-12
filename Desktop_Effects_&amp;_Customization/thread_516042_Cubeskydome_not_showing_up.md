---
title: "Cube/skydome not showing up"
date: 2007-08-02
forum: Desktop Effects &amp; Customization
---

### Post by Yes on 2007-08-02
Ok, Beryl is working fine,  but I don't see the cube.  Instead, I just see my 2D background.  In Beryl Manager, the Cube is checked, as it the rotation.

Any ideas?

Thanks.

---

### Post by atomkarinca on 2007-08-02
right click the red beryl icon on the notification area and select beryl as the window decorator (if it already isn't). if you still got no cube you can try unchecking the cube, increase the workspace number to 4 and then re-checking the cube.

keyboard shortcuts are ctrl + alt + left arrow and ctrl + alt + right arrow.

---

### Post by Yes on 2007-08-02
That didn't seem to work, sorry.  When you say increase the workspace number to four, I couldn't find that option.  Where is that?

Thanks.

---

### Post by atomkarinca on 2007-08-02
right-click the workspace area, select preferences, you should see "number of workspaces". this works for compiz but i don't know if it works for beryl. there might be an option about the number of workspaces under cube tab in beryl manager.

---

### Post by AlexenderReez on 2007-08-02
op ... have you reload after make change in setting?sometimes need to reload...

---

### Post by Yes on 2007-08-02
There is a "Number of desktops" option, but that doesn't help the problem.

Yes, I have reloaded after I made the changes.  Any more ideas?

Thanks.

---

### Post by Yes on 2007-08-03
Bump.

---

### Post by mpospisil on 2007-08-03
I would recommend switching from Beryl to Compiz Fusion because Beryl is no longer getting any updates since its merger back to Compiz.

---

### Post by Yes on 2007-08-03
I would rather try to get Beryl working, as it has taken me a lot of effort to get everything working thus far.  The only thing that still doesn't work is the cube, and I'd really like to figure this out.

---

### Post by Yes on 2007-08-08
Bump.

---

### Post by deatester on 2007-08-08
> **Yes said:**
> I would rather try to get Beryl working, as it has taken me a lot of effort to get everything working thus far.  The only thing that still doesn't work is the cube, and I'd really like to figure this out.

I don't know if this will help you as I am new at this...but you can try thses setting that I have used and have my cube and skydome working. General options # of desktops 6..Now Desktop..Now select desktopcube..Under options Fold accel  4. Fold Speed 1.5..Fold Timestep 1.2...try these setting, you can adjust the later.  fade time 1.0...unfold zoomback 1,0...Next select Rotate cube... Zoom back 15.00 ... check zoom befor rotate... thses setting might get you going then you can tweak them as you go on

---

### Post by Yes on 2007-08-08
I tried those settings, and they didn't work.

Thanks, though.

---

### Post by Yes on 2007-08-09
Bump.

---

### Post by Yes on 2007-08-10
Bump.

---

### Post by LordDon on 2007-08-10
I second this bump, I'm having the same issue.  I can change all other settings through the Beryl  Settings Manager but the cube isn't working.

---

### Post by lsweet on 2007-08-10
Yeah; I've been working at getting my cube working all day (Compiz, not Beryl).  Give this a shot -- better than endless bumps without an answer:

(The steps are for Compiz but I imagine they're similar for Beryl)

1 - Open Settings Manager
2 - General Options > Desktop Size (Tab)
3 - Set:
[LIST]
[*]Horizontal Virtual Size = 4
[*]Vertical Virtual Size = 1
[*]Number of Desktops = 4
[/LIST]

The problem I was having was that even though I had 4 desktops, Expo and Cube would only show two.  Once I made this change I was able to navigate between all 4.

---

### Post by Yes on 2007-08-10
Thanks, but no, it still doesn't work.

---

### Post by Yes on 2007-08-10
Update: If I use the shortcut keys (ctrl + alt + direction), then the cube moves, and I see the animation.  But I would like to have the desktop look like this:

[img]http://www.thinkwiki.org/images/4/4f/Cube.jpg[/img]

Right now, it's still 2D.  Can anyone help me?

Thanks.

---

### Post by deatester on 2007-08-10
Man, I sure don't know what you're missing. I just set up another new computer today, added beryl, added restricted drivers went in and used the settings that I detailed for you and the cube is working perfectly for me. the only settings that I messed with were the number of desk top cubes under general, then desk top settings that I detailed for you, mine worked first time?????

---

### Post by Yes on 2007-08-10
I changed my settings according to what lsweet said, but I just tried what you said, and it still doesn't work.

Thanks, though.

---

### Post by Yes on 2007-08-11
Bump.

---

### Post by Yes on 2007-08-11
Bump.

---

### Post by Old *ix Geek on 2007-08-12
I'll third that bump!  I want that cube...but can't seem to make it materialize. :(  I've followed all the suggestions in this thread, but to no avail.

---

### Post by Yes on 2007-08-12
Bump.

---

### Post by Arthur Archnix on 2007-08-12
Beryl is no longer being developed. You're unlikely to find much assistance in getting it going when everyone who knows anything at all about Beryl is now spending their time and efforts on compiz-fusion. 

If Beryl and Compiz could find a way to leave Beryl behind and move forward, there's really no good reason why you shouldn't as well.

Happy bumping...

---

### Post by Yes on 2007-08-12
Ok fine...I got rid of Beryl.

is the compiz in Synaptic compiz-fusion, or is that the old compiz?

---

### Post by petit.padavoine on 2007-08-12
Compiz fusion isn't in the official repositories yet.
Here's how to get it:
```

sudo apt-get -y remove compiz-core desktop-effects

```

Add the following repositories to /etc/apt/sources.list:
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

```

wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg
sudo apt-key add DD800CD9.gpg

sudo apt-get update && sudo apt-get upgrade

sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-* libcompizconfig-backend-gconf

```

Add compiz --replace to your startup programs.

If you want emerald (recommended for Window Reflections plugin in Compiz Fusion),
```

sudo apt-get install emerald emerald-themes

```

And add emerald --replace to your startup programs.

Happy compoziting !

---

### Post by Yes on 2007-08-12
I'm sorry, but do I just add the 

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

to the sources.list ?  Or do I also add the stuff in the second code box?

Thanks.

Edit:  Ok, I did everything you told me to, and I think everything worked, but I can't find anything like a "compiz-manager".  How do I use compiz/open the manager?

Edit2: I ran the command 'compiz --replace', and I got these errors:

```
/usr/bin/compiz.real (ini) - Warn: Could not open main display config file /home/username/.compiz/options/general-allscreens.conf
/usr/bin/compiz.real (ini) - Warn: Loading default plugins (ini,inotify,png,decoration,move,resize,switcher)
/usr/bin/compiz.real (ini) - Error: Failed to write to /home/username/.compiz/options/general-allscreens.conf, check you have the correct permissions
/usr/bin/compiz.real (ini) - Error: Failed to write to /home/username/.compiz/options/general-allscreens.conf, check you have the correct permissions
/usr/bin/compiz.real (ini) - Warn: Could not open config file /home/username/.compiz/options/general-screen0.conf - using defaults for core
/usr/bin/compiz.real (ini) - Error: Failed to write to /home/username/.compiz/options/general-screen0.conf, check you have the correct permissions
inotify_add_watch: No such file or directory
/usr/bin/compiz.real (ini) - Warn: Could not open config file /home/username/.compiz/options/decoration-allscreens.conf - using defaults for decoration
/usr/bin/compiz.real (ini) - Error: Failed to write to /home/username/.compiz/options/decoration-allscreens.conf, check you have the correct permissions
/usr/bin/compiz.real (ini) - Warn: Could not open config file /home/username/.compiz/options/move-allscreens.conf - using defaults for move
/usr/bin/compiz.real (ini) - Error: Failed to write to /home/username/.compiz/options/move-allscreens.conf, check you have the correct permissions
/usr/bin/compiz.real (ini) - Warn: Could not open config file /home/username/.compiz/options/resize-allscreens.conf - using defaults for resize
/usr/bin/compiz.real (ini) - Error: Failed to write to /home/username/.compiz/options/resize-allscreens.conf, check you have the correct permissions
/usr/bin/compiz.real (ini) - Warn: Could not open config file /home/username/.compiz/options/switcher-screen0.conf - using defaults for switcher
/usr/bin/compiz.real (ini) - Error: Failed to write to /home/username/.compiz/options/switcher-screen0.conf, check you have the correct permissions
/usr/bin/compiz.real (ini) - Warn: Could not open config file /home/username/.compiz/options/switcher-allscreens.conf - using defaults for switcher
/usr/bin/compiz.real (ini) - Error: Failed to write to /home/username/.compiz/options/switcher-allscreens.conf, check you have the correct permissions
```

Running 'emerald --replace' results in this error:

```
Segmentation fault (core dumped)
```

---

### Post by Arthur Archnix on 2007-08-12
Amaranth is the Ubuntu Developer and Maintainer for Compiz.

Use his instructions [here]("https://help.ubuntu.com/community/CompositeManager/CompizFusion").

You should also remove the deb's that other guy had you add. Then do a sudo purge of everything you've installed thus far.

Ubuntu Admin Vorian has an extensive thread [here]("http://ubuntuforums.org/showthread.php?t=481314") that may have already solved any remaining issues you run into.

Best,

Wait...you do realize that the cube doesn't stay like that right? I mean, you're not trying to get it so that the desktop sits statically like that screenshot you posted, are you? It's always 2D unless its rotating. Don't mean to insult you, I just re-read your posts and its a little unclear what you're trying to achieve here.

---

### Post by Yes on 2007-08-12
Sorry, what exactly is the command for 'sudo purge'?

Thanks for the guides :-)

Edit:  No, I didn't realize that, thank's for pointing that out.  I'm an idiot.  Sorry.

---

### Post by Arthur Archnix on 2007-08-12
From Vorian's thread:
```
sudo apt-get --purge remove compiz* libcompizconfig*
```

No worries. Once you get compiz up and running check out the screensaver plugins which let you set your screensaver to a rotating cube.

---

### Post by petit.padavoine on 2007-08-13
> **Arthur Archnix said:**
> Amaranth is the Ubuntu Developer and Maintainer for Compiz.

Use his instructions [here]("https://help.ubuntu.com/community/CompositeManager/CompizFusion").

You should also remove the deb's that other guy had you add. Then do a sudo purge of everything you've installed thus far.

Ubuntu Admin Vorian has an extensive thread [here]("http://ubuntuforums.org/showthread.php?t=481314") that may have already solved any remaining issues you run into.


What's the deal with this how-to by Amaranth?
The repository he uses is missing one of the plugin packages (compiz-fusion-plugins-unofficial), it's not at all up-to-date (compared to the tuxfamily.org one), AND it keeps saying there's an update to compiz-core that needs to be installed.

---

### Post by jaime77 on 2007-08-26
I have the same problem and after playing around with the settings manager, bindings, shortcuts, etc. I give up and start googling around, searching documentation, howtos, faqs, even a simple newbie guide or some tutorial. Dont find any useful. After hours, i still cant make the damn cube show up like i see in a youtube video, the last resource, the forums, i view this post and many others until i found the ONE.

Now i can view the damn cube and skydome.
JUST PRESS (ALT+CTRL+LEFTMOUSEBUTTON) AND HOLD THE LEFTMOUSEBUTTON.
Keep holding the left mouse button while you move the mouse (you can hold or release the alt+ctrl after pressing the left mouse button)

I found the ONE after leaving this post, but the similarity to my problem, make me come back and post a reply, i dont know if it will help you, but i read the full post and think you and me were looking for the same answer HOW THE HELL MAKE THE CUBE SHOW UP like we see in some picture or youtube video??? not looking for installation problem, configuration... just the damn shortcut, binding to make it show up (since i never see the Alt+Ctrl+LeftButtonMouse in any binding, shortcut or anyplace in the beryl settings manager, or in any tutorial, guide, faq, etc. ) and beryl come with no Help (at least i couldnt find it in the red icon)

---

### Post by petit.padavoine on 2007-08-30
> **jaime77 said:**
> 
I found the ONE after leaving this post, but the similarity to my problem, make me come back and post a reply, i dont know if it will help you, but i read the full post and think you and me were looking for the same answer HOW THE HELL MAKE THE CUBE SHOW UP like we see in some picture or youtube video??? not looking for installation problem, configuration... just the damn shortcut, binding to make it show up (since i never see the Alt+Ctrl+LeftButtonMouse in any binding, shortcut or anyplace in the beryl settings manager, or in any tutorial, guide, faq, etc. ) and beryl come with no Help (at least i couldnt find it in the red icon)

Beryl is NOT supported anymore. It's not being developped, so you shouldn't expect to get that much ongoing support about it.

However, if you're looking for help (or something so simple as a keyboard shortcut), you should check the [official website.](http://beryl-project.org/) There's a "feature overview" section which gets you started with all the keyboard shortcuts to trigger the basic features.

---

