---
title: "XGL/Compiz install went fine, but how do I..."
date: 2006-08-24
forum: Desktop Environments
---

### Post by tribaal on 2006-08-24
Hi folks:

How do I do the following in XGL/Compiz?

1. Assign Ctrl-F1 / F2 / F3 / F4 to switch to workspace 1,2,3 and 4?
2. Rotate the cube with my mouse (probably while holding down one of my mouse buttons).
3. Make the window animations disappear (when I drag a window, it's default behavior makes me sea-sick). I managed to get tid of this effect on the menus somehow (with gconf-editor), but i couldn't find how to get rid of the wibble for the windows... :(

Is there like a master configuration panel somewhere I missed? Thanks a lot folks! ](*,) 

- trib'

---

### Post by h00s on 2006-08-24
1. I don't know. Maybe set it somewhere in gconf-editor?

2. Hold ctrl+alt + left mouse button
or
go to the left or right edge of screen and scroll mouse

3. open gconf-editor
go to apps -> compiz -> general -> allscreens -> options -> active_plugins.
Remove wobble for plugins list.
Caution: this will remove completly wobble effect.

---

### Post by tribaal on 2006-08-24
Thanks a lot!

This plugin really was making me feel sick. :)
Thanks for the mouse-controlled rotation of the cube, too, it's pretty neat. No wonder it helps people convert others to linux... I't really a nice toy :)

Now if I could only find out how to assign theses hotkeys... ;)

- trib'

---

### Post by tribaal on 2006-08-24
Actually I answered my own question...

So for the record, to set shortcuts to "switch" directly to a particular workspace, you need to launch gconf-editor, and go:
Apps > Compiz > Plugins > Rotate > Allscreens > Options

