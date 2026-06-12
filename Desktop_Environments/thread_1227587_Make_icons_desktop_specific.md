---
title: "Make icons desktop specific?"
date: 2009-07-30
forum: Desktop Environments
---

### Post by HousieMousie2 on 2009-07-30
Okay, so I have my 6 desktops and set things up so that open windows show on the task bar only when viewing the desk top those windows are on... so my task bar isn't a cluttered mess.

Now what I want is to see my web-related icons on my web desktop and NOT on my media desktop... work on work, system on system and so on.

My icons are mostly files, a couple of folders, a few games (which I have a games desktop and would like those icons to only show on the games desktop.)

And when I dream big... it would be great if every music CD or movie DVD I popped into my machine would put it's icon only on my Media desktop.

Anyone know a (relatively) simple way to do this?  Is there some clickable something somewhere that I have overlooked?  Or would this be one of those situations where it can be done, but I would have to go through some command line stuff every time I added a new icon to a desktop, or some "simple" script that I don't know how to write? lol

Clearly this isn't a big deal, just one of those "Ya know, it would be really cool if..." kind of things.

Cheers!

---

### Post by SoftwareExplorer on 2009-07-30
I think that this has been mentioned a couple of times, but never implemented. I think it would be very cool.

---

### Post by HousieMousie2 on 2009-07-30
Damn **Snaps fingers** I was hoping...

It does seem the logical next step... if you can sort windows by desk top... task bar by desktop... why not icons?

Thanks for taking the time to reply!

---

### Post by SoftwareExplorer on 2009-07-30
> **HousieMousie2 said:**
> Damn **Snaps fingers** I was hoping...

It does seem the logical next step... if you can sort windows by desk top... task bar by desktop... why not icons?

Thanks for taking the time to reply!
Your welcome.  *heads over to brainstorm.ubuntu.com to see if it has already been proposed there*

---

### Post by Zorael on 2009-07-31
I seem to remember seeing a hack where you edited a plasma settings file to allow different activities (plasma setup) per desktop. Then you could add a different folder view to each activity. This might be a 4.3 thing, but you could try it. (The feature has been added but there isn't yet a graphical way to set it up.)

[list=1][*]Alt+F2, run the following: **kquitapp plasma-desktop**
[*]Likewise: **kate ~/.kde/share/config/plasmarc**
[*]Add the bottom line to the **[General]** header if it exists, else just add it all.
```
[General]
perVirtualDesktops=true
```
[*]Save, then Alt+F2: **plasma-desktop**
[*]Mouseover the cashew up to the right of your dashboard, Zoom Out, add more activities to fit your desktop setup.
[*]Zoom back in and see if changing desktops changes activities. Perhaps you have to restart plasma-desktop with **kquitapp plasma-desktop** and **plasma-desktop** again.[/list]

---

### Post by HousieMousie2 on 2009-07-31
I have Hardy Heron and KDE 3.5.10... can't really change that (for long drawn out reasons that involve my Mom... who's half way across the country.)

Have any idea if that works with what I'm running, Zorael?  Or anyone else?

I wasn't exactly trying to keep up with the news on Plasma, but I was under the impression that it wasn't really implemented in Hardy so much as with the newer releases... or am I off in my thinking?  lol  Again.

---

### Post by Zorael on 2009-07-31
Ah, yeah, plasma is new in KDE4. I'm not sure you can get desktop-specific icons at all in KDE3. ;/

You may want to pop in to #kde on irc.freenode.net and ask there; someone there ought to know.

---

### Post by HousieMousie2 on 2009-07-31
> **Zorael said:**
> Ah, yeah, plasma is new in KDE4. I'm not sure you can get desktop-specific icons at all in KDE3. ;/

Yeah, I had thought that, but I actually have the file you mentioned: plasmarc, so I figured at least some part of it was being worked in/on even as early as Hardy.

> 
You may want to pop in to #kde on irc.freenode.net and ask there; someone there ought to know.

Good idea.  Thanks again for your time and assistance!

---

### Post by SoftwareExplorer on 2009-07-31
I added an [idea solution]("http://brainstorm.ubuntu.com/idea/20645") for gnome, but if KDE already has it, its kind of redundant to propose it.

---

### Post by HousieMousie2 on 2009-07-31
According to pinotree in irc.freenode.net/#kde... it is not possible.

A rather resoundingly negative answer. lol

To which my brain yells back, "WHAT?!?  It HAS to be *possible*!"

Of course I have no earthly idea what it would take to make it possible.

But my mind goes to the fact that KDE allows the user to have different wallpapers on each desktop and it allows the windows to be sorted by desktop, so there is something functioning that is keeping track of what goes where... the question is... is it too far down the line to be made to handle the icons too.

It would seem to me that something higher in the food chain must be handling icons... lol but what do I know?  I'll answer that... nothing. lol

---

### Post by SoftwareExplorer on 2009-07-31
> **HousieMousie2 said:**
> According to pinotree in irc.freenode.net/#kde... it is not possible.

A rather resoundingly negative answer. lol

Was he talking about KDE 3.5 or 4.whatever too?

> **HousieMousie2 said:**
> To which my brain yells back, "WHAT?!?  It HAS to be *possible*!"

Of course I have no earthly idea what it would take to make it possible.

Just a theory: Maybe they are thinking of the desktop as a folder and don't see how to attach a little bit of info like 'only appears on desktop X' to each file with out causing issues. What if instead they keep a list of files and where they appear in  a separate file?

> **HousieMousie2 said:**
>  lol but what do I know?  I'll answer that... nothing. lol

You said it best, and it applies to me too!

---

### Post by HousieMousie2 on 2009-07-31
I identified my distribution and KDE version... so, unless he/she missed it, yeah, they meant KDE 3.5.10.

I dunno, but I asked another question in there... remains to be seen if I will be answered or not.

"Hardy Heron - KDE 3.5.10 - What is keeping track of which wallpaper goes on which desktop and what is keeping track of which windows were opened on which desktop and lastly what is keeping track of which icons should be displayed on the desktop?"

Better than half of what we see when we boot up was 'not possible' not all that long ago, granted most of that was due to hardware constraints, but not ALL of it.

C'mon, this is Linux... ANYTHING is possible. lol

---

