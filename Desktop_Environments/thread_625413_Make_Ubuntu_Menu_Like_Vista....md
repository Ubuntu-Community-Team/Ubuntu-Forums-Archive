---
title: "Make Ubuntu Menu Like Vista..."
date: 2007-11-27
forum: Desktop Environments
---

### Post by Clayton South on 2007-11-27
Hi Everyone...Hopefully you can all help me out here.

I have my Ubuntu 7.10 installation tweaked out to look like Vista - complete with wallpapers, sounds, and icons. I've even edited the location of the start button graphic so that it's vistas button.  Now I want to do something more advanced.

I want to be able to edit the width of my menus and also to attach a graphic to them so that the menu has the functionality, look and feel of Windows Vista menu. Can someone point me in the right direction?

Thanks!

-Clayton South

UBUNTU ROCKS!

---

### Post by crjackson on 2007-11-27
> **Clayton South said:**
> Hi Everyone...Hopefully you can all help me out here.

I have my Ubuntu 7.10 installation tweaked out to look like Vista - complete with wallpapers, sounds, and icons. I've even edited the location of the start button graphic so that it's vistas button.  Now I want to do something more advanced.

I want to be able to edit the width of my menus and also to attach a graphic to them so that the menu has the functionality, look and feel of Windows Vista menu. Can someone point me in the right direction?

Thanks!

-Clayton South

UBUNTU ROCKS!

Just out of curiosity, can you show a screen shot of your work?

---

### Post by oneadvent on 2007-11-27
try slab

or USP

both are more like the windows menu....I warn you though, they have a lot to be desired. It can make the effect wonderfully (I think USP even gets where you can see through it.) but the regular gnome menu does what it does quickly and without complaining. The add on menus are a little buggy.

---

### Post by Clayton South on 2007-11-28
> **crjackson said:**
> Just out of curiosity, can you show a screen shot of your work?

Sure! Here is are two screenshots of my work. What do you think of it?

-Clayton South

---

### Post by oneadvent on 2007-11-28
Hey ya, that looks great. I have a suggestion though.

See attached screenshot for the example. 

Your gnome panel is a little sketchy because it is bigger than the picture you are using on it. You should resize it to fit correctly.

---

### Post by Clayton South on 2007-11-28
> **oneadvent said:**
> Hey ya, that looks great. I have a suggestion though.

See attached screenshot for the example. 

Your gnome panel is a little sketchy because it is bigger than the picture you are using on it. You should resize it to fit correctly.

Yes this is a problem that I found as well - as you can see from the screenshot, i sized my taskbar at 45 or so, just because any smaller it looks kind of strange. However, at that size i got the double line on the graphic coloring for my bar.  Any way to fix this with the source graphic itself? So that it is one solid color instead of with a line in the middle?

-Clayton South

---

### Post by oneadvent on 2007-11-28
I'll make ya one...gimmie a sec

---

### Post by oneadvent on 2007-11-28
Here ya go. I just used the scale option in gimp.

I sized it at 45, which is huge on my lappy....

---

### Post by Tenken on 2007-11-28
I've been lucky to avoid using Vista so far, but the most XP like menu for Gnome I've seen is the Linux Mint menu, These are the repos for their old release, just add them to your sources.list

```
## LINUX MINT REPOSITORIES
## -----------------------
##
## Cassandra (Linux Mint 3.0)
deb http://www.linuxmint.com/repository cassandra/

```

---

### Post by Clayton South on 2007-11-28
> **oneadvent said:**
> Here ya go. I just used the scale option in gimp.

I sized it at 45, which is huge on my lappy....

Thanks! Where, exactly, should I drag and drop this into?

-Clayton South

---

### Post by oneadvent on 2007-11-28
oh, sorry about that. Right click a blank spot on your panel and select properties goto background and then click on the use custom image and select the new one.

---

### Post by Clayton South on 2007-11-28
> **oneadvent said:**
> oh, sorry about that. Right click a blank spot on your panel and select properties goto background and then click on the use custom image and select the new one.

Awesome thanks!

Are you using straight up Ubuntu or another version like Kubuntu?  I have all of the vista icons but the appearance manager wont recognize them. Any suggestions and tips? let me know if you need the icons and I can send them to you.