There in the list you have a "Rotate_to_#_key" field (where # is the screen number).
In my case, filling in the field with "<Control>F#" worked wonders.

Thanks again h00s

- trib'

---

### Post by h00s on 2006-08-24
You're welcome.
I'm glad I could help :)

---

### Post by LeftyAce on 2006-08-24
Hi! I'm in the opposite situation of tribaal; I want to add the water effect.  For some reason, when I add "water" to the list of active_plugins, when I close gconf-editor it disappears again.  And the water effect doesn't work.  Can either of you help me make my edit to active_plugins "stick"?

Thanks!

---

### Post by h00s on 2006-08-24
First make sure that you have installed water plugin. 
(Go to gconf-editor, apps -> compiz -> plugins, water plugin must be in list if installed.)

Then, if installed, add it to active_plugins with this order:
gconf, decoration, transset, wobbly, fade, minimize, cube, rotate, zoom, scale, move, resize, place, switcher, trailfocus, water (from top to bottom order).

I have not try this 'water' plugin because of my low spec computer and because it's reported that it uses intense CPU resources, and crashes X. :neutral:

---

### Post by LeftyAce on 2006-08-24
Ah.  I didn't realize that some plugins weren't installed by default; I thought that some were just disabled.  
Thanks for the suggestion;  I'll investigate when I get home from work.  If it's not installed, how do I install it? (fyi my compiz install was from binary .deb's.  not sure if that matters).

I want to give water a try even though many people say it's very intensive; I built my comp for gaming under windows, and figure that in todays eye-candy worshiping world, compiz makes for a great linux advertisement :-)
(And I'll admit, I fall for the eye candy too).

Cheers,

Lefty

---

### Post by h00s on 2006-08-24
> **LeftyAce said:**
> If it's not installed, how do I install it? (fyi my compiz install was from binary .deb's.  not sure if that matters).
I'm not quite sure if i'm correct, but if you modify your /etc/apt/sources.list and add compiz package list, it should be updated with latest version and with all plugins. Again, i'm not sure of this.

If you want to try it, do this:
edit /etc/apt/sources.list and add this lines to it:
```

deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
```

After that done,
```

sudo apt-get update
sudo apt-get upgrade
```

And after that done, you should have installed latest compiz plugins, cgwd etc.

> **LeftyAce said:**
> (And I'll admit, I fall for the eye candy too).


Me too, I just love it, but also I find cube, switcher and several other plugins very useful too\\:D/

---

### Post by stoeptegel on 2006-08-24
So the wobbly can be easily disabled... hmm, i was getting irritated by it too, i should have known earlier. ++ for the topic
EDIT
compiz.real doesn't seem to like it without wobbly (high cpu and desktop stalled after a while)

---

### Post by h00s on 2006-08-24
Here's another tip on this topic.

Actually, I like wobble effect but only when I grab and move window, not that ridiculous effect when you maximize open window.
So, I turned off maximize-wobble :mrgreen:

Here's how:
In gconf-editor go to:
apps -> compiz -> plugins -> wobbly -> screen0 -> options
and uncheck maximize_effect.

And another tip:
if you experiencing high memory usage with no wobble plugin running, try add it back to plugins list (after decoration and before fade plugin) and then uncheck maximize_effect as well as wobble_on_move.

---

### Post by LeftyAce on 2006-08-25
Thanks for the info thus far, but unfortunately I'm back for more guidance!

I added the necessary lines to sources.list, and ran the update/upgrade.  More packages were installed, but I still don't see water listed under plugins, and of course it still doesn't stick when I add it to active_plugins.  Can I manually dowload plugins? I looked at beerorkid.com and didn't see anything...

Sorry for my lack of knowledge in these things; still learning the ropes of this compiz stuff :-)

---

### Post by LeftyAce on 2006-08-25
.

---

### Post by h00s on 2006-08-25
This is a tough one :-?
I don't know how to install only water plugin.

BUT, after some searching forum, it looks like you have installed water plugin but it's shema is not imported into gconf-editor. Search [www.compiz.net](www.compiz.net) regarding this topic.

---

### Post by LeftyAce on 2006-08-25
Thanks again for the help.  I found a link on compiz.net to download the schemas file.  That gave me "water" listed under plugins, and I am now able to set water in active_plugins. 

Trouble is, when I try to log in to the compiz session, it gives me a blue screen (a soft blue screen) and a mouse pointer, and that's it.  It hangs with no HDD access and just sits there.  I've removed water from active_plugins, but that doesn't help.  

Any suggestions?  I heard that the order of plugins in active_plugins is important, but what I've read has water last, which is what I did.

Thanks again for ur help so far,

Lefty

---

### Post by h00s on 2006-08-25
Yep, the right order is critical.
This is correct order:
```
gconf, decoration, transset, wobbly, fade, minimize, cube, rotate, zoom, scale, move, resize, place, switcher, trailfocus, water
```
Try rearrange your plugin order according to this list (but without water plugin!) to get your xgl session working again, and then if it's working, try adding water plugin.
I hope this gonna work :rolleyes:

---

### Post by LeftyAce on 2006-08-26
I tried the changing the order, but with no luck.  I'm beginning to wonder if the schemas file I downloaded from compiz.net might have been the wrong one?  I've unfortunately not got alot of time to play with it this weekend, but I think what I'll do when I get the chance is re install compiz from cvs (instead of the .deb installation I did for this one).  Perhaps updates aren't working right because of whatever's really in the .debs (and how old they are).  
Thanks for your help h00s; you got me much further than I would have figured out myself, and I'll refer back to your instructions after I've got a fresh compiz install working.  

Cheers,

Lefty.

---

### Post by h00s on 2006-08-26
I'm sorry that my instructions didn't help much, but the fresh install from cvs would be best solution and would solve all issues I think...

And no problem, if you gonna have more question I will be willing to help you!

Take care,
h00s

---

### Post by LeftyAce on 2006-08-27
Ok, I re-installed Ubuntu just in case (didn't have anything important on the partition anyway).  and re-installed Compiz by the same method I had used before, because compiling MEsa gave me errors, and the posts I found while searching asking for help on the subject said "why didn't u just install the binaries?"

So I got to the same point as before, and it seems that installing the schemas file is what breaks things.  I downloaded a schemas file from a post on compiz.net 

How can I remove the schemas file? I installed it with gconftool-2.

If I can roll the schemas file back, or learn how to get one that works for my setup, I can continue working on the water problem.

Thanks again,

Lefty.

---

