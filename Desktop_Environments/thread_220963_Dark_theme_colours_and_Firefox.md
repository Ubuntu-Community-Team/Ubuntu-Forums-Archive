---
title: "Dark theme colours and Firefox"
date: 2006-07-22
forum: Desktop Environments
---

### Post by elcu on 2006-07-22
A strange question for themers and/or desktop tweakers.  I've found a really great dark theme:

[http://www.gnome-look.org/content/show.php?content=24409](http://www.gnome-look.org/content/show.php?content=24409)

I've edited some of the colours more to my liking by editing the ~/.themes/GothicAndBlue-GTK2-0.1.3/gtk-2.0/gtkrc file:

[http://paste.ubuntu-nl.org/18612](http://paste.ubuntu-nl.org/18612) 

Problem is, it being a dark theme, it naturally has text as a light colour.  Unless I force Firefox to not let webpages use their own colours, the theme colours tend to make things invisible in some forms. Some sites seem fine: 

Ubuntu Pastebin - if I type in text, it shows up in white:
[http://img152.imageshack.us/my.php?image=screenshotubuntupastebinfirefoxps4.png](http://img152.imageshack.us/my.php?image=screenshotubuntupastebinfirefoxps4.png)

Others are hard to use:
Ubuntu forums (I had to write this up in gedit and paste it in!):
[http://img67.imageshack.us/my.php?image=screenshotubuntuforumsreplytotopicfirefoxkh6.png](http://img67.imageshack.us/my.php?image=screenshotubuntuforumsreplytotopicfirefoxkh6.png)
Imageshack:
[http://img147.imageshack.us/my.php?image=screenshotimageshackhostingfirefoxvp1.png](http://img147.imageshack.us/my.php?image=screenshotimageshackhostingfirefoxvp1.png)

So it's probably something to do with each site's coding, but are there any values I can edit in gtkrc?  I found this:
[http://live.gnome.org/GnomeArt/Tutorials/GtkThemes#head-24f2ed6e23173fd24c8b5e3f8aa369a388dae2c6](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes#head-24f2ed6e23173fd24c8b5e3f8aa369a388dae2c6)
but all my edits to the gtkrc file seem to be in vain.

---

### Post by krizazy on 2006-09-04
I have the same issue.  I can't find a way to get firefox to ignore the theme colors, and it tries to make all the input boxes/sites use it.

The problem is that certain sites specify a background color, but not a foreground color.  They assume that everyone has a black on white setup in the browser.

The problem would be solved if there were a way to tell firefox to just ignore the gtk settings, and somehow do its own thing.

---

### Post by Kabatwa on 2006-09-06
Hey krizazy and elcu,

I've been having the same problems with firefox myself and had to select all text to see whats there or just guess what I'm typing. Anyway I stumbled across this today [http://www.krakoa.dk/linux-software.html#COG]("http://www.krakoa.dk/linux-software.html#COG") it may work I don't know. I'll give it a try in a bit and let you know!


Tim

---

### Post by krizazy on 2006-09-15
kabatwa:

That won't do anything, since I don't even run gnome.  I'm having the issue in xfce.

I really wish that there were a way for Firefox to use it's own widgets, or whatever, and ignore GTK entirely.

---

### Post by elcu on 2007-05-27
Update:

Inadvertent fix found via the make Firefox widgets look less crummy thread:
[http://ubuntuforums.org/showthread.php?t=369596](http://ubuntuforums.org/showthread.php?t=369596)

Still not perfect, but I can actually read form elements now when using dark themes.

---

