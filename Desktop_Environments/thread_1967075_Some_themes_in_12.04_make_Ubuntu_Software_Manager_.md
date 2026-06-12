---
title: "Some themes in 12.04 make Ubuntu Software Manager hard to see."
date: 2012-04-27
forum: Desktop Environments
---

### Post by marzzbar on 2012-04-27
Basically, this is my problem:
[IMG]http://i152.photobucket.com/albums/s197/marzzbar/SoftwareCentreInversion.png[/IMG]

The Software Manager is hard to see when I use the Albatross theme in xubuntu, though it also happens in the Low Contrast theme, and possibly others.

I suspect it's something to do with GTK-3, which was introduced in 12.04 (I think). I'm guessing I can edit the theme, but I have no idea what to edit. 

At the moment I'm using a different theme, but I really like Albatross :(. If anyone can tell me how to fix this, I'd be grateful :)

---

### Post by Kodeine on 2012-04-27
I just made a topic on the same thing. Only for me it happens for more than just the software centre.

---

### Post by marzzbar on 2012-04-27
So you did! Sorry for posting the same problem again, wasn't sure what to search for ><. 

I guess it's encouraging to see that it occurs on different desktop environments, and also that I'm not the only one with this problem. I still reckon it's something to do with GTK3, but I'm no 'buntu pro, yo.

---

### Post by marzzbar on 2012-04-27
I found a quick fix. As I suspected, I think it's something to do with the GTK3 theme, so I went into /usr/share/themes/Albatross/gtk-3.0 and then renamed all the files in there. Now Software Centre looks normal again, and I can keep the Albatross theme :D

---

### Post by bogan on 2012-04-28
Hi! **marzzbar**,

My upgrade to 12.04 had a similar but much more extreme display fault than your screen shot shows: See:
[http://ubuntuforums.org/showthread.php?t=1966094](http://ubuntuforums.org/showthread.php?t=1966094)

>  "Re:[B]Text invisible, white on white: 12.04LTS upgrade unuseable"
[/B]Answering my own query: I added the tualatrix ppa and installed Ubuntu-Tweak v7.0.

Altering the Gtk theme to 'Radiance' and the Window theme to 'Dust  Sand', gave me a good compromise between visibility and contrast.

Result: Problem Solved !!If you download Ubuntu Tweak from the tualatrix ppa you can set the GTK and windows themes separately.
```
Sudo apt-add-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```[B]Edit: You can also do the same thing in Dash>Advanced Settings>Theme.
[/B]
 Chao!** bogan**.

---

### Post by marzzbar on 2012-04-28
Oh cool, I'll give that a go sometime. Thanks!

---

### Post by teacosy on 2012-05-01
> **marzzbar said:**
> I found a quick fix. As I suspected, I think it's something to do with the GTK3 theme, so I went into /usr/share/themes/Albatross/gtk-3.0 and then renamed all the files in there. Now Software Centre looks normal again, and I can keep the Albatross theme :D

Hi marzzbar, 
what did you rename the files to?
thanks

---

### Post by marzzbar on 2012-05-02
Oh, I just renamed them to the same thing, but with BACKUP on the end. The idea is that the Operating System can't recongise what they are. I guess you could just delete the folder, but it's always safer to have backups :)

I tried that Ubuntu Tweak thing, it didn't do anything :(. Maybe it's just for Ubuntu and not xubuntu? :(

---

### Post by teacosy on 2012-05-02
ah thanks marzzbar... i gussed that and changed gtk-3.0 to gtk-3.0_... 
works, sort of... a bit of a hack... seems to revert to a default style... some elements are completely black though..

here is another thread on the issue im tracking: 

[http://forum.xfce.org/viewtopic.php?pid=26066](http://forum.xfce.org/viewtopic.php?pid=26066)

---

### Post by teacosy on 2012-05-02
i tried ubuntujeev's fix from the above link and it is better... still having the issue with the Ambiance & Radiance for Xfce/LXDE themes though...

---

### Post by marzzbar on 2012-05-04
Found yet another way to fix this. 

[http://binbashblog.blogspot.com.au/2011/10/manually-change-gtk3-theme-in-xubuntu.html](http://binbashblog.blogspot.com.au/2011/10/manually-change-gtk3-theme-in-xubuntu.html)

I did exactly what it said to activate the greybird theme. It doesn't look as consistent with the Albatross theme, but it looks better than the default :)

---

### Post by sadmanu on 2012-05-07
Have you seen this [https://bugs.launchpad.net/ubuntu/+source/shimmer-themes/+bug/989814]("https://bugs.launchpad.net/ubuntu/+source/shimmer-themes/+bug/989814")? A little fix for the xubuntu Albatross theme. The patch file worked well for me.

---

### Post by marzzbar on 2012-05-08
Awesome. That's probably the best solution I think. Works well for me as well!

I'm going to tweak the scrollbars to make them dark grey, and then all will be perfect :D

---

### Post by marzzbar on 2012-05-08
In case you find the link above to be too long, here's the link to the gtk-3 theme info. 

[http://ubuntuforums.org/attachment.php?attachmentid=216911&d=1335756601](http://ubuntuforums.org/attachment.php?attachmentid=216911&d=1335756601)

Just put that in /usr/share/themes/Albatross/gtk-3.0/. You'll probably need to sudo to do it.

---

### Post by simontaylor on 2012-05-21
thanks, that worked for me as well - a newcomer to Xubuntu scared off Ubuntu by Unity - I added the gtk-widgets.css to a leafpad call-up and cut and pasted from the extracted file...

It has however had the unforeseen consequence of turning my connection icon grey in a white box where it had previously been consistent with the theme: grey on black toolbar, no box.

If anybody knows what's up with that, please let me know!

Best,

Simon

[www.squarewhiteworld.com](www.squarewhiteworld.com)

---

### Post by marzzbar on 2012-05-22
Hmmm...that's not happened for me. Do you mean the connection icon in the system tray? Could you show a screenshot? What Icon theme are you using? (Applications Menu -> Settings -> Settings Manager -> Appearance -> Icons tab). I'm using elementary Xubuntu dark. Maybe try playing around with those?

---

### Post by simontaylor on 2012-05-22
hey Marzzbar,
elementary Xfce dark. attached please find screenshot. hard to see. upper right hand corner. but a little annoying I think you'll agree.

thanks for the interest, and I can confirm that I have tried other icon themes to no avail,

best,

Simon

---

### Post by marzzbar on 2012-05-23
That's really strange...just tried to reproduce it on my machine, tried different icon themes but no dice...

---

### Post by simontaylor on 2012-05-23
not a biggie, as these things go. All notification icons - crash / update / etc - do the same inversion. I'm guessing it has to do with the reversal of the colour values for system windows... but then if you aren't seeing it...?

Best,

Simon

---

