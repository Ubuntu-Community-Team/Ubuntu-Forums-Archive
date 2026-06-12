---
title: "Autohide top bar in Gnome Shell 3.2?"
date: 2011-11-06
forum: Desktop Environments
---

### Post by volkerbradley on 2011-11-06
Is it possible to autohide the top bar in Gnome Shell 3.2 in Oneiric like one could in Natty?
I've not been able to find a way to do it.

---

### Post by cbowman57 on 2011-11-06
I can't remember where I saw it but someone claimed they had modified the autohide extension to work on 3.2. Unfortunately I don't remember where I read it, you might find it by doing an exhaustive search covering no more than a month back.

I don't think it was here in the forum, I think it might have been in one of the comments at Webupd8.

---

### Post by volkerbradley on 2011-11-06
I've searched Webupd8 and Google. Just can't seem to find an answer.

---

### Post by cbowman57 on 2011-11-06
Yeah, I just "stumbled" upon it, wish I could remember exactly where.

A lot of people liked that extension, I'm sure it will make a comeback.


*** Found it, look at the comments section here: [http://www.webupd8.org/2011/06/autohide-top-bar-gnome-shell-extension.html#comment-356318148](http://www.webupd8.org/2011/06/autohide-top-bar-gnome-shell-extension.html#comment-356318148)

---

### Post by Frogs Hair on 2011-11-06
The extension at the link has not been updated for Gnome 3.2 yet . :(
[http://www.webupd8.org/2011/06/autohide-top-bar-gnome-shell-extension.html](http://www.webupd8.org/2011/06/autohide-top-bar-gnome-shell-extension.html)

---

### Post by cbowman57 on 2011-11-06
The code is a jumbled mess in the comments box but somebody that is determined should be able to piece it together.

---

### Post by werewolves on 2011-11-06
I think this should work.  None of the code is mine, I just pulled it from the comment and cleaned up the formatting.

Just unzip it to:
~/.local/share/gnome-shell/extensions

Fair warning: from what I can tell this follows "bad practice" for converting Gnome 3.0 extensions to 3.2, but that basically means you can't really disable it from what I can tell (and I'm no expert).  I may try to do it the "right way" for experience at some point.

---

### Post by cbowman57 on 2011-11-06
@werewolves, this would be a great opportunity for you to engage Finn in a bit of discussion. :)

Tell him you sorta hacked this together & see if he wants to look at it & clean it up. He might appreciate the assist.

---

### Post by volkerbradley on 2011-11-07
That did it!!!
Thanks a lot for your tip.

---

### Post by werewolves on 2011-11-07
OK, here is a properly converted 3.2 version, meaning it will enable and disable as expected.  Also, instead of just statically setting the panel height to 25 pixels, this version reads the current panel height when it initializes (allows for different shell themes).

---

### Post by cbowman57 on 2011-11-07
Excellent job. :)

---

### Post by volkerbradley on 2011-11-08
Beautiful!!
Thank you.

---

### Post by asdjkl on 2011-11-08
I've created autohide extension with a slightly modified behavior. It overlays the window instead of forcing the maximized window to resize. It is more like Gnome 2 autohiding panels.

---

### Post by cbowman57 on 2011-11-08
They're both nice but I like the fact that this one doesn't resize the window.

Just noticed something though, you can't double-click this latest one & get it to stick.  Maybe some people don't find that necessary.

---

### Post by asdjkl on 2011-11-08
> **cbowman57 said:**
> They're both nice but I like the fact that this one doesn't resize the window.

Just noticed something though, you can't double-click this latest one & get it to stick.  Maybe some people don't find that necessary.

Double-click feature and the hiding animation is not implemented. It fits my needs and I don't want to spent more time on it. Feel free to adjust the code :)

Basically, this is the "window not resizing" code that can be added to other autohide extensions:

```
Main.layoutManager.removeChrome(Main.layoutManager.panelBox);
Main.layoutManager.addChrome(Main.layoutManager.panelBox, { affectsStruts: false });
```

---

### Post by cbowman57 on 2011-11-08
Cool, thanks.

After trying it on werewolves version it is an odd combination of behaviors, I can see why you left it out.

That being said, there are probably some users that will prefer it. :)

---

### Post by bmbaker on 2011-11-08
hmmm nice great job :-)
was looking for yesterday and i also couldn't find it :-)

---

### Post by vanlong441 on 2011-11-08
thank you very much for the scritps. I've been waiting for them.

---

### Post by werewolves on 2011-11-09
> **asdjkl said:**
> Basically, this is the "window not resizing" code that can be added to other autohide extensions:

```
Main.layoutManager.removeChrome(Main.layoutManager.panelBox);
Main.layoutManager.addChrome(Main.layoutManager.panelBox, { affectsStruts: false });
```

Code stolen and integrated ;)

Thank you

---

### Post by werewolves on 2011-11-11
FYI, my extension got uploaded to the WebUpd8 PPA

> 
sudo add-apt-repository ppa:webupd8team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell-extensions-autohidetopbar


---

### Post by jefflee on 2011-11-15
> **asdjkl said:**
> Double-click feature and the hiding animation is not implemented. It fits my needs and I don't want to spent more time on it. Feel free to adjust the code :)

Basically, this is the "window not resizing" code that can be added to other autohide extensions:

```
Main.layoutManager.removeChrome(Main.layoutManager.panelBox);
Main.layoutManager.addChrome(Main.layoutManager.panelBox, { affectsStruts: false });
```

=================================================
Thank you!
I added the two sentences into the original fpmurphy extension for gnome 3.0 but there seems no effect... the windows will still maximize when they reach the top of the screen.

I added them into "function main()" since it seems to be the initialization part. I have no Gnome extension experience so I'm not sure whether this is the correct place.

Thank you for your help :)
=================================================

SOLVED:
in gconf-editor, go to /desktop/gnome/shell/windows and unchecked the edge_tiling option. 
[http://www.fedoraforum.org/forum/showthread.php?t=259779&page=37](http://www.fedoraforum.org/forum/showthread.php?t=259779&page=37)

---

### Post by Perennialplants on 2011-11-15
hi to all i m new here plz giude me..


thanks

---

### Post by volkerbradley on 2011-11-15
> **Perennialplants said:**
> hi to all i m new here plz giude me..


thanks
In your browser go to [http://ubuntuforums.org/attachment.php?attachmentid=206635&d=1320725209](http://ubuntuforums.org/attachment.php?attachmentid=206635&d=1320725209) which will download [email]autohidetopbar2@werewolves.us.zip[/email]
Open the terminal and then do the following:
```

cd ~/your_browser's_download_directory
unzip autohidetopbar2@werewolves.us.zip
cp -r autohidetopbar2@werewolves.us/ ~/.local/share/gnome-shell/extensions 

```
Hold the Alt and the F2 keys down at the same time and for the command just type the letter r and then hit the Enter key
Now open the gnome-tweak-tool and click on Shell Extensions
Scroll down to autohidetopbar Extension 
Click on the button just to the left of the word OFF
This will turn the extension on.
Double-click on the top bar to make it autohide.

---

### Post by werewolves on 2011-11-15
> **Perennialplants said:**
> hi to all i m new here plz giude me..


thanks

There is a better version in the PPA now.  Just paste these lines into the terminal.
> 
sudo add-apt-repository ppa:webupd8team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell-extensions-autohidetopbar


Make sure you remove any older versions.

---

