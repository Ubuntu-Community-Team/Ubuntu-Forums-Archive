---
title: "New to Linux - Im confused on what desktop decorator I should Install?"
date: 2009-08-15
forum: Desktop Environments
---

### Post by therocco2k on 2009-08-15
I've been through hundreds of Forums and Sites trying to figure out What I need to do, to Make my Ubuntu Gnome Desktop look Outstanding.

I've been told to install Compiz - What I installed is CompizConfig Settings Manager, I don't even know if I have COMPIZ.

I've Installed Emerald Theme Manager, and I open it up and there is no way to apply any settings or use the thing?

I've heard of Avant Navigation Theme, Avant Manager

I have all these Different applications, which don't work - and I just would like to know WHAT Program(s) Should I have to be able to Turn Gnome into Customized Outstanding looking desktop?

I Mean - Do I need Compiz Config Manager or Emerald Theme Manager, Avant?

Which do I need to Uninstall, and exactly what can I install that is easy to use and is the BEST Desktop "Enhancer"  and where can I get directions to install it no problems?

For your time I've attached a Rare, Extremly HD, Beautiful Wallpaper that I found and I think that you will use it on your desktop for sure, It's 1680px × 1050px Wallpaper.  I really want to get rid of this headache and get 1 or 2 of the best App's that will make my desktop "The Coolest"...

----------------------------------------------------------------
Rocco
Myspacepage: [www.myspace.com/roccovincent]("http://www.myspace.com/roccovincent")
Thank you.
----------------------------------------------------------------
[]("http://www.myspace.com/roccovincent")

---

### Post by oldos2er on 2009-08-15
To enable compiz, go to menus System, Preferences, Appearance, Visual Effects tab, click Extra.

---

### Post by therocco2k on 2009-08-16
Ok I Had that Enabled.... So That's Compiz? That's no Problem

I want to make my desktop Spin like a Cube with the 6 Faces, and have other cool features like little running applets on my desktop that show weather and news and stuff.

What do I download for that? Can I get a link for download and instructions?

I Have Emerald, but every time I try to pick a Theme in Emerald, I go ino a terinal and type emerald --reaplce and it's turns the theme on but then it said Reloading and stays like that for hours, and when I exit out of the terminal, the Theme goes away.

I need help for that as well.

Tanks you So much,

---

### Post by wotsit on 2009-08-16
For weather things and nice looking widgets get gDesklets from add / remove programs under the application menu. Then you'll probably want Avant Window Navigator (think graphical toolbar you get with the mac) which you can get from Synaptic, download it then run

avant-window-navigator

from inside a terminal, then just click and drag applications on to the menu bar at the bottom of the screen. Right clicking somewhere on the menu can change settings. Then for icons and themes, go to gnome-look, 

here is a link to my current icon set

