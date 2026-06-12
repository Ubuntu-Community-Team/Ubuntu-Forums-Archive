---
title: "Gnome panels"
date: 2010-08-10
forum: Desktop Environments
---

### Post by mathieumaes on 2010-08-10
I installed a brand new Ubuntu Netbook on a Asus eee PC 1201PN. It works out great, but I'm having a strange problem with the Gnome applets. I can't reach the gnome-panel properties, I can't add any panels or items on the panels... As if everything is on read-only!

I tried booting eeebuntu 3.0 where I get the same interface, but in this distro I can access all the panel configurations.

I also checked if the "locked_down" option is enabled in /app/panel/global using gconf-editor, but it's not checked...

How can I fix this ?

---

### Post by d3ejmz on 2010-08-19
yeah i would like to hear about this too, since i have 10.04 NBR installed on my HP mini 110 1045NR.

I would like to have the normal application menu (whatever it is that the analog to the windows "start" menu is called) and get rid of that icon-based program picker.

the gnome "Panel" app _will not start_. and i can't remove/add anything to the task bar.

i would also like to move the task bar down to the bottom and make it autohide (seems to me that would have been a default with such limited real estate as is on a netbook)

if anyone has help for us two new-to-ubuntu guys, much appreciation is here

thanks,
jim

(yes i know i joined the forum years ago but that was in another culture/country/life)

---

### Post by rtimai on 2010-08-19
Just a shot in the dark:  Did either of you install Ubuntu Tweak? I noticed that if you select Desktop > GNOME Settings > Complete lockdown of all panels, the Remove from Panel as well as Add to Panel options disappear from the drop-down menu. Sorry, I don't know how to make this change manually.

---

### Post by d3ejmz on 2010-08-20
no i haven't put Ubuntu Tweak on, but I can't remove anything from the panel, or add anything to it, or lock anything to it. the menu pops up, but the options are all greyed out.

look at my normal desktop fer crying out loud! No application menu! at the local computer shop (Free Geek Portland rocks, BTW) all their vanilla installs have a MENU that pops out when you click the little group hug button, and that button is a whole lot wider and says on it "Applications".

I get this weird point-and-grunt interface...

but i love the stability... haven't crashed anything yet!


maybe tweak comes all locked down with Netbook Remix? This is my first Ubuntu (or any linux) install in 4 years, so i am pretty clueless.

thanks for the ideas though

---

### Post by rtimai on 2010-08-20
d3ejmz, 

UNR might use a different default window manager from the Desktop edition, which could be incompatible with Gnome Panel. I'm pretty sure all Ubuntu editions use X-Windows and Gnome Display Manager (or are they the same thing?) The Ubuntu Desktop edition uses Metacity Window Manager, plus Compiz to add additional trimmings and functionality to windows. My hardware can't handle Compiz, so I think it was myself that installed LXDE and OpenBox low-resource window managers. It's complicated, when Linux has so many choices for each component of the desktop environment, and many overlap, or can even run inside each other. 

Now, at the Login prompt when you boot up, is there a taskbar at the bottom with something like Session Options? I have OpenBox, LXDE, Gnome/Openbox, Gnome, Failsafe Gnome, if I remember correctly. If so, you could try a different session, see if gnome-panel starts on any of them. (I believe the manual method of starting it from Terminal may be gnome-panel-control, then gnome-panel. Use the --help option for more information. Take all this with a grain of salt. I'm no Ubu-expert.)

Otherwise, you probably should post in the Netbook Remix forum. Hmm. I just checked and it's call Ubuntu Moblin Remix, dunno why. But there should be more participants there that know what you desktop components are, and what to do about the gnome-panel problem.  Good luck.

---

### Post by rtimai on 2010-08-20
Found this searching for "Ubuntu UNR missing gnome panel"

> [http://maketecheasier.com/unlock-gnome-panel-in-ubuntu-netbook-edition-une/2010/04/25](http://maketecheasier.com/unlock-gnome-panel-in-ubuntu-netbook-edition-une/2010/04/25)

Apparently the toolbar lock is by design, but there's a kind of technical workaround. 

d3ejmz, your symptoms COULD have been caused by a sequence of events. Elsewhere one user with a hidden gnome panel like yours reported that in Terminal, he entered "killall gnome-panel" thinking to start from scratch, and the original Panel popped into view. If you don't have an extra instance of gnome-panel running (I don't know if that's possible) and nothing happens, you should be able to enter "gnome-panel --replace" and return where you started. 

BTW, I have no clue how gnome panel starts up. I checked gconf-editor and gnome-session-properties, and can't find gnome-panel. FOUND: In Applications > System Tools > Configuration Editor, gnome-panel starts here:

Key name: /desktop/gnome/session/required_components/panel 
Name: panel
Value: gnome-panel

Key Documentation
Key owner: gnome
Short description: Panel
Long description: The panel provides the bar at the top or bottom of the screen containing menus, the window list, status icons, the clock, etc.

---

### Post by d3ejmz on 2010-08-21
too bad somebody decided that users shouldn't be able to access controls for the application menu and the panel. I would just like it on the bottom because that's what i am used to.

oh well, guess i'll live with it... 

feels kinda mac-like... not having a choice and all, that is :lolflag:

I couldn't find the configuration app you mentioned."configuration editor"

not in the menus...

i'll search for it later... it's late ;)

---

### Post by Vrroom on 2010-08-21
You amay want to look [here]("http://www.webupd8.org/2010/05/how-to-add-remove-applets-from-gnome.html")

---

### Post by Gaygerbil on 2010-08-21
UNR's panel is locked by default (horrible design choice I know), but luckily there's a way around it, the link above and this video will show you how to do it:

[http://www.youtube.com/watch?v=8cS1ksvPNEU](http://www.youtube.com/watch?v=8cS1ksvPNEU)

Don't worry it's easy my Gf did it and she just got Linux on her netbook a month or two ago. 

Just make sure you have your login set to Gnome after you do that and you'll be good. :]

---

### Post by rtimai on 2010-08-21
d3ejmc, you can run gconf-editor in Terminal if you can't find it in the menus. Use Edit Menus (alacarte, aka Main Menu) to check if Configuration Editor is deactivated in the menu. Still, I don't believe that all my installed programs appear in the menu either, probably not installed compliant with some menuing standard.

---

### Post by d3ejmz on 2010-08-22
Thanks for that info... I'll see what i can do with it. :)

---

### Post by d3ejmz on 2010-08-22
> **rtimai said:**
> d3ejmz, 
[...]
Now, at the Login prompt when you boot up, is there a taskbar at the bottom with something like Session Options? 
[...]

Hi, i didn't see this message before, don't know why. 

I didn't want to seem like i was ignoring you so i'll answer. No, i have no choice of session options when my netbook boots. It just goes right to work with the simple interface. 

It's okay. I am getting used to it. I just wish that there was an easy way to add applications to the menus when you install them (kinda like Windows 95 had?) i.e. "Do you want a desktop icon installed?" Duh, such a simple idea. I am sure there are tons of "really good" reasons that "can't" be done in Linux. I'll figure it out, and thanks for the prod towards that netbook forum, and your helpful attitude in general

---

### Post by d3ejmz on 2010-08-22
> **Vrroom said:**
> You amay want to look [here]("http://www.webupd8.org/2010/05/how-to-add-remove-applets-from-gnome.html")
Thanks, Vrroom!

I just switched sessions to GNOME and the normal cuspiness ensued!

---

