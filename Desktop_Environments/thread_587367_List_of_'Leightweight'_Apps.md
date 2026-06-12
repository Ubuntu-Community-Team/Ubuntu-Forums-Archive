---
title: "List of 'Leightweight' Apps?"
date: 2007-10-22
forum: Desktop Environments
---

### Post by ghandi69_ on 2007-10-22
Hey guys, as 'Alternate' window manager users (Flux, Xfce, IceWM, OpenBox, Enlightement, etc) I think it would be a good idea to generate a list of software that is in repos that doesn't depend a lot on gnome or kde.
 
On my computer, I use some of the following...

Music Player - XMMS

Notepad equivalent - Scite

Image viewer - Mirage

File Browser - Thunar..

etc...

I personally, am looking for a more full featured file browser that doesn't depend kde/gnome as much as Konquerer or Nautilus.  Just wondering what programs you guys are using out there...

---

### Post by loell on 2007-10-22
reminds me of fluxbuntu ;)

**sylpheed claws** - mail client
[B]
Kazehakase[/B] for web browser

**rox** for file manger/ browser

---

### Post by ghandi69_ on 2007-10-22
I would say a list of categories might be a good way to go...

Web Browser - Kamekaze/Dillo/Epiphany

File Browser - Rox-Filer/Thunar/Midnight Commander

Music Player - XMMS, Audacious, ??

IM - Pidgin, ??

Burning Software, replacement for K3b????

Image Editing Software - I think gimp is the only way to go.

Video Player - Is VLC the lightest??

Maybe a good list of lightweight develeopment environments would be useful....

---

### Post by TeaSwigger on 2007-10-22
Okay some contributions from me. File managers this time - 

PCManFM
Single pane with tabs and tree layout, yet incredibly quick and light. Like the following, might be quick as they come short of CLI. In the repos.

emelfm
Dual-pane "midnight commander" style. emelfm is GTK+ and inherently ugly, but quick as it gets. Seriously fast. In the repos.

emelfm2
Dual-pane "midnight commander" style. emelfm2 is GTK2x and far nicer looking, with more features and polish to boot, but it retained its seriously fast speed. Not in the repos, possibly due to license situation.

Gentoo (the file manager, not related to the OS).
GTK+ with ugliness to prove it. But if you just want featherweight speed and loads of configureability and features, well... there it is. I couldn't warm to it but ymmv.

Rox-Filer
Mentioned above. Unorthodox and quirky to some but flexible, well appointed and blazing fast.

Of course you can't beat the command line apps for speed and size. Anyone comfortable with CLI with a very slow PC or wanting to minimize that load might try the venerable Midnight Commander, the descendant of the original full featured dual-pane file manager, still alive, available and in the repos.

All that said, as I'm based on Kubuntu Feisty anyway, I tend to use Konqueror and Krusader. They're way, way heavier than any cited above, but one can't really find better file managers if one's hardware is up to it. If wanting less fuss though, I use pcmanfm or rox about as much as the KDE big hitters.

Edit: adding note that I tend to use rox in Fluxbox and pcmanfm in IceWM, just suits the feel to me. :)

---

### Post by HermanAB on 2007-10-22
Hmm, just go to the Puppy Linux web site and see what they got:
[http://puppylinux.com/](http://puppylinux.com/)

Cheers,

Herman

---

### Post by TeaSwigger on 2007-10-23
> **ghandi69_ said:**
> Web Browser - Kamekaze/Dillo/Epiphany

Kamekaze?! :shock: nononono, Kazehakase :) Slightly different meanings and hopefully as different performance eh? ;) Seriously, there does seem to be a gap in the browser selection. On one hand you have the full on, fine browsers like Konqueror or Firefox / SeaMonkey / Swiftfox / IceWeasel / Epiphany / Kazehakase (all those and more based on the Gecko browser engine). Then you have browsers so light that they cannot render all elements of a common web page like javascript (understandable) CSS (yikes), even tables and frames in some cases. If there's a nice mid-weight browser with solid rendering that leaves out things like flash(tm) shockwave(tm) and java - or better yet, has light support of that sort of thing perhaps via optional and easily toggled enabled/removed modules - that'd fill a hole in the lineup and likely find a home on my PC.

---

### Post by TeaSwigger on 2007-10-23
Some more, all just my opinion. You mileage may vary etc.

> **ghandi69_ said:**
> Music Player - XMMS, Audacious, ??
CPlay. 

Ah but that's CLI. ;) The WinAmp-based trio (XMMS, Audacious, the old Beep Media Player) are sweet. Something even leaner like xfmedia might have an edge in resource use though.

For "dedicated" GUI CD players there's XFreeCD. Don't imagine one can get lighter, assuming it works at all in your setup.

> IM - Pidgin, ??
No idea, only know that Kopete rocks. But it's no Gigi Edgley on the scale.

> Burning Software, replacement for K3b????
I would've said xfburn but as far as I know, it's still broken and virtually unmaintained. Hope it's active again? Or how about Graveman?

k3b rocks though. It is downright lightweight to me after coming from Nero 7. Alas I'm using the also-nice Gnomeburner for now since k3b refuses to burn well or at a decent speed on my system. Gnomeburner is doing a perfect job. It feels just as heavy though, and is less configurable.

