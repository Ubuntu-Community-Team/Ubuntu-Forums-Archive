---
title: "Fullscreen VLC"
date: 2007-07-31
forum: Desktop Effects &amp; Customization
---

### Post by chessercizes on 2007-07-31
hey everyone.

ok so recently i installed compiz fusion (its so cool!!), but whenever i fullscreen VLC, the video is partly transparent. I read around on the forums, and i changed the option in CCSM - General Options - Opacity, and made it 100. This solved the vlc problem, but now the dropdown menus and stuff arent transparent anymore.
Does anyone know of a way to keep these transparent while getting vlc  to be not transparent?


Thank you very much.

-chessercizes

oh, and i hope this was the right place to post this.

---

### Post by 505 on 2007-07-31
Try using different video methods in VLC. See settings, Preferences, Video, Output modules. You can also try the alternate fullscreen method for the output module you've selected (under 'Output modules', each corresponding module's setting). Try to play with it and see if it makes any difference. Note that you must restart the video each time you change such a setting.

---

### Post by Death &amp; Taxes on 2007-07-31
Remove "unkown" from the "window opacity" list

---

### Post by chessercizes on 2007-07-31
hey.
thanks for the reply =)

i messed around with it, and tried out the different options, but none of them worked.

when i go to ccsm - general options - opacity this is what it says
```
((type=Menu | PopupMenu | DropdownMenu | Tooltip | Notification | Combo | Dnd | name=sun-awt-X11-XWindowPeer) | (type=Normal & override_redirect=1)) & !(name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer)
```
and the value is 89.

from what i understand, everything after the "!" is supposed to be like the exceptions right? so would it be possible to add vlc to that list? 

thanks for the help =)

---

### Post by deadlikeoscar on 2007-07-31
I have the same problem. I had this problem before and fixed it by deleting Unknown as was again suggested here but I'm pretty sure one of the recent updates broke it again. I had the problem with my pictures as well, so I added a line above all of that stuff a while back that said (name=eog) and set the transparency to 100 and it fixed the transparency when viewing photos. I tried adding vlc and wxvlc to it but I don't think those are right. I saw wxvlc listed in my processes but it doesn't seem to fix anything.

My current setting look like this:

```
 
(name=eog | name=wxvlc) <--Transparency set to 100
((type=Menu | PopupMenu | DropdownMenu | Tooltip | Notification | Combo | Dnd | name=sun-awt-X11-XWindowPeer) | (type=Normal & override_redirect=1)) & !(name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) <--Transparency set to default 89
```

---

### Post by kelly.seay on 2007-08-01
I am also having this problem.  Setting the opacity to 100 clears up the transparency issue, but i also still see my gnome panel on top and my AWN is on top of my video.

---

### Post by chessercizes on 2007-08-01
hey guys.

concerning your problem kelly.seay, open up vlc and go to Settings > Preferences.
Check the advanced options box in the bottom right corner.
Then click on Video > Output Modules. Change the Video output module from default to Xvideo extension video output. Then click where it says Xvideo under Output Modules. And then there, check the "alternate fullscreen method" box. This worked for me on getting the fullscreen on top of the panels and all. hope it helps.

Doing the 100% transparency worked for me too, but then dropdown windows and stuff arent transparent anymore. This isnt really a big deal though; i was just wondering if anyone had got it solved.

thanks for the help guys!

=)

---

### Post by SQuark on 2007-08-02
I found this and it worked! [[link]](http://ubuntuforums.org/showpost.php?p=2950430&postcount=4)
Just add the bold part (state=fullscreen). :)

---

### Post by tschneiter on 2007-08-04
In my fresh install, the original line was as follows:
```
((type=Menu | PopupMenu | DropdownMenu | Tooltip | Notification | Combo | Dnd | name=sun-awt-X11-XWindowPeer) | (type=Normal & override_redirect=1)) & !(name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer)
```

I found that the offending entry is 'DropdownMenu'. Removing that makes vlc work in fullscreen, but removes transparency from (duh) dropdown menus. Yield: 
```
((type=Menu | PopupMenu | Tooltip | Notification | Combo | Dnd | name=sun-awt-X11-XWindowPeer) | (type=Normal & override_redirect=1)) & !(name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer)
```

Oh, I dont know about that link SQuark gave. Its on a different server dressed up to look like the ubuntuforums.org server. Logging in does nothing besides (i assume) steal your password. If you tried to log on there, Id recommend changing your password.

---

### Post by satkata on 2007-08-04
> I found this and it worked! [link]
Just add the bold part (state=fullscreen).


That helped, thanks SQuark

beside **state=fullscreen**, I added also **name=vlc**

and of course I reverted the Video settings to **X11 Video Output** under Output Modules and **disabled the alternate method** under XVideo Section.

After doing this, you should be all set. :)


I deleted the state=fullscreen entry, left only name=vlc, and it still works fine, as I have just had some problems when playing slideshow to my photos in F-Spot 4.0

---

### Post by Lapino on 2007-08-04
Something I noticed with the latest compiz versions from Trevino's repository was that the state=fullscreen didn't work anymore for me. The solution, oddly enough, was to use emerald instead of metacity as window manager. So maybe some of you might try that out too.

---

### Post by SQuark on 2007-08-05
> **tschneiter said:**
> Oh, I dont know about that link SQuark gave. Its on a different server dressed up to look like the ubuntuforums.org server. Logging in does nothing besides (i assume) steal your password. If you tried to log on there, Id recommend changing your password.

I'm really sorry about that. :(  Thanks for catching it!
I found it linked like that in another thread on these forums and didn't doublecheck the URL. I changed the link now. I hope I haven't caused anyone trouble.

---

