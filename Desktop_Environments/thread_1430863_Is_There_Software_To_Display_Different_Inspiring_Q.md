---
title: "Is There Software To Display Different Inspiring Quotes On My D?esktop"
date: 2010-03-15
forum: Desktop Environments
---

### Post by AlexanderDGreat on 2010-03-15
Hi, I've searched Google, but no answer. I've seen some websites that display, nice inspiring quotes, sayings, inspirational thoughts from people.

Is there a way for Ubuntu to have a feature like this, particularly in my desktop? Do you do it via a wallpaper? A program? What do you suggest? The reason, I want to be inspired :D:P:KS, I use Ubuntu for work. Thanks for reading. :)

---

### Post by AlexanderDGreat on 2010-03-18
Is there anyone out there, coz it's getting harder and harder to breathe. Oh oh oh!:guitar:

---

### Post by mcduck on 2010-03-18
Well, "fortune" is the traditional tool used for this kind of purposes (it gives random quotes or "fortunes" from text databases).

On the other hand fortune itself is just a  command-line application. Wanda the Fish-applet for Gnome panel will give you fortunes when you click on it (if you have fortune and some fortune files installed). If you want a graphical window with some fortune when you log in it only takes a very simple script to do that. Or if you want them on your desktop you could probably use Conky together with Fortune.

You should probably define what exactly you want.. :)

---

### Post by mcduck on 2010-03-18
..Actually the idea of having a changing fortune text on the desktop was a nice enough idea for me to figure out how to do it:

**1.** First, you need to install some stuff (you may of course add whatever other fortunes files you might like):
```
sudo apt-get install fortune-mod fortunes conky-std compizconfig-settings-manager
```


**2.** Then, you'll need to create a configuration file for Conky. Here's the settings I used (although I changed the fortune command in this post to not include offensive fortunes. Check "man fortune" to enable them if you want), just save the text as ~/.conkyrc (you'll most likely need to change the font & size settings depending on your display resolution & personal taste..):
```
alignment bottom_right
gap_x 20
gap_y 100
minimum_size 700 200
maximum_width 700
maximum_height 200

background no
own_window yes
own_window_class Conky
own_window_type normal
own_window_transparent yes
double_buffer yes

use_xft yes
xftfont Constantia:size=15

default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
border_width 1
stippled_borders 0

update_interval 10.0
text_buffer_size 300
out_to_console no
out_to_stderr no
extra_newline no
uppercase no
use_spacer none

TEXT
${execi 60 fortune -sn 300 | fold -s -w 80}
```

**3.** Next some Compiz stuff to get the Conky to display correctly (while it *should* be possible to do all this directly in Conky's settings it didn't quite behave correctly for me so I used Compiz plugins instead). Do the following things in CompizConfig Settings Manager:

- In the Window Decoration-plugin you need to disable decoration & shadows for the Conky window. IF you have no other configurations there you can simply set both "Decoration windows" and "Shadow windows"-fields to "!(class=Conky)

- enable the "Window Rules"-plugin and add "class=Conky" to Skip Taskbar, Skip Pager, Below, Sticky and No Focus -fields.

- If you want to, enable the Opacity, Brightness and Saturation -plugin and add "class=conky" to window specific settings & set the transparency to your liking. (I set it to 50).
[B]
4.[/B] You'll want Conky to start automatically, so go to System/Preferences/Startup Applications, Click the "Add"-button and set the command to "conky" (you can set the other fields to whatever you want).

**5.** That's it. Press Alt-F2 and run "conky" to test how it works, and then start tweaking the .conkyrc to your taste. :)

This is in no way a perfect solution, mostly because all fortunes have different length and the fortune output can't be aligned or formatted in Conky (at least piping it through the fold command fixes fortunes with too long lines). Like I said, many of the stuff  about the window management, and also text transparency, *should* be configurable from Conky itself but the font opacity seems to do absolutely nothing for me, and window rules set from Conky were a bit buggy. This at least works, even though some fortunes aren't aligned on the desktop as nicely as I'd like them to be...

---

### Post by AlexanderDGreat on 2010-03-20
You are a genious. I will report back what happened after doing what you said. Thank you my friend. :)

---

### Post by AlexanderDGreat on 2010-03-24
OK I did it, except for the Compiz part. But before I want to fully implement your teachings sir, how do I get to use my own quotes?

That fortune is neither funny, wise, educational, or inspiring, it's the contrary... It's poor, it's annoying, it's depressing, it's mind-blanking, it's phony, and it's disgusting. It ruins my day! It's like if a shoe can talk that's what it will say. Geesh, i hate it!

Example quote: if the shoe fits, it's ugly. What the f**k?

---

### Post by mcduck on 2010-03-24
Check "man fortune" for fortune's options, and also the fortune files located in /usr/share/games/fortunes. There's a wide selection of different types of messages, and you can tell fortune to only pick messages from the files you want.

Here's a guide to making fortune files: [http://www.jason.mock.ws/wordpress/2...-fortune-files]("http://www.jason.mock.ws/wordpress/2...-fortune-files")
The short version is that you need to create a text file with the messages, using a line with "%" to separate the messages from each other. Then run "strfile messages messages.dat" to create a .dat file that fortune uses for selecting random messages, and put both files into /usr/share/games/fortunes.

You might want to check this thread as well: [http://ubuntuforums.org/showthread.php?t=1262037]("http://ubuntuforums.org/showthread.php?t=1262037&highlight=fortune")

You can also find lots of ready-made fortune files from the web, just do a search for "fortune files" or something.. For example I'm currently using quotes from Discworld books by Terry Pratchett.

---

### Post by AlexanderDGreat on 2010-03-24
Thank you once again sir, as my gift of appreciation, a fortune. Do you like Michael Jordan? I found this in YouTube, hope you like it as well:

[http://www.youtube.com/watch?v=_-EyRUgp9Mk]("http://www.youtube.com/watch?v=_-EyRUgp9Mk")

---

