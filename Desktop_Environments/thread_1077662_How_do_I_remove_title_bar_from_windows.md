---
title: "How do I remove title bar from windows?"
date: 2009-02-22
forum: Desktop Environments
---

### Post by Nycticorax on 2009-02-22
I'm using gnome. I'd like to remove the title bar / window decoration from all windows (i.e. I don't want the title and I don't want the -[]X minimise/close buttons in the top right). I am not using compiz (special effects set to "None" in the Preferences->Appearance). How do I do this? Thanks, Dan

---

### Post by Tweepy on 2009-04-13
I would like to bump this question as I find it pretty useless let me explain:
The title bar is ALWAYS present for nothing, just title and minimise expand and close, and is quite thick.
Is there any way either to set it to 5 px or remove it?
Thanks for support.

---

### Post by RuleMaker on 2009-04-13
Im not sure how would you remove the title bar but you can remove the buttons in gconf-editor.
apps->metacity->general->button_layout, set this to an empty string and you wont have buttons and menu on your window titlebar.

---

### Post by Keith Hedger on 2009-04-13
Don't know why you would want to do this but you could build your own metacity theme that doesn't actually draw any borders etc see this howto
[http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html](http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html)

Or I suppose you could install a theme then set the prefs to that window border then delete the theme it may work. suck it and see!

---

### Post by roblloyd on 2009-04-13
take a look at the program maximus. it is used in the netbook remix to make every window fullscreen, but it also removes the title bar. then you can do [this]("http://wellithinkitscool.blogspot.com/2009/03/adding-universal-buttons-to-gnome-panel.html") to add the buttons to the panel. 

hope i helped

---

### Post by Nycticorax on 2009-05-06
@Roblloyd: Thanks for that, it seems that was what I was looking for.

One imperfection: I have my gnome panel set to autohide, but a few pixels remain on show, even under maximus Any ideas how to get rid of them? I looked in gconf_editor and I have apps->panel->toplevels->panel1->auto_hide_size set to zero.

---

### Post by desiindc on 2009-10-26
> **roblloyd said:**
> take a look at the program maximus. it is used in the netbook remix to make every window fullscreen, but it also removes the title bar. then you can do [this]("http://wellithinkitscool.blogspot.com/2009/03/adding-universal-buttons-to-gnome-panel.html") to add the buttons to the panel. 

hope i helpedHi, Where can I you suitable icons for these actions (close/unmaximize/minimize)? It places the default gnome-panel-launcher.svg when I add the custom buttons to my top panel using xte. Thanks.

---

### Post by mcduck on 2009-10-26
> **Nycticorax said:**
> @Roblloyd: Thanks for that, it seems that was what I was looking for.

One imperfection: I have my gnome panel set to autohide, but a few pixels remain on show, even under maximus Any ideas how to get rid of them? I looked in gconf_editor and I have apps->panel->toplevels->panel1->auto_hide_size set to zero.

Sorry, the minimum size is 1px, and whatever you do you won't get less than that. This is because of the mechanism gnome-panel uses to handle unhiding; it checks if the mouse cursor is over the panel, and with 0px panel size this would be impossible..

---

### Post by JugglinPhil on 2009-10-26
I once did this by accident but it should do the job: 
gtk-window-decorator --replace
in a terminal, then close it disregarding the warning and the borders should disappear.
If you want them back press alt+f2 and run the same command again.
Greetings, JP

---

### Post by MadnessRed on 2009-10-26
hm how about this..

Alt+F2
Enter: gconf-editor
Go to app > metacity > general
Double click on button layout
you will see
menu:minimize,maximize,close

I think you can remove the ones you don't want from there.

---

### Post by funyotros on 2009-11-07
1st remove the windows buttons the way is shown above
2nd Edit the theme you're using with gedit.
Supposing you'r using Clearlooks:

      * Go to /usr/share/theme
      * Copy the Clearlooks directory to /home/[yourusername]/.themes to make some 
         mistakes safely  ;) , rename it (note: .themes is a hidden directory press Ctrl+H
         to see it in nautilus)
      * Open 
         home/[yourusername]/.themes/nameIchose/metacity-1/metacity-theme-1.xml
      * Look for something like 

