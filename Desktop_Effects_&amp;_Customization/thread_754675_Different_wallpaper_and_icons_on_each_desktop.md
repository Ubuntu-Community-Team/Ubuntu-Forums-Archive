---
title: "Different wallpaper and icons on each desktop"
date: 2008-04-14
forum: Desktop Effects &amp; Customization
---

### Post by tommyhakinen on 2008-04-14
HI,

I am using gutsy with CCSM installed. I have been using the Cube dekstop for awhile till I realised that i didn't make full use of it. I was thinking is there a way that I can configure different wallpapers and icons on each desktop.

thank you

regards,

tommy

---

### Post by lpkizz on 2008-04-14
sorry dude you can't you can only do that in Kubuntu but in Ubuntu it's just one theme and one wallpaper

---

### Post by Eclipse. on 2008-04-14
It is possible but it involves hacking gnome a bit and you have to remove compiz then reinstall it again.

Search for it in this forum,  I was reading a howto yesterday.

EDIT: Nvm that, I found an easier way:

I. Disable "show desktop" in Nautilus
1. ALT+F2
2. gconf-editor
3. Apps --> Nautilus --> Preferences
4. Untick "show desktop"

II. Install ccsm (if you dont have it already):
1. In Terminal, input the following:
```

sudo aptitude install compizconfig-settings-manager
```

2. Exit Terminal

III. Select your desktop wallpaper
1. System --> Preferences --> Advanced Desktop Settings
2. Tick "Desktop Cube" and opt to disable desktop wall if prompted
3. Tick "Rotate Cube"
4. Select "Desktop Cube"
5. Click "Appearance" tab
6. Click "Add" under the "Background Images" field
7. Browse for your desired wallpaper(s), ordering them based on which face of the cube you want them to appear

Lol, I went to all the trouble of patch gnome and everything.lol

EDIT2: Slight problem with that method as your desktop icons disappear.Search for other method if you want your icons.

---

### Post by tommyhakinen on 2008-04-14
thanks for the reply.
i am going to try it out.

---

### Post by dfmalh on 2008-04-15
Hi I had this under a different post, but the tread is closed now.

I installed Kubuntu desktop (I usually work with Ubuntu/Gnome) to have a look at the KDE environment, and I noticed the following:

When you use Compiz Fusion under the KDE environment with e.g. 1 desktops, it shows 4 work spaces on the system tray but you only have one desktop. I guess this assists in creating the cube (virtual workspaces), which I actually like. It looks nice and one can spread/group and find applications easy.

The downside to this setup is that all opened applications is also visible in the bottom bar... thus if you have e.g. your mail, internet browser, a terminal and Open Office running each on a separate workspace, you can always also see them in the bottom bar. This becomes more of a problem if you start opening more and more programs, and all of them are on the bottom bar. The idea of moving an application to another workspace it to have everything less cluttered. This does not happen under Ubuntu/Gnome. Everything is separated.

Then if you create an additional desktop, you end up with 8 workspaces on the bottom bar, and this problem continues with the more desktops you create. If you want 4 desktops, you will end up with 16 workspaces... furthermore, if you have more than one desktop, and you figure out which one of the work spaces belongs to which desktop and you have one application on one desktop, and another (e.g. Desktop 1, workspace1 and Desktop 2, workspace 1)on the other, only one is displayed on the bottom bar...

So the problem must be with the 4 "workspaces" for every desktop.

This problem does not happen in Ubuntu/Gnome.

Any ideas?

_Hyperair replied with this_:

Install the "kicker-compiz" and "kicker-taskbar-compiz' packages. Then exchange your taskbar applet in kicker with the compiz taskbar or something of that sort. Also exchange your pager applet with the kicker compiz pager applet.

_I would like to respond to the anser as follws_:

Thanks for your reply. Sorry for the delay on my side, I had to re-install the KDE desktop (I did it via Synaptic Package Manager, I just ticked the kubuntu-desktop and apply).

I installed the "kicker-compiz" and "kicker-taskbar-compiz' packages (also through Synaptic Package Manager).

Then exchange the "Taskbar" applet with the "Taskbar - Compiz".

I then exchanged my "Desktop Preview & Pager" applet with the "Desktop Preview & Pager - Compiz" applet.

This solved the problem of showing all oped applications on the bottom Taskbar. It now shows only what is open on the workspace you are on. Thanks for the help with that.

I still have the problem with multiple desktops, e.g. 2 desktops gives me 8 workspaces, and the first four workspaces shows "Desktop 1" as the common name and workspaces 5-8 shows "Desktop 2" as the common name. So the conflict still exists between the "Workspaces" and "Desktops". You can also not give each workspace its own name... 

Any thought on that?

I hope I posted under the correct tread. :???:

---

