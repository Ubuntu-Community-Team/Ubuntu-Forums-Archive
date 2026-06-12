---
title: "Help me to &quot;customize my desktop&quot; please :)"
date: 2008-04-08
forum: Desktop Effects &amp; Customization
---

### Post by harrybazeegar on 2008-04-08
Hi all

I am running Ubuntu 7.04 with GNOME.

I want to decorate the look and feel of my computer so i decided to go to gnome-look.org and art.gnome.org and download themes.

I managed to install some themes (after a great deal of googling) and got a new look...
But what I want to know is:
1. what is the difference between : GDM theme, GTK engine and GTK theme
2. In the preferences->themes dialog, i see themes for controls, colours, window borders, and icons. what are these things? Can I install new such themes separately and independently?

3. what is metacity? what is domino? are these complete theme packages or what?

4. when i try to install "GTK engines" ubuntu says that it is "an engine and needs to be compiled". what does this mean? how is this done? and how is this different from other themes?

5. what is compiz, beryl and compiz-fusion? I have come to understand that beryl is now compiz-fusion, but correct me if i am wrong.

6. can compiz be installed "separately" or as an "addon" onto gnome or is it a separate window manager like GNOME and KDE? i guess beryl and compiz-fusion (which i think are the same) are sepatate Window Managers...

7. how can I get new Mouse Cursor themes?

8. How can I add shadows to panels and menus in my computer? ( my computer does not support desktop effects )

9. how can I make my computer support desktop effects? is installing some other Window manager an equivalent alternative?

With what I have managed with the help of google, my desktop looks like this right now:
[http://www.mediafire.com/?ylo1k3gzynm](http://www.mediafire.com/?ylo1k3gzynm)

(sigh)... thats alot to write.. and a lot more to answer i guess.... :)

---

### Post by scraghty604 on 2008-04-08
Im new also but all i did was use compiz-fusion ..and the emerald theme manger good enough for me...compiz comes built in on the 7.10  mabey time for an upgrade..

---

### Post by spupy on 2008-04-08
> **harrybazeegar said:**
> Hi all

I am running Ubuntu 7.04 with GNOME.

I want to decorate the look and feel of my computer so i decided to go to gnome-look.org and art.gnome.org and download themes.

I managed to install some themes (after a great deal of googling) and got a new look...
But what I want to know is:
1. what is the difference between : GDM theme, GTK engine and GTK theme
2. In the preferences->themes dialog, i see themes for controls, colours, window borders, and icons. what are these things? Can I install new such themes separately and independently?

3. what is metacity? what is domino? are these complete theme packages or what?

4. when i try to install "GTK engines" ubuntu says that it is "an engine and needs to be compiled". what does this mean? how is this done? and how is this different from other themes?

5. what is compiz, beryl and compiz-fusion? I have come to understand that beryl is now compiz-fusion, but correct me if i am wrong.

6. can compiz be installed "separately" or as an "addon" onto gnome or is it a separate window manager like GNOME and KDE? i guess beryl and compiz-fusion (which i think are the same) are sepatate Window Managers...

7. how can I get new Mouse Cursor themes?

8. How can I add shadows to panels and menus in my computer? ( my computer does not support desktop effects )

9. how can I make my computer support desktop effects? is installing some other Window manager an equivalent alternative?

With what I have managed with the help of google, my desktop looks like this right now:
[http://www.mediafire.com/?ylo1k3gzynm](http://www.mediafire.com/?ylo1k3gzynm)

(sigh)... thats alot to write.. and a lot more to answer i guess.... :)


1. GDM is Gnome Display Manager. It is the screen you see after ubuntu has started and waits for your login. GTK (Gnome Toolkit) is the buttons, menu, toolbars, text areas - all those elements that build the graphical interface of the programs. A GTK theme changes the way these things look. The Engine is a "library" that is loaded by GTK to apply the theme you chose. Different theme use different engines.

2. In Gnome there are themes for 3 things: GTK (buttons,etc.), Windows borders, and Icons. You can install these separately. A complete theme contains 3 themes for these 3 things i listed, so all thing will look the same. For example, a OSC theme will have 3 things: GTK theme that will make the buttons (GTK) look glossy/aqua like OSX; a theme for the window borders to make them have that metal look with the 3 colored buttons on the top left; and an Icon theme that makes all the Icons look like they OSX equivalents. Of course, you can select GTK/Window/Icon themes from different theme packs, but they most probably wont look good together. Icon themes are located in a folder ".icons" in your home folder, gtk (+window border) themes are in the folder ".themes". 

3. Metacity is a window manager - the program that creates the window borders - the title bar, the minimize/restore/close buttons, and the endges with which you can resize the windows. A theme for the window borders is actually a Metacity theme.

4. Some themes need engines that are not installed by default. Look for these engines in Synaptic. If you can't find them, you need to compile them in order to use that theme. Compiling a theme engine is not that hard, but it's not so short to explain.

5. Beryl was a fork of Compiz. Recently, Beryl was merged back to Compiz and Compiz was renamed Compiz-Fusion. It is a program that replaces Metacity. It also is able to create the cool visual effects.

6. Compiz is a window manager. You can actually use Compiz without gnome, on its own.

7. I don't know where is the folder that contains cursor themes, but I think you can select and install new ones from the mouse preferences control panel.

8. So Compiz doesn't work? You can try xcompmgr. It is not a window manager, but provides simple effect as drop shadows and transparency. Beware that it is not very stable, and it is not always lighter than compiz, but you can still try it out. Also, KDE4 has built-in effects as drop-shadows and stuff.

9. I really have no idea. Search the forum for people who have the same video card - maybe someone found a solution?


(Pfew, sorry if there are typos. I tried to anwer as best as i I know. Hope that info helps! :D)

