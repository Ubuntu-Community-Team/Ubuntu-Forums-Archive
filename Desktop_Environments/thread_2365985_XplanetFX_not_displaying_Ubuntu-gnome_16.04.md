---
title: "XplanetFX not displaying Ubuntu-gnome 16.04"
date: 2017-07-12
forum: Desktop Environments
---

### Post by 27grains on 2017-07-12
Markus Schmidt from [http://mein-neues-blog.de/xplanetfx/](http://mein-neues-blog.de/xplanetfx/)         told me " as I said desktop detection and image display is quite outdated. 

    
Try to render to a file (Settings tab in UI -> Output ->       File, add a path like /home/[youruser]/.xplanetfx.png in the text       entry) and then point your gnome wallpaper selection to this file.       "

     I have no idea what to do, I don't know how to render to a file.       It seems he has no time or desire to fix the software.
     Can you find someone to fix it or perhaps show me what to do? it looks like Markus has no time to fix the issue.

I have no idea how to render to a file (Settings tab in UI Settings tab in UI -> Output ->       File, add a path like /home/[youruser]/.xplanetfx.png in the text       entry) and then point your gnome wallpaper selection to this file.       "
Thank You

---

### Post by again? on 2017-07-12
****Been a while since I used XplanetFX but I if I recall the application itself renders a desktop image.
So in XplanetFX (Settings tab in UI -> Output -> File) set the location of the rendered file as advised.
Then in system settings > background, set your background to the same file.

[COLOR="#FF0000"]**Edit**[/COLOR]: Just installed here on Ubuntu-Gnome 17.04 and seems to work without changing any settings.
The xplanet rendered image location(see pic) should be the same as your desktop background location.
```
glen@GU17:~$ gsettings get org.gnome.desktop.background picture-uri 
'**file:///home/glen/.xplanetFX/output/xplanetFX2.png**'
```

---

### Post by 27grains on 2017-07-13
OK, I think I understand. Thank Yoi

---

### Post by 27grains on 2017-07-13
I can't see my problem comparing your picture and mine except XF2 is used and mine is FX1.

What am I missing?
Thank You

---

### Post by again? on 2017-07-13
> **27grains said:**
> I can't see my problem comparing your picture and mine except XF2 is used and mine is FX1.

What am I missing?
Thank You

I think by default XplanetFX creates xplanetFX[COLOR="#FF0000"]1[/COLOR].png then next refresh creates xplanetFX[COLOR="#FF0000"]2[/COLOR].png
and alternates between the 2 so as to have a backup.

What you can do is just tell XplanetFX to create a single image  **~/.xplanetFX/output/xplanetFX.png** then set your background to the same file path.(no numbering)
(The naming doesn't matter as long as the output file and ***org.gnome.desktop.background picture-uri*** point to the same image.)

After you have run xplanetFX once, you should have a **~/.xplanetFX/output/xplanetFX.png** file. 
Set your background to the newly created image with this terminal command
```
gsettings set org.gnome.desktop.background picture-uri 'file:///home/[COLOR="#FF8C00"]glen[/COLOR]/.xplanetFX/output/xplanetFX.png'
```
Substitute your username for [COLOR="#FF8C00"]glen[/COLOR].

---

### Post by 27grains on 2017-07-13
> **guber2 said:**
> I think by default XplanetFX creates xplanetFX[COLOR=#FF0000]1[/COLOR].png then next refresh creates planetFX[COLOR=#FF0000]2[/COLOR].png
and alternates between the 2 so as to have a backup.

What you can do is just tell XplanetFX to create a **~/.xplanetFX/output/xplanetFX.png** then set your background to the same file path.

Once you have run xplanetFX, set your background to the newly created image with this terminal command
```
gsettings set org.gnome.desktop.background picture-uri 'file:///home/[COLOR=#FF8C00]glen[/COLOR]/.xplanetFX/output/xplanetFX.png'
```
Substitute your username for [COLOR=#FF8C00]glen[/COLOR].

Where exactly do I put    **~/.xplanetFX/output/xplanetFX.png**  and how do I set my background?

---

### Post by again? on 2017-07-13
> **27grains said:**
> Where exactly do I put    **~/.xplanetFX/output/xplanetFX.png**  and how do I set my background?

For the output file in xplanet put 
```
[COLOR="#FF0000"]/home/**pillar32**/.xplanetFX/output/xplanetFX.png[/COLOR]
```

Then in xplanetFX hit the save button then the execute button.

Once the image has been rendered run this command in terminal to set your desktop background to point to the same image
```
gsettings set org.gnome.desktop.background picture-uri 'file://[COLOR="#FF0000"]/home/**pillar32**/.xplanetFX/output/xplanetFX.png[/COLOR]'
```

---

### Post by 27grains on 2017-07-13
> **guber2 said:**
> For the output file in xplanet put 
```
[COLOR=#FF0000]/home/**pillar32**/.xplanetFX/output/xplanetFX.png[/COLOR]
```

Then in xplanetFX hit the save button then the execute button.

Once the image has been rendered run this command in terminal to set your desktop background to point to the same image
```
gsettings set org.gnome.desktop.background picture-uri 'file://[COLOR=#FF0000]/home/**pillar32**/.xplanetFX/output/xplanetFX.png[/COLOR]'
```

    It worked Thank You

---

### Post by vasa1 on 2017-07-13
Then you can mark your thread [SOLVED] as shown here: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by again? on 2017-07-13
> **27grains said:**
> It worked Thank You
No problem.
We got there ....eventually. ;)

FYI the ~ (tilde symbol) represents your home directory and the shell interprets it as this.
If your not entering a path into a terminal it's best practice to use the full path.
i.e. 
"**/home/pillar32**/.xplanetFX/output/xplanetFX.png" instead of "**~**/.xplanetFX/output/xplanetFX.png"

---

