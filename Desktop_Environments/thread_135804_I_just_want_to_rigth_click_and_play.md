---
title: "I just want to rigth click and play"
date: 2006-02-24
forum: Desktop Environments
---

### Post by thnogueira on 2006-02-24
Yes, I miss this so simple and powerfull feature in nautilus. I want to right click any folder and play whatever music files it has in there; including subfolders, of course.
Am I missing something? Don't you miss that?

PS - No, I don't want these music organizers. Just want the simple, fast and easy...\\:D/

---

### Post by Stormy Eyes on 2006-02-24
I can write a script that will provide that functionality tonight if you want.

---

### Post by thnogueira on 2006-02-24
I'd really appreciate that. Is it possible to integrate with nautilus?

Thank you very much!
Thiago.

---

### Post by Stormy Eyes on 2006-02-24
[QUOTE=thnogueira]I'd really appreciate that. Is it possible to integrate with nautilus?

Thank you very much!
Thiago.[/QUOTE]

Nautilus includes the ability to extend it by writing scripts. I'll explain more later.

---

### Post by thnogueira on 2006-03-08
I still waiting for...

---

### Post by kaamos on 2006-03-08
Also there is a program to extend nautilus functionality called "nautilus actions". You might want to look at that. Probably this functionality won't be in, but it should be pretty simple to add the command.

---

### Post by thnogueira on 2006-03-09
Thanks kaamos,
i'm gonna take a look

---

### Post by jasay on 2006-03-12
Nothing fancy, but this seems to work for me with xmms:```
#!/bin/bash
xmms $NAUTILUS_SCRIPT_SELECTED_URIS

``` save it to ~/.gnome2/nautilus-scripts with a descriptive file name like play_media_with_xmms  Then make it executable with ```
chmod +x play_media_with_xmms
```  Now you should be able to right click on a folder/file and select scripts > play_media_with_xmms

The script above will always clear the playlist before adding the file/folder.  If you want to append files to the playlist you might use
```
#!/bin/bash
xmms -e $NAUTILUS_SCRIPT_SELECTED_URIS

``` Unfortunately this won't start the music playing, only que up the songs at the end of the list.  

If you prefer bmp you can just substitute "beep-media-player" for "xmms" above.

I haven't yet figured out how to use rhythmbox from the commandline so I'm not sure how to script it.

Anyway, that might get you started until someone smarter than me writes something better.

---

### Post by WildTangent on 2006-03-12
Sweet, I've been after this functionality for a while. Thanks for the script :D

-Wild

---

