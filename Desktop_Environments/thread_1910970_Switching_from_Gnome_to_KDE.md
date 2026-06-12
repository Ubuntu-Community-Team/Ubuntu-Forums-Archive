---
title: "Switching from Gnome to KDE"
date: 2012-01-18
forum: Desktop Environments
---

### Post by hartz on 2012-01-18
Good day all.

The current mess which is Gnome made me take the plunge to re-look at KDE after an absence of ... many many years.

So far I like it very much, I won't go back to Gnome even if it .... well, stops being Gnome.  I do have some issues with KDE - particularly plasma keeps on crashing regularly.  My MS Windows VM keeps giving errors (Windows explorer stopped working), but I suspect that that is not related, etc.

But KDE feels good, looks good, seems stable.

I have two questions for replacements of the applications I'm used to using under Gnome:  I am looking for a replacement for Deluge as well as a replacement for Tomboy Notes.  Right now I am steering clear from GTK based applications (I don't want to get the GTK libraries on my computer now, though I may change my mind about that in time)

For Tomboy I will be able to do something manually if I have to.  I have 137 notes that I want to be able to access quickly, and this list keeps growing every week as I seldomly delete anything at all.

Deluge has got some Torrents which are comming in very slowly and which I've been working on for months, some very rare software which was taken off the market when a company bough another company.  The software used to be free, so nothing illegal, the new company just doesn't distribute it any more.  Some seeders do pop up for this software ocassionally, but it has been a slow and painfull process and most of those CDs are between 40% and 70% completed.  I do not want to lose this effort, I want something which can resume the downloads from where "Deluge" left off.

I'm considering looking at installing Deluge with a Web based interface as a temporary solution.  Ktorrent seems good enough but I'm open to recommendations.  Maybe there is a way to make Either Ktorrent or another torrent application resume where deluge left off?  If all else fails I'll have to create a VM just to run Deluge!?

For what it is worth, I used to have the KDE / QT libraries installed with Gnome, particularly for K3B.  I don't think anything else comes close to K3B for CD/DVD burning right now.

---

### Post by hartz on 2012-01-18
Sigh.  I just noticed that something has already started pulling in some Gnome libraries!!!!  Not a lot, but no longer am I GTK free.  I guess it might have been be Bluefish.

Oh well.

I'd still like to find as many KDE native solutions as possible, even if just as a matter of principle, maybe to conserve memory (loading only one set of libraries as far as possible), and to eliminate incompatibilities.

Oh, and it seems Gnome program GUIs look much worse on KDE than KDE programs on Gnome!

---

### Post by kellemes on 2012-01-18
Personally I use what works best for me.. don't care how it looks or what library it uses.. it simply should work.
I have a bunch of apps installed using all kinds of libraries.. made for different environments, using Xfce..

I guess the most featurefull (QT/KDE) notetaking app is [Basket Note Pads]("http://basket.kde.org/index.php")..
Eventhough I use [KeepNote]("http://keepnote.org/") myself.

If you're happy with Bluefish.. keep using it, it's a killer app. If you still need a QT/KDE alternative you can look at [Kate]("http://kate-editor.org/"), afaik it's the standard programmers-editor for KDE.. nice editor as well.
I use [Geany]("http://www.geany.org/") myself.

Don't know about the torrent-stuff..

---

### Post by Lars Noodén on 2012-01-18
Ktorrent works.  I've used btpd a lot in the past, but it is more difficult to set up.  You might also look at Transmission.  I would expect that any bittorrent app would be able to read the existing torrents and work to complete them.  You could copy them to a new directory and give it a try to see for sure.

---

### Post by tkabir11 on 2012-01-18
> **kellemes said:**
> Personally I use what works best for me.. don't care how it looks or what library it uses.. it simply should work.
I have a bunch of apps installed using all kinds of libraries.. made for different environments, using Xfce..

I guess the most featurefull (QT/KDE) notetaking app is [Basket Note Pads]("http://basket.kde.org/index.php")..
Eventhough I use [KeepNote]("http://keepnote.org/") myself.