> Image Editing Software - I think gimp is the only way to go.
I think you're right ;) Although Krita is a very nice "paintshop-pro"-ish editor.

How about viewers? Two categories perhaps: those which are viewers alone and those which offer thumbnail navigation etc. I've found the lightest straight GUI viewer I've stuck with to be gpicview. It's faster than the crisp Mirage! Instant. For the very lightest, we'd probably have to toss all or most of the GUI and go with feh or ImageMagick. 

For thumbnail nav type viewers I suspect gqview would be the fastest. 'Taint pretty but it is quite good.

My fav for picture quality and overall feel are Gnome's combo of Eye of Gnome and gThumb. If I'm pouring over galleries taking my time I tend to use those two. As my main GUI viewers though I use the ballerina class gpicview & gqview.

> Video Player - Is VLC the lightest??
Can't say. I'd be surprised if it were the lightest video player, but perhaps the lightest which supports as many formats as well. Between VLC and Kaffeine I haven't felt a need to explore options yet.

> Maybe a good list of lightweight develeopment environments would be useful....
Web or software? Web wise, KompoZer's quick on my PC. Software wise I've no idea. 

Wanted to add a bit more about file managers. Thunar is great, I've used it and like it. It feels pretty "down to business" to me in a good way. You get your choice of button or address line style bar and bookmark or tree nav. The mounting features are an amazing effort, and it also doubles as a superb bulk rename utility. For the features it offers, the performance is absolutely fantastic. pcmanfm is the closest to Thunar in general look and feel, and gains even more speed than Thunar by dropping many features like mounting, bulk rename and more. So in terms of features it's quite limited. There's also the not inconsiderable point that pcmanfm does have some bugs while Thunar was bug free when I'd used it. But if one likes Thunar and wants or needs an even lighter app just for file browsing with some management, that's where pcmanfm might fit the bill.

---

### Post by urukrama on 2007-10-23
Have a look at this thread: [Lightweight Apps: Suggestions?]("http://ubuntuforums.org/showthread.php?t=401337&highlight=lightweight")

---

### Post by ghandi69_ on 2007-10-23
> **urukrama said:**
> Have a look at this thread: [Lightweight Apps: Suggestions?]("http://ubuntuforums.org/showthread.php?t=401337&highlight=lightweight")

There was definitely some good things mentioned there...

One thing I'm missing in the lightweight department(not sure why I even do this, my computer is fast enough to handle compiz fusion and all that...) is a network browser.  I try to use Nautilus or Konquerer, but they seem to have tons of dependencies, and running Nautilus even messes with my background and themes and such.

---

### Post by urukrama on 2007-10-23
> **ghandi69_ said:**
> There was definitely some good things mentioned there...

One thing I'm missing in the lightweight department(not sure why I even do this, my computer is fast enough to handle compiz fusion and all that...) is a network browser.  I try to use Nautilus or Konquerer, but they seem to have tons of dependencies, and running Nautilus even messes with my background and themes and such.

To prevent nautilus from drawing the desktop, try running nautilus as
```
nautilus --no-desktop --browser
```

That should work.

---

### Post by mojoman on 2007-10-25
I think K3B use KDE libraries. That's not lightweight in my book. For burning, have a look at graveman or gnomebaker (which, strangely enough, don't use the Gnome libraries).

/mojoman

---

### Post by ghandi69_ on 2007-10-25
Besides nautilus, are they any lightweight browsers out there that feature a network browser??

---

### Post by TeaSwigger on 2007-10-25
> **ghandi69_ said:**
> Besides nautilus, are they any lightweight browsers out there that feature a network browser??

And besides smbc - SAMBA Commander? Ah, might be too light ;)

Hm well the ever quirky Rox-Filer can be extended to browse via FUSE if I recall that right - not sure but I would've seen it at Rox's website if so.

---

### Post by ghandi69_ on 2007-10-25
Ok, I guess it doesn't need to be lightweight, but I would just need to not depend on kde/gnome as much as konquerer/nautilus, only because I like to know whats going on, and when I download those apps, they go crazy on my home directory and start changing things I swear....

---

### Post by Zorael on 2007-10-25
Sorry for not being constructive, but Kamekaze would translate (amongst other meanings) to "turtle wind". :)

Whilst Kazehakase would be "Dr. Wind".

[quote="Teaswigger"]Slightly different meanings and hopefully as different performance[/quote]
Indeed.

---

### Post by mojoman on 2007-11-02
> **ghandi69_ said:**
> 
Video Player - Is VLC the lightest??


I like xine-ui and mplayer is also good. Neither depend on Gnome or KDE libraries.

/mojoman

---

### Post by nutter78 on 2007-11-15
Claws is good 4 email

---

### Post by santiagoward2000 on 2007-11-15
This is my list:
[LIST]
[*]_DE:_ Xfce
[*]_File Manager:_ Thunar
[*]_IM:_ finch :guitar:
[*]_Word Processor:_ AbiWord
[*]_Spreadsheets:_ Gnumeric
[*]_Music player:_ MOC (I like Exile too) :popcorn:
[/LIST]

---