---

### Post by harrybazeegar on 2008-04-09
thanks! :)

so now...
1. okay... so is metacity an engine? or just some pore old theme? or a theme that uses an engine or an engine that uses a theme??

2. --SOLVED--

3. is Domino a window manager too? what is the difference between a window manager and a theme? between window manager and a GTK engine?

4. ok... so how do i compile a theme? is it done just the way a program source code is compiled?( configure , make , make install )??

5. so i can install beryl aka compiz-fusion and have cool effect EVEN IF desktop effects are off?

6. so how do i install compiz and/or beryl/compiz-fusion on my comp? It will just behave like another desktop environment like KDE and GNOME, wont it? will it allow me to select it as my current session? 

7. --SOLVED-- : installed program called gcursor... it allows me to change cursor themes on ubuntu 7.04

8. hmmm... so installing compiz will let me add shadows and "other cool stuff" to my panels and things, right?
and what is xcompmgr? it is a window manager allright, but does that mean that it is a desktop environment like GNOME and KDE? 

9. --question still open--

---

### Post by Therion on 2008-04-09
[Metacity](http://en.wikipedia.org/wiki/Metacity) explained.

[GTK](http://www.gtk.org/) explained.

[Window Managers](http://xwinman.org/intro.php) for XWindows explained.

[xcompmgr](http://wiki.archlinux.org/index.php/Xcompmgr) explained.

RE: #9: Assuming your hardware profile supports it -- [How to Setup Compiz Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion).

---

### Post by harrybazeegar on 2008-04-10
okay... so now i know that metacity is a window manager, so are beryl and compiz.
on the other hand GNOME and KDE are desktop envionments. 

But one place it was stated "Metacity is fully compliant with GNOME, but does not require GNOME to run". does this mean that metacity can function as a desktop environment too?

and are GTK engines the same as as window managers? if not, what are they?

and what is Qt? is it the same to KDE what GTK is to GNOME? if not, what exactly is it?

I read at [http://wiki.archlinux.org/index.php/Xcompmgr](http://wiki.archlinux.org/index.php/Xcompmgr) :
> 
[COLOR="RoyalBlue"]Introduction[/COLOR]
Xcompmgr is a simple composite window manager, capable of rendering drop shadows and, with the use of the transset utility, primitive window transparency. Designed solely as a proof-of-concept, xcompmgr is a lightweight alternative to Compiz Fusion and similar composite managers.

Because it does not replace any existing window manager, it is an ideal solution for Openbox and Fluxbox users seeking a more elegant desktop.

[COLOR="RoyalBlue"]Prerequisites[/COLOR]

Xcompmgr requires the following:

    * Xorg must be installed, configured and running
    * Composite must be enabled via graphics drivers, AIGLX, or Xgl 


so... 
1. what is a composite window manager?
2. openbox and fluxbox are window managers, so can they be "installed on top of GNOME"? does this even make sense?
3. tell me true or false: themes for metacity will be differ from themes for fluxbox, compiz or any other window manager
4. what is domino?? a window manager too? or just a theme? If it is a theme, it a theme for metacity (assuming no. 3 is true)??
5. "graphics drivers, AIGLX, or Xgl " ... what are AIGLX ad Xgl? are they drivers too or are they things like OpenGL?


so 
Q1 --OPEN--
Q2 --solved--
Q3 --OPEN--
Q4 --OPEN--
Q5 --solved--
Q6 --solved--
Q7 --solved--
Q8 --solved--

Q9 --OPEN-- : can i get a short note on what "hardware profile" allows me to use desktop effects?

cheers

---

### Post by harrybazeegar on 2008-04-12
/bump

---

### Post by cardinals_fan on 2008-04-12
> **harrybazeegar said:**
>  
1. what is a composite window manager?
2. openbox and fluxbox are window managers, so can they be "installed on top of GNOME"? does this even make sense?
3. tell me true or false: themes for metacity will be differ from themes for fluxbox, compiz or any other window manager
4. what is domino?? a window manager too? or just a theme? If it is a theme, it a theme for metacity (assuming no. 3 is true)??
5. "graphics drivers, AIGLX, or Xgl " ... what are AIGLX ad Xgl? are they drivers too or are they things like OpenGL?

1. From Wikipedia: > A compositing window manager is a computer program (or system) which enables a unified window manager under X/Linux, Windows, BEOS, etc. and a compositing manager to work, literally, "in unison." This allows for advanced visual effects, such as total (or in some cases, partial) transparency, and/or fading in and out, of application windows, system panels, and the like, as well as the potential addition of simulated three-dimensional shadows beneath windows, complex animation of window resizing, reshaping and movement, to name just a few possible features.
In other words, a WM that provides the fancy stuff.  Compiz is the best known, but Xfwm4 and Metacity (in version 2.22) include compositing managers.  Xcompmgr can work within a WM.

2. Openbox can be used within GNOME (replacing Metacity) or can be used independently.  I prefer the latter for the fast, clean design.

3. Themes for Metacity are different from Fluxbox etc. themes.  GTK themes affect all GTK apps.

4. I don't know what Domino is, but a Google search reveals that there is a Domino theme for KDE.  Is [this ]("http://www.kde-look.org/content/show.php/Domino?content=42804")what you mean?

5. AIGLX/XGL "allow an OpenGL implementation to talk to the graphics card" -Wikipedia.

---

### Post by bohica8418 on 2008-04-12
wow, thank you for answering those questions, that sorts out a lot of confusion for me as well. If there was only one advantage to Ubuntu it would be how amazingly supportive this forum is. Thanks for your time!:KS

---

### Post by harrybazeegar on 2008-04-13
> a Google search reveals that there is a Domino theme for KDE. Is this what you mean?
yes, thats what I meant, thanks :)

---