Thanks!

-Clayton South

---

### Post by oneadvent on 2007-11-28
I am using straight Ubuntu. I had it looking much more like vista, but I backed away a little bit. What icons are not being recognized? The set I am using right now is nuoveXT.2.2

It looks close, but it isn't blue. I'm pretty sure all the icons are being recognized.

---

### Post by oneadvent on 2007-11-28
Oh, and BTW, you can change the icons by right clicking on the main menu and choosing edit menu.

You can then right click on whatever and change the icon.

---

### Post by Clayton South on 2007-11-28
> **oneadvent said:**
> I am using straight Ubuntu. I had it looking much more like vista, but I backed away a little bit. What icons are not being recognized? The set I am using right now is nuoveXT.2.2

It looks close, but it isn't blue. I'm pretty sure all the icons are being recognized.

Right now I'm using Vista-Inspirate_1.0 icons. I have PNG icons and a whole bunch more. I tried to modify the directory names in the /usr/share/icons directory...no luck. I even zipped...sorry for the windows term lol...I put them in a tar.gz file and dragged and dropped them into the theme manager...no go. I think Kubuntu has a icon manager or something like that, but im not framiliar with a similar feature in Ubuntu.  I've manually changed the icons for some programs like Firefox that I've put a shortcut on my Panel for...but thats it so far. Would love to change more if you have any helpful suggestions....

-Clayton South

---

### Post by oneadvent on 2007-11-28
the icons from gnome-look.org should drop into the icons program. (most of the time. and I believe the ones you have do. You should not have to tar them at all.)

The menu is
Main menu-->System-->Preferences-->Appearance
then:
Click Customize, icons tab, and you should be able to drop the icon tar in there.

And actually I have those installed on mine so I know thats the way to do it. Heres a screenshot.

---

### Post by mulder_edu on 2007-12-01
How exactly did you edit the taskbar images to make it look that way?  I'm not sure where the files are at.

---

### Post by oneadvent on 2007-12-01
I'm sorry, what part? (taskbar?)

This is almost all the LinstaBlackPlastic package with the nuoveXT.2.2 icon set. I did not do anything but drag and drop to the right menu. Um...that and I did a small edit on the menu pic, but that was because it seems they made it like 5 percent too small....

Anyway, what part exactly? I would love to help.

---

### Post by mulder_edu on 2007-12-01
I meant what Clayton South was referring to.  Sorry.  I meant the menu button.  He edited it to have the Vista (Peryl) start button.  Where is the menu pic that you edited?  I'm not sure where the file is at.

I attached a screen shot of what I've got so far (I even got Windows Media Player to run in wine):

---

### Post by mulder_edu on 2007-12-01
Ah, I just found what I was looking for:

[http://ubuntuforums.org/showthread.php?t=566293](http://ubuntuforums.org/showthread.php?t=566293)

---

### Post by oneadvent on 2007-12-01
Oh, right, ya once you do it once its easy.

Did you still want the icon I am using? I have a few different ones I got from gnome-look.org

---

### Post by SunnyRabbiera on 2007-12-01
well at least you are doing it on your own time as many people will be offended if you put this in the development forums.
anyhow there are some themes out there that can make ubuntu look like vista, but to be honest most of them are lackluster and have a tendency to be pixmap based.
The problem with using these themes is with open office that has a pixmap issue.
really there is no real logical reason to make your system look like windows, yes its better for transition but really its not needed.
Me I have made my system look like a combination of OS's to make my system unique as opposed to something imposed by some billion dollar company in redmond.

---

### Post by oneadvent on 2007-12-01
well 
1. I like the bar just being at the bottom because I have a 14 inch monitor, and i think it looks dumb at the top.

2. I like black and blue, and just because windows decided to use it does not mean that I want to not use it. By purposely doing something different you are conforming also.

3. I do not want my computer to be "human." I want it to be a machine. That is what it is.

4. I think that my menu is different than anything windows has had. I would rather just make it to where I look think it looks cool.

5. Lastly, I will do whatever I want with my computer and I don't give a **** if people are offended.

Thanks for taking the time to listen to my rant...

Josh

---

