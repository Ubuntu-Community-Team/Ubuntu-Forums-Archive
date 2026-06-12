---
title: "New Wave theme Brainstorm"
date: 2008-12-15
forum: General Help
---

### Post by dilomo on 2008-12-15
Hi,

I'm the main creator of the theme New Wave

Here I'd like you to tell me what could be improved in the theme (now included in the community-themes package in Ubuntu 8.10)  by posting a opinion about it. Feel free to share anything that bothers you or that you like so that I keep it in there. The subjects I'm most interested in are:

[LIST]
[*]Top part of the windows
[*]Active/inactive windows feel
[*]Metacity feel
[*]Menus feel
[/LIST]

You can currently find the theme's last version [here]("http://www.gnome-look.org/content/show.php/New+Wave?content=87134") .

P.S. I have made some changes to the theme that could be seen in the following picture (they are not final yet):
[http://www.piccdrop.com/images/1229331419.jpg](http://www.piccdrop.com/images/1229331419.jpg)

---

### Post by Forlong on 2008-12-15
Hi dilomo,

I really like your theme, because it's dark-ish but still very usable. And most of all, it works great with Ubuntu, especially with the Human icon set, which is still my favourite.

This comes from a guy who's using Ubuntu since Dapper (that's over two full years now) and who could never stick too long with another theme than Human (minus the horribly dull window boarders, of course).
No theme was usable *and* pretty enough for me after a few days trial. I always went back to "default".


That said, I don't think there's anything particularly wrong with your theme.
So the first advice I'd like to give you is: don't change anything major.
Like the time you totally changed the close etc. buttons: not a smart move.
I happen to like the new ones (as a matter of fact, I didn't like the old ones at all), but many others don't, so give them **choice**.
Next time you change something that important, make sure to include both options (I know it's harder to maintain, but I think it's worth it).

The other thing is the dropdown menu.
I think they used to be of the same color as the panel, the change used to irritate me when switching from Hardy to Intrepid and installing the latest version of your theme.
Would be nice to have an option, if you want a white background in the menu or a grey one. I think both versions would be great.

Last but not least, the "glow" on buttons (you know, not when you hover with a mouse over them but when they appear to be "pre-selected") is both unique but sometimes irritating.
I'm not sure if I'd be happy if you'd get rid of it but it might be a good idea to go for something more ordinary.


But generally: I like the theme as it is. :)

---

### Post by dilomo on 2008-12-15
> **Forlong said:**
> Hi dilomo,
 
I really like your theme, because it's dark-ish but still very usable. And most of all, it works great with Ubuntu, especially with the Human icon set, which is still my favourite.
 
This comes from a guy who's using Ubuntu since Dapper (that's over two full years now) and who could never stick too long with another theme than Human (minus the horribly dull window boarders, of course).
No theme was usable *and* pretty enough for me after a few days trial. I always went back to "default".
 
 
That said, I don't think there's anything particularly wrong with your theme.
So the first advice I'd like to give you is: don't change anything major.
Like the time you totally changed the close etc. buttons: not a smart move.
I happen to like the new ones (as a matter of fact, I didn't like the old ones at all), but many others don't, so give them **choice**.
Next time you change something that important, make sure to include both options (I know it's harder to maintain, but I think it's worth it).
 
The other thing is the dropdown menu.
I think they used to be of the same color as the panel, the change used to irritate me when switching from Hardy to Intrepid and installing the latest version of your theme.
Would be nice to have an option, if you want a white background in the menu or a grey one. I think both versions would be great.
 
Last but not least, the "glow" on buttons (you know, not when you hover with a mouse over them but when they appear to be "pre-selected") is both unique but sometimes irritating.
I'm not sure if I'd be happy if you'd get rid of it but it might be a good idea to go for something more ordinary.
 
 
But generally: I like the theme as it is. :)
 
Thanks!
 
