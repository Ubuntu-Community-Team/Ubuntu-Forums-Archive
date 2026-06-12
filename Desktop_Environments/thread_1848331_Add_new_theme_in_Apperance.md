---
title: "Add new theme in Apperance"
date: 2011-09-22
forum: Desktop Environments
---

### Post by naikmanoj1991 on 2011-09-22
Today i was install new Gnome 3 shell. Its work perfectly & also its animation is too good but its default themes is not good .So I was download the new theme for Gnome 3. But i don't know how to add it in the Appearance because in my appearance window cant show the any option to add theme. 
Following image shows the screen shot of Appearance window.

---

### Post by jerrrys on 2011-09-22
where is the download site for your new theme?

---

### Post by naikmanoj1991 on 2011-09-22
> **jerrrys said:**
> where is the download site for your new theme?


[http://gnome-look.org/content/show.php/MinimaZero?content=142430](http://gnome-look.org/content/show.php/MinimaZero?content=142430)

---

### Post by jerrrys on 2011-09-22
its a "zip" package.  did you unpack it?

---

### Post by naikmanoj1991 on 2011-09-22
> **jerrrys said:**
> its a "zip" package.  did you unpack it?

Ya i was extract zip package. Hey but in the appearance window there is no option to add download theme. So how i can add it.
Just see my attachment. There is no option to add new theme.

---

### Post by jerrrys on 2011-09-22
should be at the bottom of appearance window

 [ATTACH]202709[/ATTACH]

---

### Post by naikmanoj1991 on 2011-09-22
> **jerrrys said:**
> should be at the bottom of appearance window

 [ATTACH]202709[/ATTACH]

This will show only  the 4 default themes. There is no option to add new theme.[/B] [B]I want to add new theme which is downloaded. 
Is there another way.

---

### Post by jerrrys on 2011-09-22
go to your filesystem  /user/share/icons

your theme should be there.  if not, i would suggest putting it there.  this should bring it up with the rest of your themes.

I cannot try this myself since I am running gnome3 and not gnome shell.  if this does not work, i would say to post your problem on the theme site itself.  good luck

---

### Post by naikmanoj1991 on 2011-09-22
Today i was  install new Gnome 3 shell. Its work perfectly & also its animation  is too good but its default themes is not good .So I was download the  new theme for Gnome 3. But i don't know how to add it in the Appearance  because in my appearance window cant show the any option to add theme. 
Following image shows the screen shot of Appearance window.

---

### Post by naikmanoj1991 on 2011-09-22
Screen Shot Of The appearance window

---

### Post by IanW on 2011-09-22
Sounds like you need [Gnome Tweak Tool](http://live.gnome.org/GnomeTweakTool)

```
sudo apt-get update
sudo apt-get install gnome-tweak-tool
```

---

### Post by Frogs Hair on 2011-09-22
I don't use Gnome 3  , but  I would first check the all settings tab in Appearance Preferences . If you find no option there extract the package if needed  . Run  ```
gksu nautilus
```Move the folder into usr/share/themes and see if it shows up on the theme selection menu . Dragging and dropping the theme in appearance preferences works in Gnome 2.xx but it don't know about 3 .

---

### Post by naikmanoj1991 on 2011-09-22
> **IanW said:**
> Sounds like you need [Gnome Tweak Tool](http://live.gnome.org/GnomeTweakTool)

```
sudo apt-get update
sudo apt-get install gnome-tweak-tool
```

I was done this but also on that advance setting window cant get any option to add theme

Following shows the Screen Shot

---

### Post by naikmanoj1991 on 2011-09-22
> **Frogs Hair said:**
> I don't use Gnome 3  , but  I would first check the all settings tab in Appearance Preferences . If you find no option there extract the package if needed  . Run  ```
gksu nautilus
```Move the folder into usr/share/themes and see if it shows up on the theme selection menu . Dragging and dropping the theme in appearance preferences works in Gnome 2.xx but it don't know about 3 .

i was copy the theme package and directly try to paste in the usr/share/themes but its not allow to paste in that folder.On the right click paste option is disabled

---

### Post by nilarimogard on 2011-09-22
Firstly extract the theme (I assume you've downloaded a the theme as an archive).

Then, in your home folder (that's the folder with your name), create a new folder called ".themes" - adding a "." makes it a hidden folder so later on, press CTRL + H to see it. In the newly created .themes folder, copy the extracted theme directory and it should show up in Gnome Tweak Tool.

---

### Post by coffeecat on 2011-09-22
@naikmanoj1991, I have merged your two threads. Please do not start threads on the same subject in different parts of the forum. This dilutes community effort.

---

### Post by jerrrys on 2011-09-22
User Theme Extension for gnome-shell.  check this post out

[http://ubuntuforums.org/showthread.php?t=1848516](http://ubuntuforums.org/showthread.php?t=1848516)

---

### Post by naikmanoj1991 on 2011-09-22
> **coffeecat said:**
> @naikmanoj1991, I have merged your two threads. Please do not start threads on the same subject in different parts of the forum. This dilutes community effort.

ya.Some one suggest me that post the thread in theme part. because previous thread posted in general problem part. i think normal user not able to move same thread from one part to the another part.

---

### Post by coffeecat on 2011-09-23
That's correct. Only staff can move threads. But if you want a thread moved, you can click on the report button in your post - like this: [img]http://ubuntuforums.org/images/buttons/report.gif[/img] - to request a move. Don't worry that it says "Report Abuse". You can use it to send a request to staff as well.

By the way, please use the default font and formatting, except sparingly and for emphasis. All bold is wearing on the eye. Other staff members have already edited your earlier posts. I shall now edit your latest one.

---

### Post by jerrrys on 2011-09-23
I don't know if your still interested or not, but another theme has been started here

[http://ubuntuforums.org/showthread.php?p=11278428#post11278428](http://ubuntuforums.org/showthread.php?p=11278428#post11278428)

---

### Post by naikmanoj1991 on 2011-09-23
> **coffeecat said:**
> That's correct. Only staff can move threads. But if you want a thread moved, you can click on the report button in your post - like this: [img]http://ubuntuforums.org/images/buttons/report.gif[/img] - to request a move. Don't worry that it says "Report Abuse". You can use it to send a request to staff as well.

By the way, please use the default font and formatting, except sparingly and for emphasis. All bold is wearing on the eye. Other staff members have already edited your earlier posts. I shall now edit your latest one.

Ok. Sorry for that. I really don't know about that so i was post a new thread.

---

### Post by naikmanoj1991 on 2011-09-23
> **jerrrys said:**
> I don't know if your still interested or not, but another theme has been started here

[http://ubuntuforums.org/showthread.php?p=11278428#post11278428](http://ubuntuforums.org/showthread.php?p=11278428#post11278428)

Okk. I will try to do this.

---

