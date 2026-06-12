---
title: "Transparment wallpaper terminal problem"
date: 2009-01-19
forum: Desktop Environments
---

### Post by Freke88 on 2009-01-19
Hello I am doing some changes to my desktop, big thanks to SlicknesS and Rob
but something aint right for me I want a transparent terminal that blends with the wallpaper but for some reason the panel is shown with the cross, minimize, maximize buttons and a frame

how can i get rid with that?
PS Attaching a screenshot and sorry if this is wrong section to post

See post [#12]("http://ubuntuforums.org/showpost.php?p=6583367&postcount=12") for solution

---

### Post by neu2buntu on 2009-01-19
i did this by accident before, but it made all my windows(not just terminal) lose the top bar. if i remember correctly i did this in compiz-config-settings manager and i turned off windows decorator...hope this is of some help to you.

---

### Post by gjoellee on 2009-01-19
> **Freke88 said:**
> Hello I am doing some changes to my desktop, big thanks to SlicknesS and Rob
but something aint right for me I want a transparent terminal that blends with the wallpaper but for some reason the panel is shown with the cross, minimize, maximize buttons and a frame

how can i get rid with that?
PS Attaching a screenshot and sorry if this is wrong section to post

Hi there, do have a terminal that blends in with your desktop, you cannot use the original "gnome-terminal". You must install some other terminal I think. I do not know which...

Uansett...jeg synes det jeg så på bildet var Norsk?

---

### Post by Freke88 on 2009-01-19
Jepp det var norsk ;)

"Yes it was norwegian"

---

### Post by Ludachrispeed on 2009-01-19
Hey,

Lots of people are having trouble getting that to work on intrepid.  It worked on earlier versions, I hear.

Here's the thread where they're talking about it:  [http://ubuntuforums.org/showthread.php?t=202249]("http://ubuntuforums.org/showthread.php?t=202249")

P.S. if you figure out how to do it, let me know!

---

### Post by mcduck on 2009-01-19
> **gjoellee said:**
> Hi there, do have a terminal that blends in with your desktop, you cannot use the original "gnome-terminal". You must install some other terminal I think. I do not know which...

Uansett...jeg synes det jeg så på bildet var Norsk?

Yes, you can. You just need some way to tell the window manager to not draw window borders for the terminal. This is usually done using Devilspie, but if you are using Compiz you can get the same result with it's plugins.

---

### Post by Freke88 on 2009-01-20
I am using Devilspie, and the borders are still there :(

---

### Post by mcduck on 2009-01-20
> **Freke88 said:**
> I am using Devilspie, and the borders are still there :(

Then you haven't configured Devilspie to remove those borders, or there's something wrong with your Devilspie configuration. ;)

---

### Post by Freke88 on 2009-01-20
> **mcduck said:**
> Then you haven't configured Devilspie to remove those borders, or there's something wrong with your Devilspie configuration. ;)

```
(if
(matches (window_name) "SkrivebordTerminal")
(begin
(set_workspace 4)
(below)
(undecorate)
(skip_pager)
(skip_tasklist)
(wintype "utility")
(geometry "+50+50")
(geometry "924×668")
)
)
```

---

### Post by mcduck on 2009-01-20
Sorry, it's been years since I've used Devilspie and the syntax has changed after that. I can't help you with Devilspie configuration. But if you want I can help you to remove the borders with Compiz..

Do you want all terminal windows to be transparent, or just one of them?

edit: actually it makes no difference, it can be done using window name just like you are now trying to do with Devilspie.

---

### Post by Freke88 on 2009-01-20
> **mcduck said:**
> Sorry, it's been years since I've used Devilspie and the syntax has changed after that. I can't help you with Devilspie configuration. But if you want I can help you to remove the borders with Compiz..

Do you want all terminal windows to be transparent, or just one of them?

edit: actually it makes no difference, it can be done using window name just like you are now trying to do with Devilspie.

Just the terminalprofile i have for the desktop :)

---

### Post by mcduck on 2009-01-20
You need to be running Compiz (the "desktop effects") before you can do this