In the next release I will include both the current and the new metacity themes. The drop-down remained dark because it cannot be themed separately. Version 0.7 will be with white menus as 0.5.10 and any prev. I will probably include a version with dark menus.
 
This is the only pixmap theme that supports (nearly 80%) tab navigation (e.g. when you hit tab several times you can see where is the focus). That is the reason why I used this image. It is now fixed and each control has an image suited for it's form.
 
Other improvements are the separation of toolbar (as you can see on the preview image in my previous post) and small tweaks to the controls and especially to the check/radio buttons, tabs, expanders, entry combo boxes, default buttons and others. I have some more work on the tabs and I have to create a* new metacity* because this one has some design flows that has to be corrected. Here is the time to **[COLOR=black]give me ideas[/COLOR]** of how these buttons should look like.

---

### Post by Tibuda on 2008-12-15
I don't really like dark themes, but I like yours very much, and I'm using it since hardy (downloaded from the wiki), and now I'm using the intrepid repos version. I replaced the metacity with the old one ( [from this screenshot]("https://wiki.ubuntu.com/Artwork/Incoming/New%20Wave?action=AttachFile&do=view&target=newwave-meta050.png")), because the current version window buttons don't looks good if I change the buttons order (set /apps/metacity/general/button_layout to "close:minimize,maximize" in gconf-editor), and I prefer the simples circles too.

Well, keep the good work with the theme.

---

### Post by MonkeyPaw on 2008-12-15
The crazy thing is that I have the same wallpaper on my Ubuntu install. :lolflag:

---

### Post by Brian Vaughan on 2008-12-15
New Wave is my favorite theme. Thanks for making it!

The glow effect is one of my favorite features.

I've thought about asking for recommendations for wallpaper to match the theme.

My one criticism is that, in OpenOffice, the tooltips have a black border and black text with a transparent background. That makes it very difficult to read them. I don't know if that's within the theme definition, but with most other themes, the tooltips in OpenOffice have an opaque, yellowish background, so they're easy to read.

Edit: D'oh! You've fixed that already!

---

### Post by dilomo on 2008-12-16
> **danielrmt said:**
> I don't really like dark themes, but I like yours very much, and I'm using it since hardy (downloaded from the wiki), and now I'm using the intrepid repos version. I replaced the metacity with the old one ( [from this screenshot]("https://wiki.ubuntu.com/Artwork/Incoming/New%20Wave?action=AttachFile&do=view&target=newwave-meta050.png")), because the current version window buttons don't looks good if I change the buttons order (set /apps/metacity/general/button_layout to "close:minimize,maximize" in gconf-editor), and I prefer the simples circles too.

Well, keep the good work with the theme.

I'm currently wondering what type of buttons to choose: a single piece with three parts (like vista's buttons but not placed so high) or three separate buttons that are individual of each other. The last variant is getting old as style but is more customizable. The first one is trendy. Do you  have any ideas of what material these buttons should be made (glass, metal ...)?

As far as wallpapers: every wallpaper that is a bit darker and with less details is good for the theme. If it could be in the warm color range it would be best. [This]("http://www.hdwallpapers.net/") site has good wallpapers.

---

### Post by dilomo on 2008-12-25
The theme is released and now you can give it a try by downloading it from here:

