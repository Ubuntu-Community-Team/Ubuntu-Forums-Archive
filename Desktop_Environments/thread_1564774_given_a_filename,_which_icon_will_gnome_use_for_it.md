---
title: "given a filename, which icon will gnome use for it?"
date: 2010-08-31
forum: Desktop Environments
---

### Post by weblordpepe on 2010-08-31
Hi there fellow Ubuntu soldiers!

I have a need in my scripts I am currently working on. I need a way to display the correct icon for a given file.

Does anyone know of a way (any way) which I could be told the icon used by gnome (eg, /usr/share/icons/something/something.png) for a particular file? There are ways to get details about a file using the 'file' utility, but how to get the icon for that type of file etc is unknown. Personally I don't think Gnome even touches the 'file' utility since it can't tell anything without the correct extensions.

I have tried all kinds of things, investigating MIME & stuff and GTK themes but I can't seem to come to any proper conclusion since I'm a bit of a noob.

I understand I could possibly need to hook into Gnome APIs some how. Can anybody help me with this? I have two chocolate bars and a girlfriend for trade.

---

### Post by BrandyBear on 2010-08-31
Im confused what do you mean which tells me.......I really dont get your thread:confused::(

---

### Post by psavva on 2010-08-31
> **weblordpepe said:**
> Hi there fellow Ubuntu soldiers!

I have a need in my scripts I am currently working on. I need a way to display the correct icon for a given file.

Does anyone know of a way (any way) which I could be told the icon used by gnome (eg, /usr/share/icons/something/something.png) for a particular file? There are ways to get details about a file using the 'file' utility, but how to get the icon for that type of file etc is unknown. Personally I don't think Gnome even touches the 'file' utility since it can't tell anything without the correct extensions.

I have tried all kinds of things, investigating MIME & stuff and GTK themes but I can't seem to come to any proper conclusion since I'm a bit of a noob.

I understand I could possibly need to hook into Gnome APIs some how. Can anybody help me with this? I have two chocolate bars and a girlfriend for trade.



Pretty much all of the instructions/How-to's on Gnome icons stated that the icon filename, in a theme, needed to be set up like this:


```
gnome-mime-video-x-msvideo.png 
```(this example is using the mimetype for files with an .AVI extension)
where "gnome" is your desktop manager, "mime" refers to a mimetype, "video" tells us the type of mime and "msvideo" is the specific mime type that the icon will be applied to.

Now, what I've found is that gnome (gnome 2.16, at least) automaticaly points all the icons at "gnome-mime", when you add a new icon theme, or revise one, as was my case. So to get my icons to display with the appropriate filetype, they had to be named as follows:


```
video-x-msvideo.png (the "gnome-mime" is no longer necessary)
```


Also, it might be usefull to know that you can get a list of mimetypes from your ```
/etc/mime.types
``` file. Also, if you want to know a specific files mime type, you can right click the file, select properties, and the mimetype will be displayed, for that file, under the basic tab.

Taken from
[http://mandrivausers.org/index.php?/topic/38906-easy-icon-association-in-gnome-solved/](http://mandrivausers.org/index.php?/topic/38906-easy-icon-association-in-gnome-solved/)

---

### Post by weblordpepe on 2010-08-31
Thanks heaps psavva. You're the boss.

---

### Post by weblordpepe on 2010-08-31
Just read through. This information seems to deal with specifying which icon you would -like to use- for a file. Basically I want to do the reverse. I have the file, and I would like gnome to tell me which icon it is currently using for it.

---

### Post by DavidOfLondon on 2010-08-31
Hi,

"I have the file, and I would like gnome to tell me which icon it is currently using for it."

Saying WHY you want that is important in order to get a good answer because it'll determine the form of answer you get.

If you just want file knowledge you're gonna get a how to on gedit. If you want to know how it's done in order to add to your own script you'll get a different answer.

The more specific your post the more specific the answer you'll get. It's a very specified question you're asking and you'll likely only get the answer you're after from someone who has the same need as you...and I've never heard someone ask this question beforre.

I'd edit your original post and make it more detailed.

Best,

D.

---

### Post by weblordpepe on 2010-09-02
> **DavidOfLondon said:**
> Hi,

"I have the file, and I would like gnome to tell me which icon it is currently using for it."

Saying WHY you want that is important in order to get a good answer because it'll determine the form of answer you get.

If you just want file knowledge you're gonna get a how to on gedit. If you want to know how it's done in order to add to your own script you'll get a different answer.

The more specific your post the more specific the answer you'll get. It's a very specified question you're asking and you'll likely only get the answer you're after from someone who has the same need as you...and I've never heard someone ask this question beforre.

I'd edit your original post and make it more detailed.

Best,

D.

I think its pretty obvious. Here is a file URL:
/home/twit/something/file.jpg
or

/usr/share/local/something.txt

What is the URL for the file icon which gnome uses to display it in Nautilus, the desktop, etc?

There are a lot of icons under /usr/share/icons and /usr/share/pixmaps etc etc etc
I want to know which one of those icons Gnome is choosing for the file icon in nautilus/desktop.

Why I want this information is kinda besides the point. I obviously want to fetch the icon so I can present it in a way which gives with the user's icon theme.

How much further should I reword it? Do you need puppets?

---