```
<frame_style name="frame_style_maximized_[un]focused" 
```and add 
```
<frame_style name="frame_style_maximized_[un]focused" has_title="false"
```OR

```
<frame_style name="normal_maximized" geometry="normal_maximized" parent="normal" >
```and add 
```
<frame_style name="normal_maximized" geometry="normal_maximized" parent="normal"  has_title="false">
```It depends on the theme.
Experiment and you'll get results
Hope it helps

):P

---

### Post by Ginsu543 on 2010-01-23
I realize this thread is several months old, but it wasn't marked as solved and there is a very easy way to do this if you choose to use Compiz. All you have to do is install CompizConfig Settings Manager (it's in the repos). Click on the plugin called "Window Decorator". Then, change the value of "Decoration windows" from "any" to "none". Make sure to check "Enable Window Decorator" to enable the plugin. That should remove the title bars from all your windows.

---

### Post by florentin on 2010-05-04
Also you may want to check this link for removing the titlebar on maximized windows:
[http://jaket.is-a-geek.com/blog/linux/remove-titlebar-on-maximized-windows-with-compiz](http://jaket.is-a-geek.com/blog/linux/remove-titlebar-on-maximized-windows-with-compiz)

---

### Post by cprevoe on 2010-09-23
I find maximus doesn't do everything I want it to (such as run maximized java applications properly), I decided this would be good to look into and I ran with the method suggested by funyotros.

Here's how to reproduce what I've done (with the New Wave theme):
1. Copy a theme of your choice from /usr/share/themes to your ~/.themes directory
```

  cp -r "/usr/share/themes/New Wave" "~/.themes/New Wave Without Maximized Titlebars"
  

```2. Enter your theme's directory, and modify index.theme - Go through the file and change the old title to your new title ("New Wave" to "New Wave Without Maximized Titlebars" in my case). I deleted the localized names as I cannot correct them, and I'm not publishing this theme. 
```

cd "~/.themes/New Wave Without Maximized Titlebars"
gedit index.theme
```3. Modify the metacity-theme-1.xml in two places...
```

cd metacity-1
gedit metacity-theme-1.xml

```First, search out the name element near the top ```
<name>New Wave</name>
``` Change the contents to the new name of your theme```
<name>New Wave Without Maximized Titlebars</name>
```Next search for a frame_geometry block which looks like the following
```
<frame_geometry name="normal_maximized" parent="normal" rounded_top_left="false" rounded_top_right="false" rounded_bottom_left="false" rounded_bottom_right="false">
  <!-- strip frame spacing off the normal geometry when maximised -->
  <distance name="left_width" value="0"/>
  <distance name="right_width" value="0"/>
  <distance name="bottom_height" value="0"/>
  <distance name="left_titlebar_edge" value="3"/>
  <distance name="right_titlebar_edge" value="3"/>
  <distance name="title_vertical_pad" value="3"/>
  <border name="title_border" left="1" right="1" top="3" bottom="4"/>
</frame_geometry>


```Modify it so that it appears as follows:
```

<frame_geometry name="normal_maximized" parent="normal" rounded_top_left="false" rounded_top_right="false" rounded_bottom_left="false" rounded_bottom_right="false" has_title="false">
  <!-- strip frame spacing off the normal geometry when maximised -->
  <distance name="left_width" value="0"/>
  <distance name="right_width" value="0"/>
  <distance name="bottom_height" value="0"/>
  <distance name="left_titlebar_edge" value="0"/>
  <distance name="right_titlebar_edge" value="0"/>
  <distance name="title_vertical_pad" value="0"/>
  <border name="title_border" left="0" right="0" top="0" bottom="0"/>
</frame_geometry>

```Save and close metacity-theme-1.xml

4. Open the appearances options and select your new theme.

One important difference is I do not remove the button's using gconf-editor as I want buttons for non-maximized windows.

I have set this up to run with the netbook-launcher and I have configured the panel to look like the one from maximus (plus a desktop-switcher), and I think it's a lot better.

Hope this helps!

---

### Post by liveB on 2010-12-06
Actually, I find this is the easiest mod of all in Ubuntu.  Perform routine updates using update manager and voila, not only do the title bars all disappear (it seems every other update), but magically the Dvorak keyboard is no longer the default at boot.  Just sayin'

What would be cool is getting the title bars back (all programs)...

---

### Post by Svento on 2010-12-07
> **liveB said:**
> Actually, I find this is the easiest mod of all in Ubuntu.  Perform routine updates using update manager and voila, not only do the title bars all disappear (it seems every other update), but magically the Dvorak keyboard is no longer the default at boot.  Just sayin'

What would be cool is getting the title bars back (all programs)...

There's really no need for one. There's an application called Panel Buttons, displaying the buttons in the Gnome panel. Once you've gotten used to this arrangement, the title bar is just an annoying waste of screen space.

My problem is that I have no use for it because I can't figure out how to remove the title bar. Maximus gives me serious problems and the Compiz solutions don't work.

---

### Post by bvc on 2010-12-07
attached is a metacity theme with no borders, buttons ...nothing....zero. Does that help?

---

### Post by Svento on 2010-12-08
> **MadnessRed said:**
> hm how about this..

Alt+F2
Enter: gconf-editor
Go to app > metacity > general
Double click on button layout
you will see
menu:minimize,maximize,close

I think you can remove the ones you don't want from there.

Yes, the buttons but not the title bar.

---

### Post by Svento on 2010-12-08
> **bvc said:**
> attached is a metacity theme with no borders, buttons ...nothing....zero. Does that help?
Very close, indeed! The only thing missing is a title bar for the unmaximized windows... That's very fundamental. Otherwise there's nothing to grab if I need to move them. Did you make that one yourself?

I usually chose Dust Sand or Mac4Lin borders, and now some black Mac inspired thing called LK_OSX_BB. Dust Sand has been the choice when I've tried to make things work without a title bar, because that theme is available in the Panel Button application too (so that the buttons in the unmaxed windows look the same as the ones in the panel). I hope that I can figure out how to modify Dust Sand or find some modified version somewhere.

---

### Post by Svento on 2010-12-08
x

---

### Post by bvc on 2010-12-08
> **Svento said:**
> Very close, indeed! The only thing missing is a title bar for the unmaximized windows... That's very fundamental. Otherwise there's nothing to grab if I need to move them.You may know this and not care but if you press the Alt key and right click you get the titlebar menu. Alt and left click grabs the window to move.

> **Svento said:**
> Did you make  that one yourself?Yes, it's nm156 stripped,
[http://gnome-look.org/content/show.php/nm156?content=58230](http://gnome-look.org/content/show.php/nm156?content=58230)
which seems to be messed up (close button). Must be metacity updates/changes. I'll have to look into that.

> **Svento said:**
> I usually chose Dust Sand or Mac4Lin borders, and now some black Mac  inspired thing called LK_OSX_BB. Dust Sand has been the choice when I've  tried to make things work without a title bar, because that theme is  available in the Panel Button application too (so that the buttons in  the unmaxed windows look the same as the ones in the panel). I hope that  I can figure out how to modify Dust Sand or find some modified version  somewhere.Attached is a mod of Dust Sand for you. Hows that?

---

### Post by Svento on 2010-12-09
Perfect!! Thanks a lot!

---

### Post by Svento on 2010-12-13
Just a question: I'm fiddling around with the theme to make some grey stuff black. Changing the color of the titlebar was no big deal, but the frames remain grey. I can't find anywhere where the color of the frame is specified, only some things about darkening. How do I make the border black?

---

### Post by Svento on 2011-01-31
I did figure it out at last. Now I only need to find out how to make the title bar a bit lower. I only want room for my very small buttons and something to grab when I move the unmaxed windows.

---

### Post by nrundy on 2011-01-31
You can vote for this Brainstorm. You're not the only one that wishes he could get rid of the titlebar. Developers could make this simple by creating a setting that hides the Titlebar.

[http://brainstorm.ubuntu.com/idea/23919/](http://brainstorm.ubuntu.com/idea/23919/)

---

### Post by Forlong on 2011-01-31
If you want to remove your title bars with Metacity (GNOME's window manager), the proper way to go is using [Devil's Pie](http://www.burtonini.com/blog/computers/devilspie) (the Ubuntu package is called **devilspie**) with the **(undecorate)** option.

---

### Post by Svento on 2011-01-31
I can't install tar.gz:s, but if I find it as a deb file I'll try it. Does it work like Maximus? I'm looking for something that hides the title bar on maxed windows but not on the unmaxed ones.

Any way, my problem is more or less solved - I have this gtk theme that works this way, hiding the title bar when the window is maxed, otherwise showing it. Now I'm just trying to modify it to make the title bar less appearant - i.e. lower - on the unmaxed windows (as long as the window is maxed, the bar is hidden and I have the window buttons in the panel).

---

### Post by Krytarik on 2011-02-01
> **Svento said:**
> 
Any way, my problem is more or less solved - I have this gtk theme that works this way, hiding the title bar when the window is maxed, otherwise showing it. Now I'm just trying to modify it to make the title bar less appearant - i.e. lower - on the unmaxed windows (as long as the window is maxed, **the bar is hidden and I have the window buttons in the panel**).
In order to modify the geometries of the title bar, you have to edit the file "metacity-theme-1.xml" in the "metacity-1" subdirectory of your theme.

But what I'm really wondering is, how did you achieve the latter one?

---

### Post by Forlong on 2011-02-01
Sorry if I didn't make myself clear, Devil's Pie is in the [repositories](apt://devilspie).

---

### Post by Krytarik on 2011-02-01
> **Forlong said:**
> Sorry if I didn't make myself clear, Devil's Pie is in the [repositories]("apt://devilspie").
Meaning, the following command would do it:
```
sudo apt-get install devilspie
```PS: I obviously didn't check it before, removed the respective part of my previous post to not confuse someone.

---

### Post by Svento on 2011-02-01
> **Krytarik said:**
> In order to modify the geometries of the title bar, you have to edit the file "metacity-theme-1.xml" in the "metacity-1" subdirectory of your theme.

But what I'm really wondering is, how did you achieve the latter one?

The theme I got as a file in this very thread. The buttons in the panel is an panel-app simply called Window Buttons, and it's set to control maximized windows only: [http://gnome-look.org/content/show.php/Window+Applets?content=103732](http://gnome-look.org/content/show.php/Window+Applets?content=103732). With some extra work I also made an applet theme on my own with Mac style traffic like buttons.

I know what document to change, this is how I made my title bar black. The question is, what value do I change? I find nothing in there about the height of the bar. I've tried to change different settings, but nothing affects the height of the titlebar.

---

### Post by Krytarik on 2011-02-01
Thanks for the URL, I'll try it. I tried the theme attached to this thread before, but without buttons at maximized windows...;-)

The final height of the title bar seems to be the result of
- the height of the font, specified in "Appearance -> Fonts"
- "button_height"
- "title_vertical_pad"
- "title_border"
- "button_border"

---

### Post by Svento on 2011-02-01
I can't seem to make the bar lower. Also, I can't figure out how to start or use Devil's pie.

By the way: I attach my modified theme here, with black border.

---

### Post by Krytarik on 2011-02-01
Sorry for the delay, I was trying the applet, and created my own MacOSX button theme for it, to fit my metacity theme.

1. You don't need devilspie, because your metacity theme does already hide the title bar of maximized windows.

2. I fiddled a bit with your theme. To get it work, you have also to scale down each button, otherwise the buttons are displayed in the given area, but are barely visible. But the most important part is to lower the size of the window title text, like I said via "System -> Preferences -> Appearance -> Fonts". Play a bit all the settings in the upper "frame_geometry" section, to make it look good after downsizing the font and the buttons.

---

### Post by Svento on 2011-02-01
If I'd known you're using Mac buttons, I'd attached them too. I post them now, so you may try if you like. They're not from Mac4Lin, because I have a black panel and a grey ring was shown around each button. Instead I used buttons from some theme called LK_OSX_BB. My panel has the panel picture from Mac4Lin but it's blackened in Gimp and looks very good. I attach that one too...

---

### Post by Krytarik on 2011-02-01
Then I post my buttons too, they are from the [iMetal Leopard]("http://gnome-look.org/content/show.php/iMetal+Leopard+theme?content=135107") theme, with a modification to the close button when unfocused. They should fit your setup as well. I like the dots over the squares, the latter are also used in the Macbuntu theme.

PS: I don't really like too dark themes, I currently use a modified version of the above mentioned one.

---

### Post by Svento on 2011-02-01
The differences seems to be that yours don't go out completely when not focused, and that they don't have +, - and X in them. I wasn't sure if I wanted them silvery when not focused, but I chose to make them dark, so that there was no doubt that the maxed window is not focused. It looks better on a dark panel too, I believe.

One reason I favor dark colors is that I want it to look less like real Mac. I just want it macish... Next project - out of topic - is to figure out how to make the Mac4Lin GTK theme black without losing the text. If I make the text lighter in Gnome Color-Chooser, the text in the menus becomes hard to read. Because I don't like dark menus.

I try to make changes in the gtkrc document, but I can't get the menu bar text to show up in the desired color: #CFB8B8. My changes only affects Firefox, not the Gnome stuff.

---

### Post by michu_roztocz on 2011-03-11
Thank you Svento for your theme, it's very handy and does what I expected. One thing though: maybe I have missed something, but I can't see how did you managed to achieve that unmaximized windows has borders. I'm asking for that, because I would like to do the same thing with Clearlooks window border as black borders won't match with rest of my theme. Thanks in advance!

---

### Post by Svento on 2011-04-09
> **michu_roztocz said:**
> Thank you Svento for your theme, it's very handy and does what I expected. One thing though: maybe I have missed something, but I can't see how did you managed to achieve that unmaximized windows has borders. I'm asking for that, because I would like to do the same thing with Clearlooks window border as black borders won't match with rest of my theme. Thanks in advance!
I didn't do it myself so I can't really tell. But if you want to do the same with another Metacity theme, it should be easy to replace the Dust Sand buttons with Clearlooks ones. Then change the color to the desired value.

---

### Post by Alexbrown on 2011-07-31
> **JugglinPhil said:**
> I once did this by accident but it should do the job: 
gtk-window-decorator --replace
in a terminal, then close it disregarding the warning and the borders should disappear.
If you want them back press alt+f2 and run the same command again.
Greetings, JP

I used this to keep XBMC(on my media centre) in fullscreen with synergy when my mouse leaves the screen, worked just fine  :P 

been trying to do that for months

Thanks

---

### Post by SnappyU on 2012-01-16
Thanks cprevoe!  Worked for me.  I use the following values

> <frame_geometry name="normal_maximized" parent="normal" rounded_top_left="false" rounded_top_right="false" rounded_bottom_left="false" rounded_bottom_right="false" has_title="false">
	<!-- strip frame spacing off the normal geometry when maximised -->
	<distance name="left_width" value="0"/>
	<distance name="right_width" value="0"/>
	<distance name="bottom_height" value="0"/>
	<distance name="left_titlebar_edge" value="0"/>
	<distance name="right_titlebar_edge" value="0"/>
	<distance name="title_vertical_pad" value="0"/>
	<border name="title_border" left="0" right="0" top="0" bottom="0"/>
	<border name="button_border" left="0" right="0" top="0" bottom="0"/>
</frame_geometry>

---

