---
title: "gnome-panel transparency (looking for an actual solution)"
date: 2010-01-16
forum: Desktop Environments
---

### Post by digitalchemystery on 2010-01-16
I've searched around as extensively as made sense, but I keep finding the same old, non-solutions. I'll explain the problem:

gnome-panel doesn't seem to be aware of desktop compositing. To see an application which handles it correctly, observe how gnome-terminal (with something like compiz) handles transparency. 

gnome-panel appears to fake transparency by layering a portion of the wallpaper onto its background. this creates a strange disconnect when using compiz's wallpapers plugin, as the wallpaper painted on gnome-panel will be the wallpaper set for nautilus to draw, as opposed to the one actually drawn by compiz.

some have suggested to enable a transparency rule in compiz to make gnome-panel transparent, but this has the unfortunate (and unacceptable) side-effect of altering the transparency of all children of the panel (icons, text, dialogs, etc.). In addition to this eyesore, many wallpapers simply look wrong when applying compiz's transparency to the panel.

A solution to this problem will require fixing the area in gnome-panel's source where it incorrectly handles transparency. Depending upon the design of gnome-panel, this could be very difficult or laughably easy.

I'll compare the implementations in gnome-panel and gnome-terminal to see if I can make a patch, but it'd be nice if someone who knows more already could help/direct where this needs to happen.

This is a true eyesore, and it's a point of embarassment in a modern desktop.

---

### Post by digitalchemystery on 2010-01-16
I might as well document some of what I've done.

It really doesn't matter where development happens, but I'm doing mine in /usr/local/src. I've made one of my groups the owner of this folder and set permissions accordingly.

To get copies of the source for gnome-panel and gnome-terminal:

```

apt-get source gnome-panel gnome-terminal

```

Once in the src directory for gnome-terminal, I took a shot at finding some mention of "transp" in the source files:

```

grep transp *

```

I got a couple of matches -- a couple of leads to follow:

