---
title: "Transparent Windows with opaque text and symbols"
date: 2010-01-31
forum: Desktop Environments
---

### Post by cmd6980 on 2010-01-31
I would like to make all the windows transparent while keeping text and symbols opaque this is for a touch screen application so it has a practical purpose not just eye candy.  I basically would like to make all my windows and most apps including folders like music, documents my home folder as well as apps like calculator all to be transparent.  The transparency I seek is like that of making the terminal completely transparent.   Is this possible? I have done extensive searching and have come up empty so far I am not looking to make the windows transparent by adjusting opacity in compiz and emerald I would like to make all windows transparent not text or symbols or side bars inside the folders any help is appreciated

---

### Post by sakundiak on 2010-01-31
wel for terminal just ope it up and go to edit> profile preferences>background and the set transparency. As far as you other questions seems like normal compiz stuff to me unless you want the title bar transparent.

---

### Post by Mazin on 2010-02-01
To make all windows transparent with opaque text and symbols, you should modify GTK+ itself to support ARGB transparency with a default or customizable transparency for window backgrounds.  You would have window backgrounds, etc. be masked with partial transparency while giving text full opacity, all in the Alpha channel.

If you only need to do this to one program, then you can implement your own window-drawing routines (perhaps an abstraction around GTK+) that will do proper ARGB.

Then, a compositing window manager such as Compiz will render the windows transparent and such.

The Activity Monitor in Gnome does a basic form of transparency, but what you're looking for will take a little more work.

Ganbatte.

---

### Post by snkiz on 2010-02-01
AS it stands now Gtk doesn't do transpaency across the whole desktop welll, theres testing on that now see [http://ubuntuforums.org/showthread.php?t=1349674]("http://ubuntuforums.org/showthread.php?t=1349674")

However you can do some fiddling with the murrine theme engine (Witch Ubuntu human is based on.) To achive the effect you want you would have to enable rgba in the gtkrc for the theme and disable it for the widgets you want opaque, or change the widget you want opaque to an engine not supporting rgba. Doing this to the theme will give you transparency in applications supporting rgba on thier own. The murrine site has a list of applications that can do this.
[http://www.cimitan.com/murrine/rgba-support/list]("http://www.cimitan.com/murrine/rgba-support/list")

I have modified my shiki brave theme to use rgba and a different engine (aurora.) for buttons and notebook here's how it looks on my rig.

---

### Post by cmd6980 on 2010-02-01
ok, so apparently this is going to take more work then I thought, ok, so basically gtk won't do transparency across folders and programs so modification of gtk to support ARGB is the only way to achieve the desired effects?   Are there any tutorials out for achieving this with the murrine theme engine and never having used the Murrine engine am I going to be just spinning my wheels as a imagine there is some sort of learning curve?   thanks for the replies.

---

### Post by snkiz on 2010-02-02
If your using the default theme in Ubuntu the you are using the Murrine theme engine. What I would suggest is copy the human theme (or another Murrine based theme.) to your theme directory located at ~/.themes Open the gtkrc file and look near the top in the "engine" options for a line that looks like this:
```
rgba			= FALSE # ENABLE rgba.
```
Change that to TRUE and that will enable transparency for the whole theme. Now you scroll down and look for the "style" of the widget that you want opaque and add the rgba option in its "engine" sub-section:
```

style "entry" = "wider" {

	bg[SELECTED] = mix (0.4, @selected_bg_color, @base_color)
	fg[SELECTED] = @text_color

	engine "murrine" {
		rgba = FALSE
		focus_color = shade (0.65, @selected_bg_color)
		roundness = 2 # Overall roundness of entry box.
	}

```
This may or may not work depending on how the classes are laid out at the bottom of the gtkrc, I haven't figured all that out yet. But if it doesn't you can change the engine to another you have installed, that does the trick every time. The best way to do that would be to copy/paste a widget "style" from another theme to make sure you have the new engines options.

If it all goes to crap (and it probably will. gtk doesn't handle typos well.) check your .xsession-errors file there will be a gtk error listing what went wrong on witch line. 

There are guides out there to gtk theming, but they tend to make it very complex. I learned what I know by getting a few well documented themes and experimenting and changing options. Get a program called *thewidgetfactory* in the repos, and run it by typing twf in a terminal (The terminal will show any gtk errors.) Then you can see adjustments without reloading your desktop theme. Props to the shiki guys, their themes are well laid out and documented.

---

### Post by snkiz on 2010-02-02
Just thought you would find this useful, I ran across it in my travels today learning ROX [http://live.gnome.org/GnomeArt/Tutorials/GtkThemes]("http://live.gnome.org/GnomeArt/Tutorials/GtkThemes")

Happy reading.

---

### Post by cmd6980 on 2010-02-03
Skinz I found the link and information you provided useful thanks for the help I also looked at a few blogs and some of the upcoming features in Lucid and it seems this will be in the new release so maybe this project can wait till then but after looking over the link this just seems more involved than I really care to get for this project.  I have been working on it slowly but A themer I am not.

---

