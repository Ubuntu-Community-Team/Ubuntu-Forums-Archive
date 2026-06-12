---
title: "Gnome control themes only work partially"
date: 2005-09-12
forum: Desktop Environments
---

### Post by openback on 2005-09-12
I've installed quite a few themes for GTK2 controls, but when I switch to them, quite a few change only the color scheme. The controls themselves just look like default GNOME. Some work, some don't. Has anyone else had this issue?

---

### Post by graigsmith on 2005-09-12
[QUOTE=openback]I've installed quite a few themes for GTK2 controls, but when I switch to them, quite a few change only the color scheme. The controls themselves just look like default GNOME. Some work, some don't. Has anyone else had this issue?[/QUOTE]
 gtk themes are mostly only color themes.  whatever metacity theme you are using may be overriding with it's own controls.  try some different metacity themes, and see what you come up with.

---

### Post by openback on 2005-09-12
[QUOTE=graigsmith]gtk themes are mostly only color themes.  whatever metacity theme you are using may be overriding with it's own controls.  try some different metacity themes, and see what you come up with.[/QUOTE]
 I just took your suggestion and went through a bunch of combinations of my themes. Still no luck.

---

### Post by graigsmith on 2005-09-12
i only get colors from gtk themes, as far as i know it's supposed to be that way...  sometimes they also have different scroll bars and tabs.

if you really want it to look different, you will have to use a different Metacity theme.

Alot of themes, have both metacity and gtk themes.  clearlooks for instance, has both a metacity theme, and a gtk  theme.  the gtk theme does the colors. and the metacity theme makes the rounded edges and everything.

if you wanna change the metacity theme you have to open up your themes, click theme details.  Then you can pick the colors with the controls tab, and you can pick the Metacity theme with the window border tab. 

so even though you downloaded a gtk theme from gnome-look.org it may look different in the screenshot, but the color will be the same.   in the screenshot, they probably are using a different metacity theme, and a different font.

---

### Post by openback on 2005-09-12
[QUOTE=graigsmith]i only get colors from gtk themes, as far as i know it's supposed to be that way...  sometimes they also have different scroll bars and tabs.

if you really want it to look different, you will have to use a different Metacity theme.

Alot of themes, have both metacity and gtk themes.  clearlooks for instance, has both a metacity theme, and a gtk  theme.  the gtk theme does the colors. and the metacity theme makes the rounded edges and everything.

if you wanna change the metacity theme you have to open up your themes, click theme details.  Then you can pick the colors with the controls tab, and you can pick the Metacity theme with the window border tab. 

so even though you downloaded a gtk theme from gnome-look.org it may look different in the screenshot, but the color will be the same.   in the screenshot, they probably are using a different metacity theme, and a different font.[/QUOTE]
 Well I'm talking about themes for the controls (Application Themes at art.gnome.org) . These are supposed to changed the style of the controls, not just the colors.

---

### Post by graigsmith on 2005-09-12
ok, how did you install it?  i tried easy listening and its working for me.

edit:  well if your getting the colors, you should be getting the controls as well.  im not sure why you wouldn't get controls, and get color.  but if you aren't getting color, or the controls, then mabey you diddn't install the theme right.  

or hey, mabey the theme is busted.  what theme isn't working?

---

### Post by openback on 2005-09-12
[QUOTE=graigsmith]ok, how did you install it?  i tried easy listening and its working for me.

edit:  well if your getting the colors, you should be getting the controls as well.  im not sure why you wouldn't get controls, and get color.  but if you aren't getting color, or the controls, then mabey you diddn't install the theme right.  

or hey, mabey the theme is busted.  what theme isn't working?[/QUOTE]
 I've been downloading it and using the "Install" button, but I found that I can drag a link from Firefox right onto the "Theme Details" dialog. I've always gotten a success dialog, and I tried Easy Listening, and that one works for me also. But this one: [http://art.gnome.org/themes/gtk2/159](http://art.gnome.org/themes/gtk2/159) just changes colors for me, even though it should change other things also.

---

### Post by graigsmith on 2005-09-12
i tried it as well, and no it doesn't work.   but if you look at the top of the page, it says it requires the bluecurve engine.  i don't know where you can get the bluecurve engine.  does anyone know where you can get that?  or is it only available in redhats os?

---

### Post by graigsmith on 2005-09-12
ahha, if you have the universe repositories available to you, you can go into synaptic and search for wonderland, install that package - and then you should be able to use that theme perfectly.

edit, you should be able to, but i just tried it, it diddn't work. mabey theres some kind of conflict.

---

### Post by openback on 2005-09-12
[QUOTE=graigsmith]i tried it as well, and no it doesn't work.   but if you look at the top of the page, it says it requires the bluecurve engine.  i don't know where you can get the bluecurve engine.  does anyone know where you can get that?  or is it only available in redhats os?[/QUOTE]
 I just now found that out, as I saw totem complain that it couldn't find an engine. I just installed the engines with synaptic and I'm good now. ( it's from a "back-port" repo ) I neve knew there were engines to install, too!

---

### Post by graigsmith on 2005-09-12
[QUOTE=openback]I just now found that out, as I saw totem complain that it couldn't find an engine. I just installed the engines with synaptic and I'm good now. ( it's from a "back-port" repo ) I neve knew there were engines to install, too![/QUOTE]
 cool.  glad to hear its working with the bluecurve thing from back-ports.  it doesn't seem to work with the one from universe repositories.

---

### Post by openback on 2005-09-12
[QUOTE=graigsmith]cool.  glad to hear its working with the bluecurve thing from back-ports.  it doesn't seem to work with the one from universe repositories.[/QUOTE]
 Yeah, well for some reason that installed libbluecurve.so into /usr/lib/gtk-2.0/2.4.0/engines/ , so I just made a link to it called libwonderland.so . Not sure why it did it like that, but all works well now.

---