> 
gnome-terminal.schemas.in:          "image" for an image, or "transparent" for either real transparency if
gnome-terminal.schemas.in:          a compositing window manager is running, or pseudo-transparency
profile-editor.c:      SET_SENSITIVE ("transparent-radiobutton", !bg_type_locked);
profile-editor.c:  SET_ENUM_VALUE ("transparent-radiobutton", TERMINAL_BACKGROUND_TRANSPARENT);
profile-editor.c:  CONNECT ("transparent-radiobutton", TERMINAL_PROFILE_BACKGROUND_TYPE);
profile-preferences.glade:		<widget class="GtkRadioButton" id="transparent-radiobutton">
profile-preferences.glade:		      <property name="label" translatable="yes">S_hade transparent or image background:</property>
terminal-options.c:      "transparent",
terminal-screen.c:  vte_terminal_set_background_transparent (VTE_TERMINAL (screen),
terminal-screen.c:      vte_terminal_set_background_transparent (vte_terminal,
terminal-window.c:      /* Set RGBA colormap if possible so VTE can use real transparency */


Of particular interest are the hits from profile-editor.c, terminal-screen.c, and terminal-window.c.

My first step is to look for an instance of TERMINAL_BACKGROUND_TRANSPARENT in the code:

```

grep TERMINAL_BACKGROUND_TRANSPARENT *

```

This narrowed it down to checking in terminal-screen.c:

> 
profile-editor.c:      else if (bg_type == TERMINAL_BACKGROUND_TRANSPARENT)
profile-editor.c:  SET_ENUM_VALUE ("transparent-radiobutton", TERMINAL_BACKGROUND_TRANSPARENT);
terminal-profile.h:  TERMINAL_BACKGROUND_TRANSPARENT
terminal-screen.c:                                           bg_type == TERMINAL_BACKGROUND_TRANSPARENT &&
terminal-screen.c:          bg_type == TERMINAL_BACKGROUND_TRANSPARENT)
terminal-screen.c:                                               bg_type == TERMINAL_BACKGROUND_TRANSPARENT &&


Opening up terminal-screen.c in a text editor and searching for TERMINAL_BACKGROUND gives an interesting result in the function "terminal_screen_realize":

> 
  /* FIXME: Don't enable this if we have a compmgr. */
  bg_type = terminal_profile_get_property_enum (priv->profile, TERMINAL_PROFILE_BACKGROUND_TYPE);
  vte_terminal_set_background_transparent (VTE_TERMINAL (screen),
                                           bg_type == TERMINAL_BACKGROUND_TRANSPARENT &&
                                           !terminal_window_uses_argb_visual (priv->window));


That's an interesting comment, and I'm not entirely sure what the FIXME is alluding to -- gnome-terminal already seems to behave properly in the presence of a compositing window manager.

I'll look into gnome-panel's transparency handling next.

---

### Post by digitalchemystery on 2010-01-16
The grepping-for-transparency trick isn't working for gnome-panel, so it looks like I'm in for some translating.

The relevant files in gnome-panel appear to be panel-background.{c,h} and panel-background-monitor.{c,h}. I don't know much about Gdk programming, but I hope the key has something to do with the GdkPixbufs which gnome-panel appears to be using to store its background information.

I'm sure that the background monitor listens for changes in the system's wallpaper (by subscribing to gconf events) and kicks off the relevant re-painting methods. Hopefully the GdkPixbufs support alpha channels, in which case it might be a matter of creating these objects in a compatible way (and preventing gnome-panel from clipping the wallpaper and smashing it in as a layer to paint on itself).

Maybe the fix is as simple as commenting out the line where the current background is examined and applied to the panel...

---

### Post by digitalchemystery on 2010-01-16
I've narrowed my searching down to two functions in panel-background.c:

- get_desktop_pixbuf
- composite_image_onto_desktop

Somewhere in these functions should be the key to a non-obscuring true transparency for gnome-panel.

---

### Post by MooseDog on 2010-01-17
> **digitalchemystery said:**
> 

some have suggested to enable a transparency rule in compiz to make gnome-panel transparent, but this has the unfortunate (and unacceptable) side-effect of altering the transparency of all children of the panel (icons, text, dialogs, etc.). In addition to this eyesore, many wallpapers simply look wrong when applying compiz's transparency to the panel.



not quite sure i understand this, does the pic below define what you're describing?

in my compiz settings for opacity...i have the following bit:

   ```
 (class=Gnome-panel) & !(type=Menu | PopupMenu | Dialog | DropdownMenu)
```

maybe helps?

---

### Post by chewearn on 2010-01-17
hi MooseDog
He already explained in his first post why he didn't like your solution.  I'm also doing the same thing as you, but for the longest time, I also felt this is a poor solution; for the same reason as digitalchemystery explained.

To recap what digitalchemystery said, the compiz opacify makes the everything in the panel transparent: the icons, applets, etc.  Therefore, if you crank up the setting to show the background, the entire panel becomes too dim to see the icons and applets anymore.  But if you don't crank it up, the transparency is not that great.  So, you have to fiddle with the settings for a compromise.  And you repeat the fiddling when you change the wallpaper, because the brightness/colour of the wallpaper affects the visibility of the panel.

Personally, I am rooting for digitalchemystery to do a proper patch.  Unfortunately, I know squat about the programming involved to be of any help.

---

### Post by MooseDog on 2010-01-17
much clearer now.

i'm not a programmer of any sort either, but thinking out loud, maybe just maybe there is another "type" one could add to that compiz codelet to be able to exclude icons and such as you guys have described in the panel from the transparency (as to me the code !(type=Menu | PopupMenu | Dialog | DropdownMenu) is doing just that.)

---

### Post by chewearn on 2010-01-17
> **MooseDog said:**
> much clearer now.

i'm not a programmer of any sort either, but thinking out loud, maybe just maybe there is another "type" one could add to that compiz codelet to be able to exclude icons and such as you guys have described in the panel from the transparency (as to me the code !(type=Menu | PopupMenu | Dialog | DropdownMenu) is doing just that.)

Try this as an experiment.  Bump the transparency all the way down to zero.  See if you panel dissappeared completely.  I am pretty sure that's what you will get.

-----

Actually, I rechecked my settings, it's much simpler than yours, but do the exact same thing:
```
type=Dock
```However, thinking about the idea you mentioned, maybe there is way to specify the icons or applets.  I will investigate if that is possible.

---

### Post by chewearn on 2010-01-17
Whew!  That's one hour wasted.  Ok, the idea didn't work for reason that the Compiz window matching only works on top level window, and not child windows.

So, while the Dock consisted of one main window and multiple child windows (which presumably are the icons, applets, etc), forcing Compiz to act on the child windows did not work.

---

### Post by digitalchemystery on 2010-01-18
It would be nice to be able to make non-functional interface widgets transparent.... something like Type=Background. I'm not sure how universally feasible that is, but the gnome-panel, it would make the surface that the text/icons are painted on transparent.

I looked around for a couple of hours trying to get this fixed, but I'm not entirely sure what needs to be altered. I've tried some of the changes I made, but the only effect is to lose the fakely painted sliver of the background image. I've so far failed to find a way to get the panel to be transparent, but I'm sure it has something to do with how they're creating their Cairo surfaces or GdkPixbufs.

Looking through the documentation for these libraries, they appear to be ARGB-capable, but I don't know if that applies only to the layers composited within them, or if that translates to a system-wide transparency.

And again with the compiz false-solutions: try it with a wallpaper that has 'busyness' around the areas of the panel. Once you drag a window under the panel, what is on the background will be applied on the panel above the window. This is inconsistent with 'reality'. Our UIs should be intuitive and mimick physically consistent systems. The wallpaper makes sense to be below everything, and the panel makes sense to be above. There is no sense in how transparency is handled in this situation.

---

### Post by chewearn on 2010-01-18
Not sure if it helps, but I stumbled onto this site: [http://blogs.gnome.org/desrt/2007/02/18/panel-composite-bin/](http://blogs.gnome.org/desrt/2007/02/18/panel-composite-bin/)

---

### Post by digitalchemystery on 2010-01-18
That looks helpful. It's not directly related, but I might be able to get some useful information from it. 

The linked article appears to be talking about a uniform way for panel applets to have transparent backgrounds. As I've understood, it can be difficult to have a panel applet which doesn't mess up the fake transparency of gnome-panel.

I got interested in one of the results of the author. He mentions one of his failed attempts resulted in a completely transparent region of gnome-panel. This is what I'm looking for -- but it appears that the problem exists both globally in gnome-panel and in any individual applets which take their own hacks at transparency.

That's slightly discouraging, and I've seen themes mess up regions of gnome-panel, so I know that there are several different mechanisms at work.

Thanks for the post. I'll see if any of the mentioned names lead to pages with anything closer. It definitely has to be a known issue...

---

### Post by steveneddy on 2010-01-18
I know this doesn't help you, but others may get some use out of this:

[http://ubuntuforums.org/showpost.php?p=7950948&postcount=3](http://ubuntuforums.org/showpost.php?p=7950948&postcount=3)

---

### Post by steveneddy on 2010-01-19
I thought about this today and have come up with what I think is an acceptable answer from what I can tell the OP is trying to accomplish.

Why don't you just use a .jpg of the color that you want, make it semi transparent, and add additional transparency, very subtle transparency, via Compiz?

For instance, look at the attached .jpg . One could alter the color and transparency of that, make it the bar's backgrouns, to accomplish your task.

If you are wanting a completely transparent Gnome bar, just save a file with a totally transparent .jpg and use that for the background.

---

### Post by chewearn on 2010-01-20
> **steveneddy said:**
> I thought about this today and have come up with what I think is an acceptable answer from what I can tell the OP is trying to accomplish.

Why don't you just use a .jpg of the color that you want, make it semi transparent, and add additional transparency, very subtle transparency, via Compiz?

For instance, look at the attached .jpg . One could alter the color and transparency of that, make it the bar's backgrouns, to accomplish your task.

If you are wanting a completely transparent Gnome bar, just save a file with a totally transparent .jpg and use that for the background.

I actually thought of this earlier, but it doesn't work well.  Here is two screenshots to illustrate the problems with it.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=144202&stc=1&d=1263966588[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=144203&stc=1&d=1263966588[/IMG]

1 and 4: the Terminal has true transparency and shows it's background correctly.

2: I have Compiz fully transparent cube, so my desktop background is actually the skydome (i.s.o. the wallpaper).

3: gnome-panel's fake transparent background (using a transparent png) is showing the wallpaper, instead of the skydome, causing "disconnect".

5: as per 3, except with a window tucked underneath.

---

### Post by digitalchemystery on 2010-01-20
I'll post a series of images conveying the points.

01-desktop-with-seemingly-transparent-panel.resized.png
  an image of gnome-panel with the desktop shining through

02-desktop-with-false-transparency-broken-metaphor-broken-experience.resized.png
  an image which breaks the visual continuity and mental model of the computing experience

03-application-of-the-transparency-gradient.resized.png
  using a supplied transparent image for the panel's background

04-still-not-true-transparency.resized.png
  blocked windows even with a transparent background image

05-true-transparency-ruined-my-panels.resized.png
  Compiz's window-type-based transparency enabled; glass effect looks good, but the panel's icons have suffered greatly in visibility (notice the top panel's fate as well)

---

### Post by digitalchemystery on 2010-01-20
Here are some examples of solutions which don't involve gnome-panel...

06-cairo-dock-understands-layers.resized.png
  cairo-dock, once expanded across the bottom of the screen and resized, looks like a panel, and it understands transparency. that's how a panel should behave... one problem with cairo-dock (aside from its obscene customization interface) is the inability to interchange its applets with gnome-panel applets.

07-another-example-of-transparency.resized.png
  notice how the window fram is crisp and visible, how pixel shader operations can render a blur effect with the transparent layer, and that the wallpaper stays below things (where it belongs)

08-why-is-my-wallpaper-on-top-of-something-above-it.resized.png
  this particular wallpaper is a good example of why adjusting Compiz's transparency setting isn't an acceptable work-around. watch the next example for another reason.

09-tiretracks-shouldnt-be-going-over-that-window.resized.png
  some wallpapers can get by with the strange set of hacks which make things look alright. other wallpapers come along and we're reminded that it's all a lie...

---

### Post by mrcommunicative on 2010-01-24
I'm working on something like this too, primarily to get a blur effect on the gnome-panel. I have blur for my titlebars (emerald) and for docky with the glass theme. They both look great. From what I have read, older versions of gnome-panel could be composited, but the current version won't blur with Karmic.

---

### Post by XsilverX on 2010-06-24
[IMG]http://i741.photobucket.com/albums/xx51/XsilverX90/Screenshot.png[/IMG]
loged as root navigat to file system/usr/share/themes 
is you are using ambiance go to ambiance folder or if you are using radiance go to radiance folder once in there open the folder named "gtk-2.0" and open the file called "gtkrc" with gedit (as root)
find the line: 
bg_pixmap[NORMAL] = "panel_bg.png"  

and put a # before it leaving it like this: 

# bg_pixmap[NORMAL] = "panel_bg.png" 
(with a space between the # and the text)

save it, restart your computer and then right click your panel go to background and select solid color 

thats all ;D hope it works for you  
(this only works with the ambiance and radiance theme)

---

### Post by FlameReaper on 2010-07-23
> **XsilverX said:**
> <screenshot>
loged as root navigat to file system/usr/share/themes 
is you are using ambiance go to ambiance folder or if you are using radiance go to radiance folder once in there open the folder named "gtk-2.0" and open the file called "gtkrc" with gedit (as root)
find the line: 
bg_pixmap[NORMAL] = "panel_bg.png"  

and put a # before it leaving it like this: 

# bg_pixmap[NORMAL] = "panel_bg.png" 
(with a space between the # and the text)

save it, restart your computer and then right click your panel go to background and select solid color 

thats all ;D hope it works for you  
(this only works with the ambiance and radiance theme)

Doesn't exactly solve the problem here, as it does not apply *actual* transparency, which is what is being sought by the thread starter. It only achieves the effect that looks like this:

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=164340&stc=1&d=1279893269[/IMG][/CENTER]

Notice the browser's title bar hidden under the panel.

---

### Post by PhosPhoton on 2011-01-13
Bump?

Gnome-panel's "transparency" is still fake, even with Compiz. It's been like a year now and I haven't seen a fix for this.

---

### Post by chewearn on 2011-01-13
> **PhosPhoton said:**
> Bump?

Gnome-panel's "transparency" is still fake, even with Compiz. It's been like a year now and I haven't seen a fix for this.

Don't hold you breath.  There isn't going to be a fix, unless anyone of us who is annoyed submit a patch ourselves.

Gnome is fully committed to Gnome Shell.  Meanwhile, Ubuntu is dropping Gnome and working on Unity.  Nobody is working on fixing legacy issues.

---