1. First, open the CompizConfig Settings Manager. (Install it first if you haven't got it already).

2. Go to Window Decoration-plugin's settings, and add your program/window/class to the "Decoration windows"-field *as Invert*. This will remove borders.

In your case, just change the field to this:```
(any) & !(name=SkrivebordTerminal)
```

3. Move on to Window Rules-plugin, and add your program to all the fields you want (the field names will tell you what they do. For a typical desktop terminal you'd want to use "Skip Taskbar", "Skip Pager", "Below" and "Sticky". In your case, add following code to those fields:
```
name=SkrivebordTerminal
```

Now you should have a terminal window with no borders, which doesn't show on taskbar or pager, is always below other windows and is visible on every workspace.

edit: If you use the "Show Desktop"-button on your panels, you might want to stop the terminal from hiding with other windows. In that case go to General settings, and on General-tab disable "Hide Skip Taskbar Windows".

edit2: Based on your devilspie configuration you might want to set the window size and place it into workspace 4 instead of stickying it into all workspaces. The size can be configured on the "Window Rules"-plugin's "Size Rules"-tab, and the workspace in "Place windows"-plugin's "Fixed Window Placement"-tab, in the "Windows with fixed viewport"-section..

---

### Post by Freke88 on 2009-01-20
Thank you very mutch this worked perfectly :KS

---

### Post by Subban on 2009-01-20
I've been using a transparent terminal on the desktop for a few years now, using Eterm as the terminal window with the following options, I have it on a launcher on a gnome panel.

```
Eterm --trans -x --shade=0 --scrollbar=0 --buttonbar=0 --geometry=80x15+0+790 --foreground-color=white --color4 rgb:0/0/0
```

Adjust colours and position as required, I didn't really see the need to run devilspie as this was the only use I had for it, I hope it helps someone else.

---

### Post by mcduck on 2009-01-20
> **Subban said:**
> I've been using a transparent terminal on the desktop for a few years now, using Eterm as the terminal window with the following options, I have it on a launcher on a gnome panel.

```
Eterm --trans -x --shade=0 --scrollbar=0 --buttonbar=0 --geometry=80x15+0+790 --foreground-color=white --color4 rgb:0/0/0
```

Adjust colours and position as required, I didn't really see the need to run devilspie as this was the only use I had for it, I hope it helps someone else.
On the other hand, why even install Eterm when you can get the same result with programs already installed..

If you use Eterm you need to install 1 program. If you use Gnome-terminal with Devilspie you need to install one program. If you use Gnome-terminal with Compiz you already have everything you need.

Besides, Gnome-terminal supports true transparency and antialiased Truetype fonts (+ easier way of managing terminal settings).

---

### Post by Subban on 2009-01-20
> **mcduck said:**
> On the other hand, why even install Eterm when you can get the same result with programs already installed..

If you use Eterm you need to install 1 program. If you use Gnome-terminal with Devilspie you need to install one program. If you use Gnome-terminal with Compiz you already have everything you need.

Besides, Gnome-terminal supports true transparency and antialiased Truetype fonts (+ easier way of managing terminal settings).

Well, Devilspie is running in the background all the time isn't it? Please correct me if I am wrong about that but I didn't want have something running fulltime for a minor 'feature'.

Handling it with Compiz is certainly another solution if you run Compiz full time, I'm not sure what percentage of people do that, I suspect many like myself switch between Compiz and metacity but again I may be wrong about that. The method using Eterm I use is happy with compiz or metacity and doesn't require anything else to be running to do it.

I have the Eterm on the desktop 100% of the time with Irssi, hellanzb and mediatomb and a bash (just for odd jobs) running inside a screen (screen is setup to launch those apps by default). I use normal gnome-terminals for my day to day use. Personally I don't use a transparent terminal for my day to day work perhaps others are the same. I am not arguing the use of devilspie, merely saying I didn't feel it was the best solution for me, and throwing it out there as it might be useful for anyone wanting a simpler(?) solution for a window on the desktop to display irc, top or anything similar.

Oh, you are dead right of course about Eterm not being the prettiest with its fonts and not as easy to change options on, but it does just fine for a desktop window.

---

