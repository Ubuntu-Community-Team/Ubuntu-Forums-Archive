---
title: "How to set gedit font colors"
date: 2009-06-18
forum: General Help
---

### Post by dater on 2009-06-18
Hi,

I am using Ubuntu 9.0.4. I have several other Linux distros that I use for work and home. And various kernel and distro versions. A couple of them have an older version of gedit 2.16. In it, I see that it doesn't have color schemes, but does allow you to set a color for your background and the color of the font as well as other things.

In the newer versions of gedit, such as come with Ubuntu 9.0.4, the gedit version is 2.26, and has the added feature of color schemes. This is nice, but it does not have an option to set the font color anywhere like it did in previous versions. I have googled, and searched this forum, but can see no plugin or other setting to set the font color so far. Has anyone else found a way to do this?

TIA!

---

### Post by asdfhjkla on 2009-06-18
Color schemes are set by .xml files in the following directory:

```
/usr/share/gtksourceview-2.0/styles
```

You can either edit these, or make your own - which will show up in the "Color Schemes" part of the gedit Preferences window.

You need to be a superuser to create / save files in this directory so in a terminal:

```

cd /usr/share/gtksourceview-2.0/styles
ls
sudo gedit **filename**

```

Where **filename** is either one of the existing files, or the name of your new color scheme.

If you are editing one, to set foreground and background color, edit the following line:

```
<style name="text" foreground="white" background="dark_blue"/>
```

Edit:

Don't forget to change the name of the theme or else it won't show up in the list:

```

<style-scheme id="**your theme id**" _name="**your theme name**" version="1.0">
  <author>**Your name**</author>
  <_description>**Description**</_description>
```

---

### Post by dater on 2009-06-18
Thanks asdfhjkla

I will give it a go. However I don't know why they would remove this
older functionality that was in earlier versions of gedit. I liked
the control it gave, and was hoping someone knew of a plugin or something
I was missing to be able to do it in the newer version without having
to make or edit a scheme. Guess I can complain to gedit devs.

Regards!

---

### Post by asdfhjkla on 2009-06-18
Happy to help!

This was asked about on Launchpad a couple of years ago (see [here]("https://answers.launchpad.net/ubuntu/+source/gedit/+question/14370")), and from there I found an application named [gSchemer]("http://badeagle.co.cc/gschemer.php") which allows you to create schemes through a GUI. Never used it myself, but it might be worth a look :)

---

### Post by dater on 2009-06-18
Thanks again asdfhjkla.

I got it to work, by creating my own style as you describe.
I have some experience with xml and I am a command line person
anyway, so just creating my own is fine. 

Still, for those that are not and don't want to edit an xml or
use another application such as gSchemer, you would think they 
would have left this functionality in there as it is so easy 
to "spin the dial" to the color you want, like it used to be.

At any rate, thanks for helping me figure out how to work around
the missing functionality and getting the color style that I like.

Ciao! 
/dater

---