[http://www.gnome-look.org/content/show.php/BuuF-iconset?content=46201](http://www.gnome-look.org/content/show.php/BuuF-iconset?content=46201)

and my general theme

[http://www.gnome-look.org/content/show.php/SlicknesS?content=71993](http://www.gnome-look.org/content/show.php/SlicknesS?content=71993)

with bits of this theme

[http://www.gnome-look.org/content/show.php/CarbonMine?content=94731](http://www.gnome-look.org/content/show.php/CarbonMine?content=94731)

for installing system-wide themes, download it to the desktop or something, then do

cd Desktop

sudo mv themename /usr/share/themes

for implimenting the theme system-wide. Then it's pretty much the same for icons but its /usr/share/icons

umm... Finally you may like to take a look at Conky (sudo apt-get install conky) which is a cool system monitor found on the pics in the links. There are loads of tutorials on this. As for emerald, I've never had it stall on me, so I can't really help. Try this link

[http://ubuntuforums.org/showthread.php?t=665992](http://ubuntuforums.org/showthread.php?t=665992)

Hope that helps!

Oh finally, when you have your apps on the desktop, don't forget to add them to system>preferences>sessions or they won't be there when you restart your comp.

---

### Post by mcduck on 2009-08-16
> **therocco2k said:**
> Ok I Had that Enabled.... So That's Compiz? That's no Problem

I want to make my desktop Spin like a Cube with the 6 Faces, and have other cool features like little running applets on my desktop that show weather and news and stuff.

What do I download for that? Can I get a link for download and instructions?

I Have Emerald, but every time I try to pick a Theme in Emerald, I go ino a terinal and type emerald --reaplce and it's turns the theme on but then it said Reloading and stays like that for hours, and when I exit out of the terminal, the Theme goes away.

I need help for that as well.

Tanks you So much,

To adjust Compiz settings as you wish you'll need the CompizConfig Settings Manager. (The appearance-dialog that's included by default only switches between Metacity no desktop effects) and two different pre-configured setups for Compiz.

(so the only really important program to install is  CompizConfig Settings Manager. Everything else is either included by default or only required for some extra features you might or might not want. Just choose some nice themes and you'll have a great looking desktop.)

What comes to Emerald, you only need it if you prefer Emerald window decorations over the ones that Metacity themes can do. If you want to use Emerald you'll have to set it as your window decorator in CompizConfig Settings Manager, under the Window Decoration-plugin's settings. Just change the command to "/usr/bin/emerald". 

The reason why Emerald quits when you start it from  terminal and then close the terminal is that if you do it like that, Emrald runs as child process of the terminal. When you close the parent process, all it's child processes are closed as well. Better way is to use the Run dialog (press Alt-F2) and start emerald from there. This will, however, start Emerald only that time, you still need to set it as default decorator in Compiz settings to make it start automatically.

Then there's of course GTK, which you already have, and which is what handles how your applications look like. Just get the themes you like from gnome-look.org and install them and you're good to go.

Now you have you application theme, window borders and all desktop effects covered. Installing anything else depends on what you want, do you want a dock, desktop widgets, text-based information on your desktop etc..

---

### Post by gjoellee on 2009-08-16
Maybe you can learn something here: [http://news.softpedia.com/news/Ubuntu-8-10-Desktop-Customization-Guide-100830.shtml](http://news.softpedia.com/news/Ubuntu-8-10-Desktop-Customization-Guide-100830.shtml)

---

### Post by oldos2er on 2009-08-16
Emerald needs compiz running as window manager. If you install the package fusion-icon, it gives you an easy way to control both Emerald and compiz (from an icon on your panel).

 More info here: [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by therocco2k on 2009-08-17
Thank you all for the Extremely Descriptive Explanation of everything. I now have a Clear Understanding on how everything Works, (EXCEPT Compiz Config with all its effects and 3d cubes, never can figure them out...) 

- I Have Avant Navigator Up and Running, I've gotten my Emerald Theme's loaded, icons loaded, Now I'm going to download gDesklets for Desktop Applets suggested to me by wotsit. If anybody knows of a better Desktop Applet Program please let me know.

Otherwise, Thank you for all your help!:KS

---

### Post by mcduck on 2009-08-17
> **therocco2k said:**
> Thank you all for the Extremely Descriptive Explanation of everything. I now have a Clear Understanding on how everything Works, (EXCEPT Compiz Config with all its effects and 3d cubes, never can figure them out...) 

- I Have Avant Navigator Up and Running, I've gotten my Emerald Theme's loaded, icons loaded, Now I'm going to download gDesklets for Desktop Applets suggested to me by wotsit. If anybody knows of a better Desktop Applet Program please let me know.

Otherwise, Thank you for all your help!:KS

Screenlets. gDesklets is quite old, and uses pixmpap graphics while Screenlets was made to be used with Compiz (or other compositing managers) and uses vector graphics for smoother, scalable graphics.

[http://www.screenlets.org/index.php/Information]("http://www.screenlets.org/index.php/Information")
[http://gnome-look.org/?xcontentmode=6700]("http://gnome-look.org/?xcontentmode=6700")

---

