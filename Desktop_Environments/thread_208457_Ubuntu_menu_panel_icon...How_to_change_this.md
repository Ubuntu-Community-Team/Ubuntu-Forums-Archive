---
title: "Ubuntu menu panel icon...How to change this?"
date: 2006-07-03
forum: Desktop Environments
---

### Post by wargames on 2006-07-03
Ok, I want to change the ubuntu logo next to the Applications menu item but so far I can't figure this out. It was easy in Breezy, but it's still a no go in Dapper. I've searched the forums and nobody seems to have an answer to this. I've tried gconf-editor and setting the custom icon setting in the apps/panel/objects thing and nothing. I've tried manually putting my new icon in place of the /usr/share/icons/hicolor/48x48/apps/distributor-logo.png icon and running both killall gnome-panel and even rebooting to see if any of the changes takes effect, but nothing. Is it impossible to change this icon? And if not, then how the heck can I change it?

---

### Post by Ptero-4 on 2006-07-03
Can you change the /usr/share/icons/<iconset>/<size>/apps/gnome-logo-transparent.png icon with your own? IIRC that's the one that holds the foot icon used in the menubar applet.

---

### Post by wargames on 2006-07-05
[QUOTE=Ptero-4]Can you change the /usr/share/icons/<iconset>/<size>/apps/gnome-logo-transparent.png icon with your own? IIRC that's the one that holds the foot icon used in the menubar applet.[/QUOTE]

It's not the gnome foot logo I want to change, it's the ubuntu logo next to the Applications drop down menu. I've replaced the ubuntu distributor-logo.png in /usr/share/icons/hicolor/48x48/apps with my own, and my new icon will show up next to the "About Ubuntu" section under "System" and if I right-click the panel and choose "Add to Panel" the selection for "Menu Bar" also contains my new icon but the Ubuntu logo never changes next to Applications. I've tried the apps->panel->objects under gconf-editor and use the custom icon setting and then run killall gnome-panel and still nothing. I read others posts on this subject but it doesn't appear that anyone has an answer yet (or at least I can find) that actually works. I tried the "gtk-update-icon-cache" and that does nothing also.

Has anyone been able to change the Ubuntu logo next to the Applications drop down menu, and if so, could you provide instructions on how to do it?

---

