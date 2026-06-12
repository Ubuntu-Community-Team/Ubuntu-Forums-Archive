---
title: "Editing menus is having no effect"
date: 2007-10-03
forum: Desktop Environments
---

### Post by Daminator on 2007-10-03
I know how to edit the menu's in Ubuntu, as I've done it in the past. I found it didn't work great, but if I repeated steps a few times I could eventually get things as I wanted them. However, now I can't add anything to the menus at all. Everything looks like it should work and I go through the process of adding an item or a folder or whatever, but nothing actually changes on the menu. I've tried making a change and then logging back out and back in (as I seem to remember having to do that before), but still no change is happening.

Has anyone had this problem? C=I couldn't find it when I searched the forum.

Damian

---

### Post by tyler22 on 2007-10-03
hey i had this problem. When I restarted gnome all my menus appeared where they should be. Give that a try, hopefully it will work for you.

---

### Post by Daminator on 2007-10-03
All of my menus are where they should be, it's just that I can't add to them at all.

Am I restarting gnome when I log out and log back in again (which on my system also restarts X)? If so, I've done that and the changes still don't show.

Damian

---

### Post by Daminator on 2007-10-05
Any ideas on this? I just can't configure my menu.

Damian

---

### Post by Lord Illidan on 2007-10-05
I'm wondering, if you start alacarte from the terminal, and try to add things, does it work that way? Can't test it here as I'm on windows at uni :mad:

---

### Post by Daminator on 2007-10-05
No, I tried that. Same results

It's strange. I was hoping other had had the problem and it was just going to be a 'do this' fix, but I can't find anyone else struggling.

---

### Post by GavinZac on 2007-10-07
alacarte (ubuntu/gnome's menu editor) is absolute rubbish and is the worst aspect of the system.

im currently search for an alternative since it has decided to stop showing the Sound & Video folder altogether, despite the links existing in /usr/share/applications

---

### Post by Daminator on 2007-10-09
Post back if you find anything. I simply want to add apps to my menu and it's not possible at the moment.

---

### Post by vasiliymeshko on 2007-10-09
I remember having this problem some time ago, and it was because one of the files (or directory) alacarte needed, had owner set to 'root' Unfortunately I can't seem to remember which one it was. :confused:

Try running alacarte from console and see if any errors come up.

---

### Post by Mellthas on 2007-10-19
With Ubuntu Gutsy editing menus is much worse for me than in the previous versions. I can’t rename many of the menu items (only by editing the files by hand in my user directory) and moving is impossible with some of them. Furthermore some icons look extremely blurry (e. g. Open Office). That seems to be the case with PNG icons that are not 22×22 px.

---

### Post by reset3x on 2007-10-19
I ran into this when I was using GNOME a while back. If my new menu entries didn't appear right away I would kill gnome-panel and they would be there when then panels came back.

---

### Post by Daminator on 2007-10-22
This is starting to really frustrate me now. It's exactly the same in 7.10. Editing menus in Windows is so easy. Just go to a folder and move a few short cuts around. Why can't I edit my menus in Ubuntu!!! I've edited them fine in the past, but now it refuses to let me add an application, but doesn't give me any errors.

Ahhh!!!!

---

### Post by jeromio on 2007-11-18
+1

This is stupid. Firstly, I should be able to edit things in place as is possible in KDE and Windows. 

Secondly, I open up the Menu editor (which is called "Main menu", instead of "Menu Editor" as it should be) and nothing actually works. I click the "+ Item" button and nothing happens. Oh, the dialog is there (wait, more like 5 since I guess I clicked 5 times), but it's BEHIND the friggin window. Nice. Okay, so I create a new item and click OK. Hrm. Nothing happened. Absolutely no effect. I've tried a dozen times. This sucks.

---

### Post by Daminator on 2007-11-19
I read somewhere that it was a matter of setting the correct permissions on files, but I don't know which files.

---

### Post by mikepee on 2007-11-22
Ala Crap is what I call it.  That program is so half @ss it's embarrassing.

I want something like you get in windows.  I'm sorry did I say that... OOOPPPPPS.  You know grab a bunch of icons and toss them in a new group.  Fast simple painless and brainless... oh and it works.  Oh and the other part I'd like is well that it would work 100% of the time.  Not crap out on me almost every time I edit something.

So far Ala Carte screwed up my icon list twice when I changed a package in the package manager.  This I can forgive.  After all the two are not exactly buddies.

It's embarrassing cause the menu is suppose to make things simpler for GUI users.  Changing you menu with Ala Carte program pretty the pits.  Useful when configured but crap if your not a geek and just want rearrange you damn icon list.

The point is if the package manager ain't gonna be friends with the menu list then I am forced to be friends with the menu list for the package manager.  You follow.  So that means me and the menu list do a lot of point and click and rearrange sort of things.  So far the menu edit features... well are just plain embarrassing.

As for my research I can find anything myself.

Here's the crux of my problem with it, do this... please and you will see...
Install a program that doesn't show up on the menu (I'm cool with that part)...
 then try and find it (I'm cool with that part)... 
then add your own icon (WTF)... 

Ala Crap does nothing to make this job easy!  In fact when you click the add launcher button the stupid dialog pops up behind the ala carte windows!  Now that's quality!  Then edit your launcher... who needs a button for that... after all you'd think there would be a button cause well there appears to be a button for everything else... including room for a button... but NO!!!!!!!!!!!! you have to right click to get the properties and then edit your launcher from there (and yes the dialog also pops up behind the main ala catre window!!!!!!!!)  Forget a way to back up the who menu from the program, just in case the program sucks so much it munches your menu! (yeah it's happened a few times)

Fact making the good 'ol desktop launcher icon might just be easier... but here again ala crap fails you.  If there's some magic way to send a desktop launcher to ala crap I have not found it.  But at least they thought to give use the option to send the Ala crap icon to the desktop.

How about a logical button that scans linux for logical places that store linux programs and creates a list and from that list finds any embedded icons so you can further assume that it is yes program meant to run X windows.  Then you can click on that icon from that list and Wowzers it asks you where in your Applications menu you'd like it!  Holy crap cause that's what I do when I want to add an icon to the application menu!

Just copy the damn start menu from windows... start there for basic functionality!  I'm just saying I agree with the other guy.  This program is so damn half baked it's just embarrassing.

I stand down now... I sit over here now.

Mike

---

