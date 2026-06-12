---
title: "How can I change my default video player?"
date: 2006-10-03
forum: Desktop Environments
---

### Post by NJCarrier on 2006-10-03
Whenever I open a video or audio file it defaults to Totem Movie Player. Not only do I not like the program, but it won't play very many files. If I put a DVD in my computer, it pops open Totem. Lots of links on the internet open up in Totem. How can I change my default player? I would much more prefer to have a player like MPlayer Movie Player. It would be even better if I could specify which files to open with what programs. How could I go about doing this? Thanks for any help,
Nate

---

### Post by Rui Pais on 2006-10-03
> **NJCarrier said:**
> ... 
 It would be even better if I could specify which files to open with what programs. How could I go about doing this? Thanks for any help,
Nate

Open nautilus, right click on file you which to change default app, choose 'Properties' from the menu. 
Go to the tab called 'Open With' and choose the default you prefer or Add a new app if the preferred app is not listed.

---

### Post by NJCarrier on 2006-10-03
Thanks, that has helped. What about when I put a DVD in? It automatically pops up Totem. When you right click on the DVD it doesn't have an option to allow for changing the program. Thanks for the help,
Nate

---

### Post by konst88 on 2006-10-03
go to:
system>preferences>removable drives>multimedia>DVD
put there the name of the program you like.
good luck!

---

### Post by Rui Pais on 2006-10-03
Try gnome-volume-properties
(Menu -> Settings -> Removable Drives and media)
and go to Tab 'Multimedia' 

Change to your desired videoplayer :)

---

### Post by NJCarrier on 2006-10-04
Everythings a lot better now, except for one problem. When there is a video integrated into firefox it still uses Totem, and for some reason, my Totem doesn't support all the same video formats/codecs as my other players. I can't recall what site I was at, but it had a link to watch the video for a PC user, and one for a Mac user. The PC one used WMP and the Mac used Quicktime. My other video players can play those formats. How can I change it to use a different video player? Thanks so much:),
Nathan Carrier

---

### Post by konst88 on 2006-10-04
not all players have a plugin for FF.
search the palyer name in synaptic, and try to find something which conected to FF.
you can also remove from synaptic totem's plugin.

---

### Post by Delkster on 2006-10-04
> **NJCarrier said:**
> Not only do I not like the program, but it won't play very many files.

Just for the record, in my experience Totem with the Xine player engine still has better compatibility with different formats and codecs than Totem using the Gstreamer framework.

If you install the totem-xine package (you can find that in Synaptic by that name, but you need the universe repository enabled), and with the xine-extracodecs package installed (you need multiverse for that as some of the formats or codecs are patent-encumbered) the Xine-based player should show almost everything you throw at it (save for WMV 8/9 and RealMedia, which probably still need the corresponding Windows codecs in Dapper).

---

### Post by NJCarrier on 2006-10-05
Thanks. I added the two libraries titled libxine1c2 and libxine-extracodecs. Well know that totem plays DVDs I decided I like it better for DVDs. How ironic. Well I went to System>Preferences>Removable Drives and Media and switched it to "totem." Just one problem. I think when I changed it from totem it had some commands or something after it. When I just do totem it only brings up the program when I insert a DVD. It doesn't start playing. How can I make it autoplay? Thanks,
Nate

---

### Post by Rui Pais on 2006-10-05
> **NJCarrier said:**
> ... I think when I changed it from totem it had some commands or something after it. When I just do totem it only brings up the program when I insert a DVD. It doesn't start playing. How can I make it autoplay? Thanks,
Nate

totem %m

---