[http://www.gnome-look.org/content/show.php/New+Wave?content=87134](http://www.gnome-look.org/content/show.php/New+Wave?content=87134)

---

### Post by alex.rayu on 2008-12-25
The color choice of unobtrusive colors is good. It's dark but not black. Tolerable. A few thoughts:

1. Music player is not the best place to see the controls. At least an open folder should complement it on the screenshot.
2. Can't tell the difference between the active and non-active window.
3. The default button outside glow looks weak. Probably it's a bad idea to make it outside at all.
4. Strong border around the window controls and the weak gray window controls strain my eyes to find the required control. Besides, the border being all 3 controls together. Ever wondered why Apple and M$ made them different colors? Not to make people look for the needed control.
5. the text on the buttons almost touches the button image (on the &#1054;&#1090;&#1082;&#1072;&#1079;&#1074;&#1072;&#1085;&#1077;) button. Need some spacing.

Thanks for taking your time!

---

### Post by mariner09 on 2008-12-25
One of the issues I have with this theme seem to be consistent in themes with black or dark panels.  I have 2 icons in the notification panel that always seem to take on a different color than the panel.  This does not happen in the "New Human" theme.  It also doesn't happen in any of the Nodoka Dark themes.  Is this based on the specific engine or any other settings that can be modified by the user?

---

### Post by alex.rayu on 2008-12-25
Ok. Lets review this wonderful PDF file written by the initial NewWave author. [https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/NewWave?action=AttachFile&do=view&target=graphical_guidelines.pdf](https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/NewWave?action=AttachFile&do=view&target=graphical_guidelines.pdf)

Why not stick to what this guy says - he has the clue.

1. He has no border around the window buttons.
2. Consisten/Simple/Eye-Easy. he has it!
3. Active/Inactive windows are more discrenable.
4. In the 0.7.0 the windows buttons are MUCH better, but they minimize/maximize buttons are smaller and are moved to top. As you move your mouse cursor to minimize you have to ajust to where they are located. Either make them as large as close button or center them vertically.
5. Usability - the window icons are gray. Need to be white. Better follow the ones that the initial design has - no border, very contrast/bold images of buttons. This is very popular now - Adobe, Apple - use them widely in their products. They are also very simple, which is good.
6. Selection. Orange selection color is bad. Even lighter orange.
7. Folder icon. He has them orange. But nicer orange icons than the ones currently proposed (the ones with dots).

Just some ideas.

---

### Post by dilomo on 2008-12-25
> **alex.rayu said:**
> The color choice of unobtrusive colors is good. It's dark but not black. Tolerable. A few thoughts:

1. Music player is not the best place to see the controls. At least an open folder should complement it on the screenshot.
2. Can't tell the difference between the active and non-active window.
3. The default button outside glow looks weak. Probably it's a bad idea to make it outside at all.
4. Strong border around the window controls and the weak gray window controls strain my eyes to find the required control. Besides, the border being all 3 controls together. Ever wondered why Apple and M$ made them different colors? Not to make people look for the needed control.
5. the text on the buttons almost touches the button image (on the &#1054;&#1090;&#1082;&#1072;&#1079;&#1074;&#1072;&#1085;&#1077;) button. Need some spacing.

Thanks for taking your time!

Have you seen the screenshot of the released theme? 

1.This was just a preview of the top of the windows because I think ppl have seen the controls of New Wave a lot in Gnome-look.org
2. That is already a past. See the screenshots on the link for download of ver. 0.7.0
3. I have made it as strong as I feel it should be. Can you try the theme yourself and then report if it is weak again?
4. Honestly I can't understand what are you talking about -> "... the border being all 3 controls ...". Maybe a screenshot will make things clearer? Btw what monitor are you using - LCD or CRT?
5. Well I think that this depends on the Icon not the spacing. See the plus Icon?


Thanks for the useful feedback!

---

### Post by dilomo on 2008-12-25
> **mariner09 said:**
> I have 2 icons in the notification panel that always seem to take on a different color than the panel.

What exactly are these applications? I think that this is fixable with proper match in the gtkrc file but I need to know what are the applications that cause the problem.

---

### Post by dilomo on 2008-12-25
> **alex.rayu said:**
> Ok. Lets review this wonderful PDF file written by the initial NewWave author. [https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/NewWave?action=AttachFile&do=view&target=graphical_guidelines.pdf](https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/NewWave?action=AttachFile&do=view&target=graphical_guidelines.pdf)

Why not stick to what this guy says - he has the clue.

1. He has no border around the window buttons.
2. Consisten/Simple/Eye-Easy. he has it!
3. Active/Inactive windows are more discrenable.
4. In the 0.7.0 the windows buttons are MUCH better, but they minimize/maximize buttons are smaller and are moved to top. As you move your mouse cursor to minimize you have to ajust to where they are located. Either make them as large as close button or center them vertically.
5. Usability - the window icons are gray. Need to be white. Better follow the ones that the initial design has - no border, very contrast/bold images of buttons. This is very popular now - Adobe, Apple - use them widely in their products. They are also very simple, which is good.
6. Selection. Orange selection color is bad. Even lighter orange.
7. Folder icon. He has them orange. But nicer orange icons than the ones currently proposed (the ones with dots).

Just some ideas.

I guess you have not heard or read a lot of New Wave. Fancois made this guidlines with a snapshot of New Wave 0.5.6 or smth like that very long time ago.

1. This was very old and not very usable metacity.
2. I think I have this now. Maybe the contrast is a bit more for some tired eyes. I will have a thought about this.
3. Impossible to be done as in the guidlines otherwise I would have done it a long ago.
4. Well you can move your mouse w/o adjusting it and it will still do what you want. Try it.
5. They are not grey in active windows. Besides you don't have to look at them but at the contents of the wondow.
6. Sorry but this is theme for Ubuntu. In the future I may do a blue version.
7. This is the them's iconset. I have not used it in the screenshots because it is not easy to install by newbees. You can find them here: [https://code.launchpad.net/~ubuntu-new-wave/anton/devel.icons](https://code.launchpad.net/~ubuntu-new-wave/anton/devel.icons)

---

### Post by alex.rayu on 2008-12-25
> **dilomo said:**
> 4. Honestly I can't understand what are you talking about -> "... the border being all 3 controls ...". Maybe a screenshot will make things clearer? Btw what monitor are you using - LCD or CRT?


Yep sorry I was not clear (and made a typo). That was the screenshot with the border around the window controls. I am glad it's gone. But then another comment that I later had is that now, the minimize and the maximize controls are smaller than the close control and are moved to top. The user expects them to be at least at the center of the window title and finding them even a bit higher requires attention. A user usually presses the required button mechanically, and giving extra attention to such things is a bit distracting as for me.

This can be solved by either pulling the buttons down to be at the center, or by making the max and min buttons at least as large as the close button, thus extending them into the expected area.

Again, objective that will be good, even though purely out of personal preferences I would go with high-contrast buttons without borders, like the initial mockup. But that's more subjective than the usability thing.

Thanks for working on it!

---

### Post by mariner09 on 2008-12-25
Lotus Notes, primarily...

Here's a screenshot...

---

### Post by dilomo on 2008-12-25
> **mariner09 said:**
> Lotus Notes, primarily...

Here's a screenshot...


Thanks for the info. I will have it in mind when preparing the next release and if possible will fix it.

---

### Post by dilomo on 2008-12-25
> **alex.rayu said:**
> ... But then another comment that I later had is that now, the minimize and the maximize controls are smaller than the close control and are moved to top. The user expects them to be at least at the center of the window title and finding them even a bit higher requires attention. A user usually presses the required button mechanically, and giving extra attention to such things is a bit distracting as for me.


Did you tried the theme on your PC? If you do you will see that the max/min buttons can be clicked without moving the mouse up because they have the same clickable area as the X button. So if you are doing it mechanically the you will be able to maximize without exactly pointing the button.

---

### Post by dilomo on 2009-01-03
> **mariner09 said:**
> Lotus Notes, primarily...

Here's a screenshot...


Unfortunately I can't fix this. Maybe if someone knows how to do it I will merge the changes.

---

### Post by Forlong on 2009-01-03
The problem with the icons in the notification area seems to be related to Java.
I can confirm this for Azureus/Vuze, managed to work around this by tweaking the icon itself.

Would be interesting to know if all dark themes are plagued by this.

---

### Post by dilomo on 2009-01-03
> **Forlong said:**
> The problem with the icons in the notification area seems to be related to Java.
I can confirm this for Azureus/Vuze, managed to work around this by tweaking the icon itself.

Would be interesting to know if all dark themes are plagued by this.

That would be interesting indeed. What exactly is this icon tweak?

---

### Post by Forlong on 2009-01-03
> **dilomo said:**
> What exactly is this icon tweak?
I simply changed the specific icon in Azureus' jar file to have a dark-grey background.

---

### Post by dilomo on 2009-01-03
> **Forlong said:**
> I simply changed the specific icon in Azureus' jar file to have a dark-grey background.

So the problem is not in the theme but in the icon not having transparent bg? I'm glad i dont use java based products.

---

### Post by Forlong on 2009-01-03
> **dilomo said:**
> So the problem is not in the theme but in the icon not having transparent bg?
I think so. But I didn't check with another dark-ish theme.

---

### Post by dilomo on 2009-02-07
I released the last bufix release of 0.7.x series and now I'm looking up to 0.8.0. The main changes are going to be in the treeview control and the scrollbars. So what I'm asking is everybody interested to tell me his/her ideas of how the scrollbars should look like or change? If you can show pictures it will be even better. If you don't want them to chnage write here too. 

I count on your opinions for modifying them so please share as much info as possible.

---

### Post by celticbhoy on 2009-02-07
I use your theme, but the only small issue I have is the last remaining little bit of orange that remains, it looks as though I have changed my theme from the Ubunutu default, but forgot to change an element. I know that it is a small thing, but to me it makes it look incomplete. Its not enough to stops me using the theme, just a little anoiance.

---

### Post by dilomo on 2009-02-07
> **celticbhoy said:**
> ... only small issue I have is the last remaining little bit of orange that remains, it looks as though I have changed my theme from the Ubunutu default, but forgot to change an element.

To be honest I can't understand what are you talking about. Can you be more specific or provide a screenshot?

---

### Post by celticbhoy on 2009-02-07
Sorry for nhot being clear/specific enough. The areas i am refering to are highlighted options, ie if you look at the first screenshot you provide in gnome look the item on the items Sans, Bold and 10 are highlighted in an orangish coloured bar. I know that this is a very petty concern, but it the only fault I can find with the theme. I think the colour is just too much like the stock Ubuntu human theme.

---

### Post by celticbhoy on 2009-02-07
ps I know that the use of orange is mentioned in the gnome-look page and is there for a reason, but to me me it is the only element that doesn't quite fit in with the rest of the theme.

---

### Post by dilomo on 2009-02-07
> **celticbhoy said:**
> ps I know that the use of orange is mentioned in the gnome-look page and is there for a reason, but to me me it is the only element that doesn't quite fit in with the rest of the theme.
 
Now I understand what are you talking about. This is the color of the text in treeview that Does not have focus. If the treeview has focus the color of the text is black. I made this because there is no other way to indicate the absense of focus.
 
If you are talking about the orange gradient bg I think that it has a little bit in common with Ubuntu's default theme but not much because my colors are a bit more red than the ones ubuntu uses. This similarity is not intentional because I haven't used human since my first install of ubuntu linux and that is about 3 years from now and I don't remember how it looked like :). 
 
Right now I'm developing New Wave ver. 0.8 that will have different treeviews with more detail and different color of highlight for sorted colums so it will look definitely different. 
 
P.S. 
After all I will consider your opinion in the development process. Thanks for the feedback!

---

### Post by celticbhoy on 2009-02-07
Glad to get the point accross. As I say I guess it was not meant to mimic Human, but as you are intentionally trying to form a sort of link tgo Ubuntu, then there will be some kind of throwback to the default Human theme Ubuntu supplies. I look forward to version 0.8, especially if the highlight colour changes.

Thanx for listening ...

---

### Post by dilomo on 2009-02-07
> **celticbhoy said:**
> I look forward to version 0.8, especially if the highlight colour changes.

Thanx for listening ...

No problem but you should consider the fact that New Wave 0.8.0 is not going to come anytime sooner than a month or even two.

However one of the most important things that should be done for this version is Firefox theme that itegrates the fixes from userChrome.css and add some more New Wave feel to the browser. I currently don't have the necessary knowledge but if there is someone else that could help me with that I would be very glad.

---

### Post by ugluck on 2009-02-07
hi i'm daniel planas, i'm a crator of new marmol theme. this my scrollbar brainstorming for newwave theme

[[img]http://images2.hiboox.com/vignettes/0609/91730644f905a5d43632988033666eef.jpg[/img]](http://www.hiboox.es/go/imagenes/dibujos/scrollbars,91730644f905a5d43632988033666eef.jpg.html)

---

### Post by Forlong on 2009-02-07
> **dilomo said:**
> I released the last bufix release of 0.7.x series
Thanks for keeping us updated.
Just installed it and I like what I'm seeing so far.
The only thing that bugs me is the context menu. It's plain white now &#8211; way too bright for my liking.


P.S. there's nothing wrong with the scrollbars, IHMO. I like 'em the way they are.

---

### Post by celticbhoy on 2009-02-07
Sorry to crash on your thread again, but I have been thinking about your thread, and more importantlly the reasons behind it. And I have just checked my setup to discover the reason the orangy colour looks so out of place is because I have changed my icon set to something monochrome, therefore the last whisp orange is out of place. But to be constructive I think the additional element that you should look to add is a backround fitting with the theme. Maybee some of the posters to this thread could upload there own as suggestions.

On another note, remember to post when the new theme does become available.

---

### Post by dilomo on 2009-02-08
> **ugluck said:**
> hi i'm daniel planas, i'm a crator of new marmol theme. this my scrollbar brainstorming for newwave theme
 
[[IMG]http://images2.hiboox.com/vignettes/0609/91730644f905a5d43632988033666eef.jpg[/IMG]]("http://www.hiboox.es/go/imagenes/dibujos/scrollbars,91730644f905a5d43632988033666eef.jpg.html")
 
Well you have done good mockup but I have to say that this is no scrollbar but slider. Scrollbars are located at the most right or bottom of some windows and allow you to move the contents if they are more than the available screen space. 
 
I think that there are too many Sliders with rounded moving parts so I won't do it that way but if you wish you could modify it in your theme as long as you keep up with the license: share it like I did, mention me in the desctiption and of cource you can't make money from it ;) 
 
 
[quote=Forlong]Just installed it and I like what I'm seeing so far.
The only thing that bugs me is the context menu. It's plain white now – way too bright for my liking.[/quote]
 
The context menus should not be plain white but a shade of gray. If they are white - there must be something wrong with the gtkrc file. I will check this out. 
The scrollbars are way to blurry in some cases so I will try to improve that and will post the result here in order to get more feedback before release.
 
 
[quote=celticbhoy] ...therefore the last whisp orange is out of place. But to be constructive I think the additional element that you should look to add is a backround fitting with the theme. Maybee some of the posters to this thread could upload there own as suggestions.
 
On another note, remember to post when the new theme does become available. [/quote]
 
So the human look is gone? I let the user decide what bg is appropriate for him but in the next version I may try to iclude one and I will write here when it's released ;)

---

### Post by Forlong on 2009-02-09
Just installed the darkmenus version and everything's sorted now.
I wonder why darkmenus is not the  default, though.

---

### Post by ugluck on 2009-02-11
I have a couple of new mockups


slider (I still think they have problems)

[[img]http://images1.hiboox.com/vignettes/0709/9bed21a3632992ab9078d96be5df6714.jpg[/img]](http://www.hiboox.es/go/imagenes/informatica/scrollpropose,9bed21a3632992ab9078d96be5df6714.jpg.html)


Scrollbars(I like the scrollbars as they are;) I did not change)

[[img]http://images1.hiboox.com/vignettes/0709/4c501d97c02806144b70245bc51ec7f5.jpg[/img]](http://www.hiboox.es/go/imagenes/animales/scrollpropose2,4c501d97c02806144b70245bc51ec7f5.jpg.html)

---

### Post by dilomo on 2009-02-15
> **ugluck said:**
> I have a couple of new mockups


slider (I still think they have problems)

[[IMG]http://images1.hiboox.com/vignettes/0709/9bed21a3632992ab9078d96be5df6714.jpg[/IMG]]("http://www.hiboox.es/go/imagenes/informatica/scrollpropose,9bed21a3632992ab9078d96be5df6714.jpg.html")


Scrollbars(I like the scrollbars as they are;) I did not change)

[[IMG]http://images1.hiboox.com/vignettes/0709/4c501d97c02806144b70245bc51ec7f5.jpg[/IMG]]("http://www.hiboox.es/go/imagenes/animales/scrollpropose2,4c501d97c02806144b70245bc51ec7f5.jpg.html")

Good idea about the first mockup!

Sorry I didn't write for a while but I had to go away from home. I think that I might try what you suggest in your first mockup but the scrollbars should stay the same I suppose. One thing that could be improved a bit is more clear and sharp (in the shadow section) overall look.

[quote=Forlong]
Just installed the darkmenus version and everything's sorted now.
I wonder why darkmenus is not the  default, though.     [/quote]

I use the one with light menus as default because it is more usable compared to the dark menus version.

---

### Post by dilomo on 2009-06-19
It's been a while since I posted back here but now I would like to ask everybody of what they think of the scrollbar arrow positions in New Wave 0.8.0? 

Which one of the following variations you like most:
 a- Arrows at top and bottom
 b- Arrows at bottom
 c- Arrows at top
 d- No arrows at all( New Wave 0.8 was designed with this in mind) 

Please write explanation if possible.

---

### Post by SerenityKill3r on 2009-06-19
I don't know if this has been mentioned, but when I resize a window, theres a gap that appears quickly between the window border and the menubar (File, Edit, View etc.).

It's most noticeable in minimising and maximising applications.

---

### Post by dilomo on 2009-06-19
> **SerenityKill3r said:**
> I don't know if this has been mentioned, but when I resize a window, theres a gap that appears quickly between the window border and the menubar (File, Edit, View etc.).

It's most noticeable in minimising and maximising applications.

Can you show a screenshot?

---

### Post by SerenityKill3r on 2009-06-19
> **dilomo said:**
> Can you show a screenshot?

it happens too fast to capture, but its still noticeable, and can be annoying if I'm doing alot of minimising and maximising.

Chances are its a compiz issue, and not an issue with the theme.

---

### Post by dilomo on 2009-06-19
> **SerenityKill3r said:**
> it happens too fast to capture, but its still noticeable, and can be annoying if I'm doing alot of minimising and maximising.

Chances are its a compiz issue, and not an issue with the theme.

The chance is quite big if the gap appears between the menubar an the titlebar but if it appears in the place of the menubar it is a slow not optimize pixmap engine. If so I'll try to fix it in the next release by minimizing color variation.

---

### Post by dilomo on 2009-06-27
> **dilomo said:**
> It's been a while since I posted back here but now I would like to ask everybody of what they think of the scrollbar arrow positions in New Wave 0.8.0? 

Which one of the following variations you like most:
 a- Arrows at top and bottom
 b- Arrows at bottom
 c- Arrows at top
 d- No arrows at all( New Wave 0.8 was designed with this in mind) 

Please write explanation if possible.


So nobody want's the arrows to be changed?

---

### Post by dsavi on 2009-06-27
Personally I like the arrows as they are in Jaunty, (Which version of New Wave that is I do not know) both at the bottom.

Thanks for making it, New Wave has finally convinced me that Gnome can be graphically superior to Windows and Mac OS X. Do you have a degree in graphic design or something?

---

### Post by dilomo on 2009-06-28
> **dsavi said:**
> 
Thanks for making it, New Wave has finally convinced me that Gnome can be graphically superior to Windows and Mac OS X. Do you have a degree in graphic design or something?

Well not exactly but I'm in the architecture filed so I know smth about color, composition and accuracy ;)

---

### Post by benjamimgois on 2009-07-03
Hi Dilomo,

Personaly, i prefer the tradicional way, with narrows at the top and bottom. I think that it's more intuitive, and easier for new users. 

The only point, that i think that it could be better on New Wave is the Metacity Buttons, they are good, but not that good in my opinion. I would like to suggest the ones used on "Impression" theme.

[IMG]https://wiki.ubuntu.com/Artwork/Incoming/Karmic/Impression/Metacity?action=AttachFile&do=get&target=MetaCityMockup.png[/IMG]


At least for me, they look modern and pretty. 

Congratulations for the great job, New Wave stills one of the bests themes already done for gnome.

---

### Post by dilomo on 2009-07-04
Thanks.

I know of this metacity but think that is not intuitive enough for new users. I know that the current New Wave theme's metacity is not the best one. So I will try to make a refined version for the next release but I don't promise this yet as I have a lot of other work.

---

### Post by benjamimgois on 2009-10-17
Hey Dilommo, a new ubuntu version is comming, and there's a lot of changes in the UI and in the Human-theme. But, at least for me, new wave still has the best look ever, and even fits well with the new boot screen. I'm not an artist, but i have some suggestions to improve new wave. 

[LIST]
[*]The metacity buttons that will be used on Opensuse 11.2, they look simple and nice and could fit well on new wave.
[*]Metacity borders and scrools from Humanity 1.2, could give a more modern look.
[/LIST]
obs: The scrools could continue to use gray and orange, in the same way as new wave is now, but use the style of humanity 1.2. Take a look at the screenshots below. 

Well this is just a suggestion, i hope this could help in some way.

---

### Post by dilomo on 2009-10-22
> **benjamimgois said:**
> Hey Dilommo, a new ubuntu version is comming, and there's a lot of changes in the UI and in the Human-theme. But, at least for me, new wave still has the best look ever, and even fits well with the new boot screen. I'm not an artist, but i have some suggestions to improve new wave. 

[LIST]
[*]The metacity buttons that will be used on Opensuse 11.2, they look simple and nice and could fit well on new wave.
[*]Metacity borders and scrools from Humanity 1.2, could give a more modern look.
[/LIST]
obs: The scrools could continue to use gray and orange, in the same way as new wave is now, but use the style of humanity 1.2. Take a look at the screenshots below. 

Well this is just a suggestion, i hope this could help in some way.

Thanks for the suggestions!

Right now I don't have Internet because a problem with my roommate has occurred but when I do have it back I promise some cool new features of New Wave that I have developed in the meantime. 
As far as the proposals you made:
- The metacity might change if I have time to test it. I have thought of a simpler version and will try its looks for a month.
- About the borders and scrolls of Humanity I do not agree and will most likely not change them because they represent more visual clutter (more lines to display a certain action) 

P.S. Sorry for not responding faster but I'm writing from a friend's PC.

---

### Post by Forlong on 2009-10-24
Hi,

I installed the latest version from Gnome-look.org and found out that unsing plain Metacity causes the titlebar to change color (light grey) when going fullscreen (e.g. maximizing Firefox).
This does not happen with Compiz enabled.

Looks like abug to me, is it possible to prevent this behaviour?

---

### Post by lrgalego on 2009-10-30
I really like your theme, I'm using it in Ubuntu 9.10
I just want to make one little change, how could I change the menu to the part of gadgets stay transparent just like the middle of the menu, like the Human theme does?

---

### Post by dilomo on 2009-11-05
Forlong can you provide a screenshot?

As far as the transparent panels tat feature is coming soon in the next version of the theme as well as much improved Configurator application. Just be patient - a week or two.

---