### Post by Perfex on 2006-07-05
Breezy
[http://doc.gwos.org/index.php/Gnome_Icon](http://doc.gwos.org/index.php/Gnome_Icon)

This worked for me, only problem is you have to kill gnome after, to refresh the bar.

Dapper
[http://doc.gwos.org/index.php/Gnome_Icon_Dapper](http://doc.gwos.org/index.php/Gnome_Icon_Dapper)

---

### Post by wargames on 2006-07-07
> **Perfex said:**
> Breezy
[http://doc.gwos.org/index.php/Gnome_Icon](http://doc.gwos.org/index.php/Gnome_Icon)

This worked for me, only problem is you have to kill gnome after, to refresh the bar.

Dapper
[http://doc.gwos.org/index.php/Gnome_Icon_Dapper](http://doc.gwos.org/index.php/Gnome_Icon_Dapper)

Sorry Perfex but that did not work. It only managed to change my Ubuntu logo to the Gnome foot and that's it. I tried replacing the Gnome foot with my own icon but just like before, it will not show my icon instead of the Gnome foot icon. Same problem I've been having all along.

Maybe I'm not asking my question right or something, so here it goes....

I want to change the Ubuntu logo that's right next to the word Applications in the menu bar to my own custom icon. This was easy in Breezy but so far I  can't get it to work in Dapper. As stated above, I've tried gconf-editor, and I've tried coping my icon to the /usr/share/icons/hicolor/48x48/apps directory and replacing the distributor-logo.png and tried replacing the start-here.png icon as well. I've tried the gtk-update-icon-cache command and still nothing. I've tried Perfex link above but it only replaced the Ubuntu logo with the Gnome-foot logo, but I still can't replace the Gnome-foot icon with my own custom icon. Is that icon somehow not a stand alone graphic file? Why did restalling the gnome-menu, gnome-panel, and gnome-panel-data packages change it to a Gnome-foot instead of just keeping the Ubuntu logo up there since it came from the Ubuntu repositories?

This is driving me crazy ](*,) 

I have not found anything yet in the forums that tells how to replace the Ubuntu logo icon next the Applications drop-down menu item with a custom icon. Is this not possible in Dapper, and why not?

---

### Post by wargames on 2006-07-07
Ok this is what I did to change the Ubuntu logo next the word Applications in the menu bar to a custom icon in Dapper.

1. I followed this guide to change the Ubuntu logo icon to the Gnome foot logo icon in the menu bar:

[http://doc.gwos.org/index.php/Gnome_Icon_Dapper](http://doc.gwos.org/index.php/Gnome_Icon_Dapper)

(Thanks to Perfex above for this info.)

2. Then I copied my custom icon to replace the gnome-foot icon to this location:

/usr/share/pixmaps/gnome-logo-icon-transparent.png

3. I then used command "killall gnome-panel" and then my custom icon replaced the gnome-foot icon next to the word Applications in the menu bar.

Enjoy! :)

---

### Post by nicjasno on 2006-07-10
Doesn't work. 

Of course the distributor-logo.png was renamed and removed from the /usr/share/icons/apps/hicolor dir

but then when i renamed my cusrtom icon to gnome-foot.png and copied it to /usr/share/pixmaps  nothing happened after killall gnome-panel.

---

### Post by wargames on 2006-07-10
> **nicjasno said:**
> Doesn't work. 

Of course the distributor-logo.png was renamed and removed from the /usr/share/icons/apps/hicolor dir

but then when i renamed my cusrtom icon to gnome-foot.png and copied it to /usr/share/pixmaps  nothing happened after killall gnome-panel.


Did you make sure to name your custom icon "gnome-logo-icon-transparent.png" and not "gnome-foot.png" and then copy your custom icon (now named gnome-logo-icon-transpartent.png) to /usr/share/pixmaps/ using this:

sudo cp gnome-logo-icon-transparent.png /usr/share/pixmaps/gnome-logo-icon-transparent.png

---

### Post by nicjasno on 2006-07-10
Yep.

---

### Post by wargames on 2006-07-10
> **nicjasno said:**
> Yep.

Are you sure? You stated above you named your custom icon gnome-foot.png and then copied it to /usr/share/pixmaps/ and then issued killall gnome-panel.

If you did it like that, then yes, it would not work.

Maybe someone else can verify the steps I posted, but I tested this a few times and it changed the icon to my custom icon every time.

Give it another shot and see if it works. During my testing Dapper was picky about it, and you had to follow the steps exactly one right after the other to get it right.

Here's my review of what I did:

1. sudo rm /usr/share/icons/hicolor/48x48/apps/distributor-logo.png

2. Then go to "System-Preferences-Synaptic Package Manager" and search for "gnome-menus, gnome-panel, and "gnome-panel-data". Choose to reinstall them and click "Apply". After it finishes, remove the gnome panel from the top bar by right-cliking on it and select "Remove from Panel". Then restore the menu by right-clicking on the now-empty area and select "Add to Panel". Choose "Menu Bar" and click "Add".

With any luck, the classic Gnome foot will be back. 

3. Copy your custom icon to usr/share/pixmaps/gnome-logo-icon-transparent.png

Make sure you are replacing the original gnome-logo-icon-transparent.png (which looks like the Gnome foot) with your own custom icon using the same name as gnome-logo-icon-transparent.png. Browse to that location and verify that your custom icon is indeed in that location and has the name gnome-logo-icon-transparent.png.

4. Issue a killall gnome-panel in the terminal and your custom icon should now have replaced the Gnome foot.

These are the steps that I used and it worked. I did a Google search and someone else had stated about replacing the gnome-logo-icon-transparent.png with a custom icon, so I decided to try it in Dapper using the steps above and it worked first time, so I decided to post what I found. It would be strange for it to only work on my install.

Anyway, just try it again, and go step by step to see if it'll work.

---

### Post by m83 on 2006-07-10
I have found [the solution]("http://wiki.archlinux.org/index.php/Gnome_Custom_Menu_Icon") on the Arch Linux Wiki.

And it works. The problem is that it changes the icon only for the curent user, not globally, but it's enough for me.

---

### Post by nicjasno on 2006-07-10
m83, youre THE man !!! Workde even without killall gnome-panel. Thank you so much :)

---

### Post by wargames on 2006-07-11
> **m83 said:**
> I have found [the solution]("http://wiki.archlinux.org/index.php/Gnome_Custom_Menu_Icon") on the Arch Linux Wiki.

And it works. The problem is that it changes the icon only for the curent user, not globally, but it's enough for me.

yeah, I read about this also, but that section does not exist in my Dapper install. There was no object with the tooltip "Main Menu" so I could not use this method. That's really weird that this section in gconf-editor is not present in my Dapper install but is present in yours. :-k I wonder if this is something about how Dapper installs on one PC verus another PC. Also, how did nicjasno see the changes without issueing killall gnome-panel as the directions state? :-k

But as long as everything is working ok, good job on sticking to solving your problem. =D> Maybe someone else can use this thread to help solve their problem too.

---

### Post by lcbl86 on 2006-07-15
someone can help me???

i tried a lot of times...

i just want the foot icon on my panel, but i've tried a lot of times and theres always the ubuntu icon...

i have followed the tips above and all that you said but theres always the ubuntu icon...

---

### Post by nicjasno on 2006-07-15
m83's method works 100%. I tried it on another box here. Completly different install, worked perfect.

---

### Post by lcbl86 on 2006-07-15
hey man please help me cause i tried the m83's method but i have a problem, 

in the configuration editor i go to apps>panel>objects> but i cant find my main menu object

theres only 3 objects 

firefox_launcher_screen0

object_1

session_dialog_screen0

i dont know in the tooltip every key is blank

can you please give me a "fisher price" step by step on ubuntu dapper 6.06 LTS??? 

i just want the gnome foot!!!

---

### Post by twoseids on 2006-07-16
I tried m83's method but I couldn't change the path for my custom icon. It was greyed out. Even tried "sudo gconf-editor" but same deal.

---

### Post by MarkSheely on 2006-07-16
I have done it the following way:

First, I downloaded the .png icon I wanted to use for the menu icon onto my desktop. Then, I renamed the icon "distributor-logo.png".

Next, I opened a terminal, typed "sudo nautilus", entered my password, and navigated to the following folder:

/usr/share/icons/hicolor/48x48/apps/

Then, I dragged the new icon I want to use from my desktop into the file browser window. You are asked if you really want to replace the icon that is already in the file; click yes, because of course that's the whole point of doing this.

Close nautilus.

Remove your old menu from the panel, and then add the menu back onto the panel. Viola! There's your new icon.

--Mark

---

### Post by twoseids on 2006-07-16
> **MarkSheely said:**
> I have done it the following way:

First, I downloaded the .png icon I wanted to use for the menu icon onto my desktop. Then, I renamed the icon "distributor-logo.png".

Next, I opened a terminal, typed "sudo nautilus", entered my password, and navigated to the following folder:

/usr/share/icons/hicolor/48x48/apps/

Then, I dragged the new icon I want to use from my desktop into the file browser window. You are asked if you really want to replace the icon that is already in the file; click yes, because of course that's the whole point of doing this.

Close nautilus.

Remove your old menu from the panel, and then add the menu back onto the panel. Viola! There's your new icon.

--Mark
I didn't have that "distributor-logo.png" file in that particular directory. I followed the steps anyway, and nope - I'm still looking at the nice Ubuntu logo.

I really don't mind. But the gnome foot would be nicer.

---

### Post by m83 on 2006-07-17
> **twoseids said:**
> I didn't have that "distributor-logo.png" file in that particular directory. I followed the steps anyway, and nope - I'm still looking at the nice Ubuntu logo.

I really don't mind. But the gnome foot would be nicer.

Maybe you have a menu-bar object type. A menu-bar object is that menu that has the Ubuntu icon and "Applications Places System" text beside it. Here is how a menu-bar object looks like:[IMG]http://hal.cs.tuiasi.ro/~afita/ubuntu-menu-bar.png[/IMG].
In this case you should look for a panel object that has "menu-bar" in the object-type property field in Configuration Editor.

Here is how Configuration Editor looks like with the view opened to the menu-bar object:
[IMG]http://hal.cs.tuiasi.ro/~afita/gnome-configurarion-editor-menu-bar.png[/IMG]
You should change the "custom_icon" property and check "use_custom_icon".

---

### Post by twoseids on 2006-07-17
Okay, I think we're getting closer. But how do I change the "custom_icon" property? If I right-click on "custom_icon" I have "Edit Key" and "Unset Key" as possible options. I'm afraid to do "Unset Key" so I haven't. When I select "Edit Key" I get this:

[IMG]https://mail.jaars.org/~eric_seidlitz@sil.org/key.png[/IMG]

---

### Post by m83 on 2006-07-17
That's where you anter the path to the icon that you want to show as the menu button. Like so: /usr/share/icons/hicolor/48x48/apps/gnome-main-menu.png (try entering that, see what happens ;) ).

---

### Post by equilibrium on 2006-07-21
the custom_icon key doesn't seem to work for the "menu-bar" object.
> The location of the image file used as the icon for the object's button. This key is only relevant if the object_type key is "drawer-object" or "menu-object" and the use_custom_icon key is true.
if you change it to "menu-object" the custom file seems to be shown but it looks like a normal launcher with no "Applications" "Places" or "System" menus :(

---

### Post by UberPuppy on 2006-08-09
Hehe, I think I found a solution - entirely by accident. 

Step 1: mv you icon to ~/.icons/distributor-logo.png

And THAT's IT!

I did this entirely by accident when I left an icon of that name in an icon-development folder. I then moved all those icons to ~/.icons and hey presto, the thing changed on me. I'm not sure exactly when cos I didn't notice, but it did :) 

And, in case anyone's wondering ... I _never_ used the icon at all at any point prior to that (it was kinda an accidental download that I dumped straight away). 

After having spent DAYS! trying to fix this, going through gconf, manualyl replacing all start-here.png and distributor-logo.png in EVERY folder on the entire system, I cannot believe it's so easy! Had to tell you all.

:D Enjoy


p.s. I should qualify that I had ALREADY previously implemented the solution where gnome-panel and co were reinstalled .., so I can't actually, on second thought, guarantee that this method works prior to that one - which does the trick nicely anyway.... but at least you don't have to sudo overwrite any existing icons :)

---

### Post by GoLoGo on 2006-08-10
I cant seem to make it work. I already followed the steps in document on the website. I also deleted the distributor-logo.png in 2 different places, and re-installed all the gnome panel stuff, and it still wont give me the foot. Thanks, and yes i chose the "Menu Bar".

---

### Post by fabioleitao on 2006-08-18
Nothing I've tryed there changed the Icon... And I want to try something else besides the foot or the Ubuntu group.

I wonder if that got cached somewhere else? 

Have anyone at all been able to change that on 6.06?

For the amount of nothingness I've achieved I was starting to believe this is only a hoax.

Really frustrating.

---

### Post by jperez on 2006-08-20
> **wargames said:**
> Ok this is what I did to change the Ubuntu logo next the word Applications in the menu bar to a custom icon in Dapper.

1. I followed this guide to change the Ubuntu logo icon to the Gnome foot logo icon in the menu bar:

[http://doc.gwos.org/index.php/Gnome_Icon_Dapper](http://doc.gwos.org/index.php/Gnome_Icon_Dapper)

(Thanks to Perfex above for this info.)

2. Then I copied my custom icon to replace the gnome-foot icon to this location:

/usr/share/pixmaps/gnome-logo-icon-transparent.png

3. I then used command "killall gnome-panel" and then my custom icon replaced the gnome-foot icon next to the word Applications in the menu bar.

Enjoy! :)

I know this is a bit late, but that method worked perfectly!  I tried the whole "Apps > Panels > Objects" trick and that worked, but without having text next to the icon.  I tried this method and bam, there it is!  I can now start to make my Ubuntu system look like the T-Mobile Sidekick 3 with a custom theme.  Thanks for the info!

Jesse~

---

### Post by reubano on 2006-09-09
> **twoseids said:**
> I tried m83's method but I couldn't change the path for my custom icon. It was greyed out. Even tried "sudo gconf-editor" but same deal.

Yeah, it was greyed out for me to. Anyone know how to enable the option to chage the path? I have tried EVERY other suggestion on this and other threads and nothing has worked. It's killing me that I can't get the gnome foot icon to show.

---

### Post by strabes on 2006-09-10
this isn't working for me either. I can't even get the foot logo to replace the default ubuntu logo. I am trying to make my desktop look like OS X so this is kinda important.

---

### Post by reubano on 2006-09-10
I just noticed something wierd when I log out and log back in to ubuntu. WHen it is first loading the screen after I log in, I see the foot but then it dissapears once my desktop theme is applied (the quick launch icons change slightly too as well). Has neone else noticed this or know how/why it does that?

---

### Post by jperez on 2006-09-11
For those looking to replace the Ubuntu logo in the **gnome-panel** using a *menu-bar* and not *menu-object*, I may have the solution for you!

I decided to do a simple file search for all files with the word "logo" in the filename and I eventually came the conclusion that the **distributor-logo** is indeed the file that needs to be changed, but not within:

```
/usr/share/icons/hicolor/48x48/apps/
```

directory, but in the this directory:

```
/usr/share/icons/Tango/scalable/places/
```

The **distributor-logo.svg** is the file that needs to be changed.  So, find a or create a custom SVG file and then open a terminal.

------

**[size=5]Method 1[/size]** (Command-line driven)

If you're not afraid of the command-line, then simply type this in:

```
cd ../
cd ../
sudo mv /usr/share/icons/Tango/scalable/places/distributor-logo.svg.bak
sudo mv *<PATH>*/filename.svg /usr/share/icons/Tango/scalable/places/distributor-logo.svg
```

Replace *<PATH>* with the path to the custom SVG file and *filename* with the name of your SVG.

```
killall gnome-panel
```

You're done and if that's the logo that it's working off of, then you'll see the changes right away!


**[size=5]Method 2[/size]** (File Browser)

If you think you might mess up using the command-line, then fear not.  Here's the method for you.  In the terminal, type:

```
sudo nautilus
```

This will open up the File Browser, but as the root (or superuser) and changes can be made to system files.  Head over to the directory:

```
/usr/share/icons/Tango/scalable/places/
```

Rename the **distributor-logo.svg** to **distributor-logo.svg.bak**, find your custom SVG file, rename it **distributor-logo.svg** and then close the browser.  Now, as in Method 1, type this in the terminal:

```
killall gnome-panel
```

Then if all was done correctly and if the panel is running off that logo file, then you'll see the changes right away!

------

I hope this helps everyone to have custom panel icons so that the panel can match your theme.

Jesse~

---

### Post by gabbman on 2006-09-11
How do you change a png file to an svg file, renaming it only puts and x where the ubuntu logo used to be.

---

### Post by crossedout on 2006-09-11
You can inter-mix the png and svg files.

-Xout

---

### Post by gabbman on 2006-09-11
I don't think so, I followed all of the above, and then googled apple icon svg and found one that I renamed distributor-logo.svg dropped it in the /usr/share/icons/Tango/scalable/places/apps folder and found that was the ticket to success.  Previous attmpts with png's did not work.

---

### Post by jperez on 2006-09-11
That's why I said to use SVG files, but I noticed something.  Not all installs will use the same distributor logo.  I will try to make a list of all the different logos being used and the appropriate directories and filenames to replace.

I will only do this with Dapper though as I don't have a copy of Brezzy and I don't think anyone uses Hoary anymore.

Also, about PNG to SVG, there is a program that can convert them, but I don't have the necessary compiler files on my PC ot make the program.  I actually replaced my logo with a custom Apple Icon I made to pretty much close the deal on the OSX theme I wanted and I imported the PNG file I had into InkScape and traced it, then saved it.

As soon as I get the chance, I'll give the link to the PNG to SVG converter.

Jesse~

---

### Post by jperez on 2006-09-12
I think I have this little mystery of the panel icon solved, but more testing is required.  From what I have seen so far, it looks to me like the panel icon is linked to Icon Themes.

The OSX Icon Theme is Tango-based and thus looks for the panel icon in the **/scalable/places/** folder within the Tango directory.  Vista-Inspirate is Gnome Icon Theme based and thus points to the **gnome-logo-icon-transparent.png** in the system **pixmaps** directory.

Now, this is just a theory, so as soon as I figure it out, I'll post it in the HowTo section!

Jesse~

---

### Post by crossedout on 2006-09-12
@gabbman:  I currently inter-mix png and svg w/o issue so not sure why you had difficulty.

Also, icons are largely based on the current theme.  Check out the How-To in my sig to get more info.

-Xout

---

### Post by bionnaki on 2006-09-13
I've been able to change my icon to a custom icon. basically, I have a fully transparent image because I want the menu button to be invisible. the only thing visible now is the little black arrow. any ideas on how to change this?

---

### Post by wargames on 2006-09-17
Why keep beating a dead horse?

The HowTO I posted earlier in this thread works and is simple and quick. I've tried it on several computers and it worked for jperez as well.

Is it not working for others?

---

### Post by jewelz on 2006-09-23
this is THE solution: [http://www.gnome-look.org/content/show.php?content=36903](http://www.gnome-look.org/content/show.php?content=36903)
(i had to edit object0)
> 
1. add a main menu applet to your panel
2. run gconf-editor
3. go to /apps/panel/objects/object_0
4. check use custom icon
5. in custom icon key add an image path


---

### Post by wargames on 2006-09-25
> **jewelz said:**
> this is THE solution: [http://www.gnome-look.org/content/show.php?content=36903](http://www.gnome-look.org/content/show.php?content=36903)
(i had to edit object0)

I'm sorry but not the solution for the Menu Bar applet icon. You see the Main Menu applet is a drop-down style menu that will only show the icon of your choice and nothing else in the panel. What people want to do is change the icon in the Menu Bar applet and that is the one that displays the Ubuntu logo along with the separate "Applications Places System" drop-down sections all being displayed at once in the panel. The simple HowTo I posted earlier will change the Menu Bar applet icon to your custom icon and is easy. I believe people are getting the Menu Bar applet and Main Menu applet confused. Ubuntu ships showing the Menu Bar applet with the Ubuntu logo, and this is the icon alot of people want to customize. Of course you can customize the Main Menu applet icon as well but the Main Menu applet is not the exact same thing as the Menu Bar applet. Confused yet? :D 

Anyway if you want to change the Menu Bar applet Ubuntu icon, follow my HowTo listed above in this thread.

If you want to change your menu layout to the Main Menu style applet and customize that icon then follow jewelz HowTo above.

I hope this clears this up.

---

### Post by wilder on 2006-10-17
> **strabes said:**
> this isn't working for me either. I can't even get the foot logo to replace the default ubuntu logo. I am trying to make my desktop look like OS X so this is kinda important.

Hi, I've followed this tutorials:
- [http://www.taimila.com/ubuntuosx.php](http://www.taimila.com/ubuntuosx.php)
- [http://www.supriyadisw.net/2006/09/ultimate-ubuntu-dapper-look-like-osx](http://www.supriyadisw.net/2006/09/ultimate-ubuntu-dapper-look-like-osx)

And to change the icon on applications menu, after installing the OSX icon theme, do this:

```

cd
cp /home/yourusername/path/to/image.png /home/yourusername/.icons/OSX/scalable/apps/48/distributor-logo.png
killall gnome-panel

```

:rolleyes:

---

### Post by woodsworth on 2006-11-01
None of the above methods words in Edgy.

---

### Post by wilder on 2006-11-01
> **woodsworth said:**
> None of the above methods words in Edgy.

Copying the image to my icon folder worked like a charm. I'm on Edgy and my apple icon is here on applications menu and it's on "Add to Panel" window.
Only the trash icon not worked after upgrade, but i created a symbolic link named "user-trash.png" and "user-trash-full.png" and it worked again.

---

### Post by Dunhausen on 2006-11-03
Hello.  I am remastering livecd and have much headache with this problem, only worse, because I cannot start/stop gnome when remastering!

This is the bug that was keeping it from working: [http://bugzilla.gnome.org/show_bug.cgi?id=167941](http://bugzilla.gnome.org/show_bug.cgi?id=167941)

What you have to do from the shell is "touch theme_directory" and then you run gtk-update-icon-cache.

All of the solutions previous that force a refresh of the cache should work too.

---

### Post by strabes on 2006-11-15
I have solved this. [http://strabes.wordpress.com/2006/10/16/change-the-menu-bar-logo-on-ubuntu-dapper/](http://strabes.wordpress.com/2006/10/16/change-the-menu-bar-logo-on-ubuntu-dapper/)

---

### Post by themerchant on 2006-11-26
I use configuration editor, and I worked most of it out, however when I finally come to apply it, a question mark is replaced over the main menu bar, and the computer says that (image location) is not found.

---

### Post by themerchant on 2006-12-03
*bump* look above post.

---

### Post by strabes on 2006-12-03
Follow the guide I wrote on my blog which I linked to in my above post.

---

### Post by Rontie on 2006-12-16
EDGY USERS!!!!!

okay if you are using edgy and have tried everything that the boards have offered to get the logo next to the applications menu in the panel to change, then like me i am sure that you are or about to pull out your hair, 

i coped the files over like they said to do, and i made the changed in config editor, but nothing. If this is you then go to synaptic package manager and mark for reinstallation the gnome-panel. I did this and finialy after trying Everything this is the only thing that made it work for me.

---

### Post by strabes on 2006-12-16
my method works in edgy. You have to copy the files into the specific directory of the icon theme that you are using. it's worked for everyone that I walk through it with.

---

### Post by victorbrca on 2007-01-07
> **strabes said:**
> my method works in edgy. You have to copy the files into the specific directory of the icon theme that you are using. it's worked for everyone that I walk through it with.

Thanks, worked for me!!!

The only thing different is that my default theme icon used by some of the other icon themes was "GNOME” instead of Tango.


Vic.

---

### Post by dbbolton on 2008-01-21
> **strabes said:**
> Follow the guide I wrote on my blog which I linked to in my above post.
I tried your method, but my icon theme is still using the old icon. Do you think I need to update the icon cache to get it to work? I would try that, but I'm not really sure how.

---

