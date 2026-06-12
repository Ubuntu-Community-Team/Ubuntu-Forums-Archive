---
title: "Icon uniformity"
date: 2008-04-21
forum: Desktop Environments
---

### Post by Romanus81 on 2008-04-21
This is the one thing that has always bothered me about Gnome: Icons are usually of different sizes and unevenly distributed around the desktop. I still boot into windows from time to time and I always think the desktop looks much tidier. Sometimes I'll pop a CD into my PC and the icon on the desktop will be hiding behind another one. Is there a way to make all the icons on the desktop a uniform size and placed on a strict grid, so as to not cause overlap between them?

---

### Post by Vadi on 2008-04-21
Right-click on desktop and "Keep Aligned"? As for size, right-click on an icon and stretch size.

---

### Post by Romanus81 on 2008-04-22
There has to be a better way to maintain size uniformity than by eye, isn't there some setting in gnome I can use?

---

### Post by Vadi on 2008-04-22
I don't know what you mean, because all icons have always been uniform for me unless I stretched them :(

Some apps that create icons on the desktop do make their icon sizes different. But then again, no "native-native" linux apps are supposed to do that - they all should go into the Applications menu. (At least, that's what all so, exept ones like PlaneShift and Google Eearth (their installer)).

---

### Post by fyo on 2008-04-23
> **Vadi said:**
> I don't know what you mean, because all icons have always been uniform for me unless I stretched them :(

That certainly hasn't been the case for me. I've never stretched or otherwise resized an icon, yet they're all different sizes.

Icons for images are quite large, compared with the small "unknown" icons, which appear to match the "drive" icon. For some reason jpg's are slightly larger than png's, which are slightly larger than gif's.

pdf's are large as well.

---

### Post by KOTAPAKA on 2008-04-23
I know what you mean. It is driving me nuts. Especially when I have HDD with 8 partitions and when I mount them I have to move most of my icons to find them. I would also like to know a solution. Although the only one I can think of is to disable thumbnail view. (gnome-control-center -> file manager -> preview.
Here is an example of icons behind other icons:
[[IMG]http://img514.imageshack.us/img514/6790/screenshot1xu0.th.png[/IMG]](http://img514.imageshack.us/my.php?image=screenshot1xu0.png)

---

### Post by fyo on 2008-04-23
OK, so I decided to quickly test things. It seems the dimension of image icons depends on their dimensions. Some additionally have a border around them (jpg and png in my example below), while some do not (gif and xcf below):

[IMG]http://i57.photobucket.com/albums/g221/fyodor_/Screenshot.png[/IMG]

It's completely messed up.

---

### Post by Vadi on 2008-04-23
... oh.

To tell the truth I think that's perfectly normal that the icons reflect their "true" sizes. I'd be very confusing if everything was a box and things were squished/stretched to fit into the given box.

---

### Post by fyo on 2008-04-24
> **Vadi said:**
> ... oh.

To tell the truth I think that's perfectly normal that the icons reflect their "true" sizes. I'd be very confusing if everything was a box and things were squished/stretched to fit into the given box.

While it may be "perfectly normal", it's also **perfectly stupid**. I can, to some extent, understand that an icon would have the same ASPECT RATIO as its content, but all icons should still have the same width... and they don't. That's a huge mistake and a good part of why it's ugly.

As for the aspect ratio thing... why should adding a preview be allowed to mess things up? I agree that stretching the content to get a uniform aspect ratio is not a good solution, but why not render it with "transparent bars" around? (left and right or up and down, depending on content aspect ratio).

That would allow for uniform icon sizes, previews and preservation of aspect ratios in the previews.

Regardless, the way it's done now is amazingly stupid. At the very, very least, icons should have the same width. They don't. pdfs, images and "standard icons" (like "drive" or unkown type) all have different default widths, regardless of the aspect ratio of their content. That's **monumentally stupid**.

---

### Post by Vadi on 2008-04-24
Take it up with the Gnome HIG developers then. You two are the only people who I've seen complain about this though.

---

### Post by fyo on 2008-04-24
> **Vadi said:**
> Take it up with the Gnome HIG developers then. You two are the only people who I've seen complain about this though.

I've been silently annoyed for years and by the sound of his original post, Romanus has felt this way for quite some time without sounding off as well.

Ahh, well, maybe it's time to check what the KDE guys have done.

---

### Post by ddado on 2008-04-24
A bing thanx to romanus, fyo and kotapaka for "outing themselves" on this matter... I switched from WinXP to Ubuntu just a couple of months ago and unequal icon size is one of the rare things that annoy me on the gnome desktop... now i dont know if and how kde has dealt with this issue, but i hope somebody from the developer team will do something about it soon! ;-)

---

### Post by kaylus on 2008-04-25
Everyone:

There are two easy solutions that I know of, the one that works best for me is #1, I'm not sure how it will work for you.

1. Run **gconf-editor** (you can install through synaptic) and then go to "/apps/nautilus/icon_view/" and modify "thumbnail_size" to 36, 48, or whatever your desktop icons are normally. This will make the icons preview not extend past that. The default is 96 which puts the preview at twice (or more) the size of normal icons. You will still have problems that the icons aren't put in imaginary 48x48 (or 36x36) boxes, but they will look much more uniform.

2. The other thing (and the what some people prefer, I don't) is to do what someone said previously, open up Nautilus file browser (try Places->Home) and then go to Edit Menu->Preferences. On the "Preview" tab, in "Other Previewable Files", change "Show Thumbnails" to "Never" -- this will add SOME uniformity until a better way is found.

This has been brought up before and by many people that I know. A simple search of ubuntu forums finds gnome icon size has been asked a few times. I've worked in companies that use linux distros in a production environment and I would rank this kind of issue in the top 10 of User Interface Help request issues.

People don't like the cluttered look, it's a natural tendency. Nautilus icons are different sizes, show up at all locations, appearing in front of other icons when mounting, etc. People then complain that they have no control over the consistency of items on a large scope (not individual scope)

**As to icon overlapping when mounting new hardware:** You may see a fix if you upgrade to 8.04, but I can't confirm. I know that there was a patch to fix that EXACT bug out a while back for Nautilus 2.22. Ubuntu 7.10 Nautilus is 2.20, and I do believe 8.04 is 2.22 so might be patched -- Cheers!

[QUOTE=vadi]Take it up with the Gnome HIG developers then. You two are the only people who I've seen complain about this though.[/QUOTE]

What a genuinely unhelpful answer, Vadi. Thank you for taking the time out to add nothing but a response in the same attitude that's driven people away from linux for years. The person was asking how to accomplish something. Generally stating to take it up with gnome developers is both unhelpful and False. The desktop being used on Ubuntu is generated through Nautilus, Gnome developers wouldn't help. RTM.

Kaylus

---

### Post by mobusby on 2008-06-28
You have to bring the setting in gconf-editor down from 96 to 30 before PDF preview icons no long disrupt the normal layout in nautilus.

---

### Post by US41 on 2008-11-22
> **Vadi said:**
> Take it up with the Gnome HIG developers then. You two are the only people who I've seen complain about this though.

This answer is an example of what chases so many users away from Linux.

I think the multi-sized icons scattered about in folders and on the desktop is stupid looking too.

I saw the post about the g-conf editor. The fact that you have to download a program in order to do something that even Windows offers in the way of default configuration availability is NOT ACCEPTABLE for widespread Linux adoption.

The configuration settings for default icon size must be made available in the default Ubuntu distribution. If G-Conf is too complex for a typical end user, then build a preferences applet to front it.

---

### Post by ddado on 2008-11-22
Hmmm...

I agree with US41 - And I would add the "align to grid" option as well, which is missing (at least in my case, on Gutsy).

Thumbnails of picture files and .pdf files are a nice thing - if one wants them or if one has a specific folder where all of the data are then same size... but i don't think they should be set as default. it looks really messy on the desktop.

---

