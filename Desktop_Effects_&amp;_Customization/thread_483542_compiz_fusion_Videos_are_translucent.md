---
title: "compiz fusion: Videos are translucent"
date: 2007-06-24
forum: Desktop Effects &amp; Customization
---

### Post by kpkeerthi on 2007-06-24
I can see my desktop through video players while running compiz fusion. As you can see below, the desktop icons and firefox are partly visible through VLC... kind of intrusive to me. Is there any way I can disable it? Thanks.

---

### Post by llamakc on 2007-06-24
Yes. Change the video player's config options. I use xine and changed it to 'xshm'.

---

### Post by kpkeerthi on 2007-06-24
Thanks. But I  never had this problem when I used beryl. So I don't think its a player issue. I think its something in compiz fusion thats causing this. I'm trying to find some transparency settings in CompizConfig but I couldn't find anything that could help.

---

### Post by llamakc on 2007-06-24
You're wrong. If you are using compiz, you're not using Beryl. Make the change like I said. Or, search the forums for the answer to make the change like I said.

---

### Post by kpkeerthi on 2007-06-24
Never mind, I figured out. I used regex matcher plugin and set opacity to 100% for VLC.

---

### Post by Nossie on 2007-06-24
I'm seeing my ubuntu desktop through my OSX vnc connection...  is your problem just video or across the board? I'm sure I prolly just have some mis configured plugin but I cant find it!

also get it in gnome games... but I turn compiz off for wow.

I dont think changing the settings of each individual application is such a good idea ( no offence) :P

although I could be wrong!

---

### Post by steveneddy on 2007-06-24
If this happens, you can always, as a quick fix, hold down the Alt key and roll the middle mouse scroll wheel. This makes the focused window more or less transparent.

---

### Post by VirtualTiger on 2007-06-24
A was having a similar problem with the "Battle for Wesnoth" game being translucent.  I was able to fix it by removing the UNKNOWN attribute from the Opacity windows.

You can get there through: 

System\Preferences\CompizConfig Settings Manager

General Options

Opacity Settings Tab

Window Opacities

Hope this helps.

---

### Post by doldett on 2007-06-25
> **VirtualTiger said:**
> A was having a similar problem with the "Battle for Wesnoth" game being translucent.  I was able to fix it by removing the UNKNOWN attribute from the Opacity windows.

You can get there through: 

System\Preferences\CompizConfig Settings Manager

General Options

Opacity Settings Tab

Window Opacities

Hope this helps.

It fixes my problem with vlc. Many thanks :D

---

### Post by Nossie on 2007-06-25
fixed ty !! even my screensavers were translucent lol :D

ty again !!

---

### Post by VirtualTiger on 2007-06-25
Yea, after posting my fix, I noticed last night that my Screen Saver was also Translucent.  I had a good chuckle on that one, kind of defeats the purpose of a screen saver. I was going to see what I could do to fix that when I get home this evening.

If anyone has found a fix for the screen saver issue, I would appreciate it.

Thanks.

---

### Post by VirtualTiger on 2007-06-25
I've been playing around with the Translucent issues with the screen saver and found out how to use the opacity window logic.

There were a couple of methods to fix this.

Method 1 - I Didn't use because it could get messy, but I thought it was a good thing for others to know so they're aware of how the logic works.

Default Opacity windows Setting:
```
((type=Unknown | Menu | PopupMenu | DropdownMenu | Tooltip | Notification | Combo | Dnd | name=sun-awt-X11-XWindowPeer) | (type=Normal & override_redirect=1)) & !(name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer)    89
```

Modified Opacity Window Setting:
```
((type=Menu | PopupMenu | DropdownMenu | Tooltip | Notification | Combo | Dnd | name=sun-awt-X11-XWindowPeer) | (type=Normal & override_redirect=1)) & !(name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer | name=gnome-screensaver)    89
```
I removed "Unknown |" to further explain my fix from yesterday to get "Battle for Wesnoth" working for me.  And I added the "| name=gnome-screensaver" to the end of this line, this is inside of  a NOT condition, so it will be skipped, and the transparency will be ignored. 

 Basically, when reading the line:
```
| = OR
& = AND
! = NOT EQUAL
```

Method one works fine, but has a drawback in that if you're having problems with multiple programs, you could be adding additional programs to this line, making it difficult to read and follow.

Method 2:
Added another line to the opacity windows via the Add button.
```
(name=gnome-screensaver)    100
```
NOTE: Make sure this line comes before the default setting since once it meets a TRUE condition, it doesn't check the rest of the opacity window conditions.  Set the Opacity windows value to 100 to disable the transparancy for the condition.  

I could easily keep adding to this list of additional programs that I don't want to be transparent, for example:
```
(name=gnome-screensaver | name=wesnoth)
```

Attached Below is a screen shot .

---

### Post by Nossie on 2007-06-25
removing that original line on the last page stopped all the problems I was having with transparency... including the screensaver.

---

### Post by deadlikeoscar on 2007-06-25
Thank you for your fix. I added eog to the list to stop the translucency on my pictures when I viewed them full screen.;)

---

### Post by Nossie on 2007-06-25
> **Nossie said:**
> removing that original line on the last page stopped all the problems I was having with transparency... including the screensaver.

alas no... the screensaver works fine but most games are still transparent :-|

I guess I'll just put up with it till its fixed... I'm sure there must be an easier way than excluding every application I use :-\

ty for the info tho!

---

### Post by Olric86 on 2007-06-29
I've a little problem ... If I add something or change some value then it saves like binary code .... Can someone  help me ? 
I obtain the same thing if I use gconf-editor.

---

### Post by mid_night gypsy on 2007-06-29
Could any one tell me how to set up the start menu to be transparent in gnome? Thanks,gypsy

---

### Post by karlhm76 on 2007-06-29
I have the binary bug as well. Why is this so? I also can't remove the default opacity line, it just puts it back if I delete it.

With my problem, fullscreen videos are fine, the screensaver is transparent and many fullscreen openGL games, particularly those run through cedega are transparent.

---

### Post by michaelzap on 2007-06-29
Wow I love that alt-mouse wheel trick!

---

### Post by wooglin280 on 2007-06-30
I have the binary bug as well.  Does anybody have a fix for this?

---

### Post by karlhm76 on 2007-06-30
I haven't solved the binary bug, but I removed the "unknown" from the default opacity string as suggested by others. The string turned into the square symbol, but the changes were applied. Now nothing is transparent, menus, amsn, nothing, but then neither are my screensaver or openGL games.

I then got another problem where the top bar would float in front of my fullscreen apps, so I removed it which effectively solved the problem. However, has anyone fixed either the binary problem, or the problem with the top bar?

---

### Post by wooglin280 on 2007-06-30
I believe the square symbol is what myself and others are referring to as the binary bug.  If you make any changes to the default line, it turns into the square symbol.  If you add a new line, it turns into the square symbol  (as well as any other existing lines).  When it is the square symbol, all opacity is turned off.  

Also, this interface for changing opacity is really bad.  No newb is going to understand &, !, |.  I'm a java software engineer so i understand it, but the interface should be intuitive enough for anyone to understand.  I hope the compiz fusion team continues to improve these things.

---