If you're happy with Bluefish.. keep using it, it's a killer app. If you still need a QT/KDE alternative you can look at [Kate]("http://kate-editor.org/"), afaik it's the standard programmers-editor for KDE.. nice editor as well.
I use [Geany]("http://www.geany.org/") myself.

Don't know about the torrent-stuff..


I've been looking for some good note-taking alternatives for KDE too- and both of your suggestions look great :) Will try them out both.
And OP- why not try Vuze for torrents?

---

### Post by 4Foot on 2012-01-18
> **Lars Noodén said:**
> Ktorrent works.  I've used btpd a lot in the past, but it is more difficult to set up.  You might also look at Transmission.  I would expect that any bittorrent app would be able to read the existing torrents and work to complete them.  You could copy them to a new directory and give it a try to see for sure.

hartz:

Ditto on using Ktorrent, it works a treat and most torrent sites recommend it. If you kept the original torrent file all you have to do is put it in Ktorrent and point the program to the directory where the downloaded files are and it will rebuild the index for you.

I am currently using Ubuntu on my laptop and Mint on my desktop and just like you am sick of the desktop mess that Gnome has become. Thanks for your thought on KDE I am planning to emulate your move.

Happy Trails
:)

---

### Post by oldos2er on 2012-01-18
> **tkabir11 said:**
> I've been looking for some good note-taking alternatives for KDE too- and both of your suggestions look great :) Will try them out both.
And OP- why not try Vuze for torrents?

I use Basket for note-taking, it's in the repositories. Having never used Tomboy, I can't tell you how it compares, but Basket is very feature-rich in my opinion. Also it can import Tomboy notes.

[http://basket.kde.org/](http://basket.kde.org/)

---

### Post by schnelle on 2012-01-18
Torrent app: Qbittorent (pure Qt app) 8-)

---

### Post by hartz on 2012-01-19
> **oldos2er said:**
> I use Basket for note-taking, it's in the repositories. Having never used Tomboy, I can't tell you how it compares, but Basket is very feature-rich in my opinion. Also it can import Tomboy notes.

[http://basket.kde.org/](http://basket.kde.org/)

I decided to try out basket and it seems quite good, possibly even over-kill.  It in fact has got an import function for Tomboy, but when I clickthebutton it appears that nothing happened.  So I went ahead, installed Tomboy, and am in the process of copy-pasting my notes in one by one (I tried importing th notes as text but they aren't plain text, it is XML and tomboy specific.

Regarding torrents, ktorrent has done a remendous job of just working!  I put my half-done torrent data into the default work dir for ktorrent, re-added the .torrents and it right-away started to scan to see if the existing content was valid.  Perfect for what I needed (but for some reason was afraid to just try)

Now... I still want a replacement for "shutter" (something I forgot about previously) ....

---

### Post by Lars Noodén on 2012-01-19
> **hartz said:**
> ...Now... I still want a replacement for "shutter" (something I forgot about previously) ....

If shutter is a screen shot tool, then ksnapshot would be the equivalent in KDE.

---

### Post by hartz on 2012-01-24
> **Lars Noodén said:**
> If shutter is a screen shot tool, then ksnapshot would be the equivalent in KDE.

Yes it is a screenshot tool.  If you take more than just the ocasional screenshot though then should look at shutter.

It does not have an equivalent, in any case none that I've found so far.  For now I will stick to it, even under KDE.

---

### Post by cespinal on 2012-01-24
Are you using kubuntu? try to go for the final KDE 4.7 updates that went live yesterday.

The system feels completely solid.

---

### Post by hartz on 2012-01-26
> **cespinal said:**
> Are you using kubuntu? try to go for the final KDE 4.7 updates that went live yesterday.

The system feels completely solid.

I've been running 4.7.97 (Which is 4.8 RC2) for a few days and it is much much more stable than 4.7.3

I had a single crash so far, plasma threw up.  I'll be updating to 4.8 GA soon.

---

### Post by cespinal on 2012-01-26
Made the update to 4.8 last night. Muon hanged in the first attempt. Then I got it right. 

Everything seems to be ok now. The only problem that still persists from previous versions is that Rekonq crashes plasma for some reason. I use Chromium instead.

---

