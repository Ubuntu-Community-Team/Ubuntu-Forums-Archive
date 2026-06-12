---
title: "Can't paste OpenOffice graphs into other programs"
date: 2009-02-12
forum: General Help
---

### Post by Mander on 2009-02-12
I've seen several things related to copy-paste and OpenOffice, but they all seem to invovle a clipboard manager (klipper, glipper, etc) and closing OpenOffice before trying to paste into something else.

I have some graphs I've made in OpenOffice Calc that I wanted to paste into some other image editing program (e.g. GIMP) because I want to trim off extra white space that I can't seem to get rid of in Calc.  But I can only copy and paste the graphs between OpenOffice programs.  If I try to paste them into GIMP, inkscape, GNU Paint, etc nothing happens.

Is there a fix for this somewhere?  

I'm still using 8.04, by the way.

---

### Post by SamNSane on 2009-02-12
I'm not going to pretend that I know much about this. Your post merely prompted me to try copying a graph created in an OpenOffice spreadsheet and pasting it into Gimp. It worked.

Maybe you should list which version of OpenOffice you're using (I'm using 3.02 under Hardy Heron.), how the graph was created / what its dimensions are, and how you are selecting / copying / attempting to paste it. Maybe someone will be able to figure out from that what the problem is.

---

### Post by Mander on 2009-02-13
Sorry for the lack of detail!

I'm using OpenOffice 2.4.1, under Hardy.  I haven't tried to upgrade to Office 3.0 yet.

The graphs in question are ordinary bar/pie charts, created from a small table of numbers in Calc.  I have made at least 20 of them for different aspects of my research and have made them all a standard size of 12x6 cm.  They are all black and white, no fancy colors or 3-D or anything like that.

Perhaps I should try to upgrade OOo?

---

### Post by SamNSane on 2009-02-13
So when you attempt copy & paste you just highlight the cell range which contains a graph, hit <Ctrl>-C, switch to Gimp (for instance), and paste into an already-created bitmap or into a new bitmap? That works for me with OpenOffice 3.01 in Hardy.

I have no idea whether or not upgrading to OO 3.01 would fix the issue for you. I might also be using a later version of the Gimp, version 2.6.2 (from GetDeb).

The 2.4 version of OpenOffice included in the standard Ubuntu repositories is said to be the "GoOO" version, which is supposed to incorporate many of the changes in version 3.0.

If you decide to upgrade OO, I strongly suggest using the Launchpad PPA repository and key for the installation so that your OpenOffice installation will continue to get important updates

[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

That link is the location for the PPA for the OpenOffice Scribblers  repository. There are instructions there as to how to add the repository and its authentication key to your Software Sources applet. It's the easiest / safest way to get OO 3.x in Hardy, I think.

But I'd really like to see if someone more conversant with the way the clipboard / desktop integration works can figure out what's going on with your system. I kind of take copy & paste for granted in about any operating system these days. Having it NOT work is kind of worrisome. I'm leery of installing more / later software on a system that might not be functioning properly in the first place.

Or it could be that I'm just being an overly cautious old ninny.

:D

---

### Post by Mander on 2009-02-14
Well, I think I am more inclined to not try and upgrade, myself.  

The GIMP version I have is 2.4.5, whatever is in the Hardy repository.

I just tried it again and no dice.  If I highlight a graph or chart, it doesn't work, even if I create a file in GIMP first and paste it.  If I copy some text, though, it does.

It must be related to the other bug, but I thought it only affected people using Glipper.

---

### Post by SamNSane on 2009-02-14
Well, if you get desperate enough to try version upgrades for OO and Gimp, I can tell you that I've done those particular upgrades (the Launchpad PPA for OO and the GetDeb for Gimp) on three heavily used office systems with no ill effects. I don't just go grabbing random updates for the heck of it, but the apps we use heavily are, I think, worth keeping as up-to-date as possible.

On the other hand, if your present version of OO and Gimp suit your needs, you should probably stick with them. I have a hard time believing that updating them will fix this problem. I just noted the differences in versions in an attempt to provide complete information about differences in our systems.

I intend to look around for information on this later today because a friend in another city says she has run into this issue before -- in Intrepid, though. I've never seen any kind of trouble with copy & paste in Ubuntu, other than the somewhat annoying convention of losing the clipboard contents when closing the app from which they were copied. I think I understand the reason for it, but I think it's an example of extreme conservatism where it probably isn't warranted -- leastwise, not for conserving resources. Most systems these days aren't hampered by carrying a little dross around on the clipboard. Or maybe I misunderstand the devs' reasoning.

---

### Post by 73ckn797 on 2009-02-14
I use OO3.0 & Gimp 2.6 in Ubuntu 8.10.

I can create a pie chart in OO, right click on the chart and select copy, open Gimp to a newly create empty doc and simply paste into Gimp.

---

### Post by SamNSane on 2009-02-14
> **73ckn797 said:**
> I use OO3.0 & Gimp 2.6 in Ubuntu 8.10.

I can create a pie chart in OO, right click on the chart and select copy, open Gimp to a newly create empty doc and simply paste into Gimp.

Hmmm. Now I'm beginning to wonder if the version of one app, or the other, or both may have something to do with the issue after all. Weird. I'd think it would be more likely to be an issue with the desktop environment itself.

---

### Post by SamNSane on 2009-02-14
Hi, **Mander**. In your research of this problem, have you come across [DDM]("http://data-manager.sourceforge.net/")? I didn't see an Ubuntu package, per se, but there is a .deb package available at the home site. It has features specifically designed for handling image data. Those features, along with what looks like a rather impressive list of general features, might offer something to you.

This, plus the middle mouseclick method of pasting in the X environment (which I haven't even tried yet) were the only two promising finds as I searched for information on this.

The friend I mentioned earlier thinks her problem was solved by the simple expedient of using the middle click. I can't imagine why that would work when right-click paste or <Ctrl>-V or pasting from the target application's own menu system wouldn't work, but I guess you use whatever works for you. I'd hate to think that the Gnome desktop environment (or maybe some of the apps that run on it) is squirrely enough to require a hit-or-miss approach to as basic a function as copy & paste, but whatever floats our boats!

---

### Post by SamNSane on 2009-02-15
I just happened to wonder if my posting a few observations about how (I think) copy & paste works in the gnome desktop environment.

First of all, the copy & paste functions seem to have a sort of split personality about them. I think that may be because so much of how they act is probably determined by the applications from which and to which the data is being copied and pasted.

I have also noticed that a documents like spreadsheets when opened as read-only don't behave at all as well for purposes of copy and paste as they do when they are in editable form. I'm not sure, because I haven't tested, but I think this may also apply to cases where one is trying to copy something from a protected range in a spreadsheet.

I ran into some problems this morning while testing and realized that my issues were being caused by the fact that I was attempting to use a read-only copy of a spreadsheet as the source of the graph to be copied.

Once I started using an editable copy of the spreadsheet I could do two things very easily:

1. If I wanted to copy the actual graph object, I could just click anywhere within the graph body. I could see that the object was selected because the resizing handles and outline around the object appeared along with the anchor. At this point I could crank up OpenOffice Writer and paste the editable graph into a document.

2. If I wanted to copy an image of the graph, the most reliable method to use was to use File -> Preview in Browser from the Calc menu system. When the browser opened displaying the spreadsheet, I just right-clicked on the graph image and selected Copy Image from the context menu. I could then paste the image into a graphics editor like Gimp.

Those two methods, with a non-write-protected spreadsheet, were the only truly reliable methods I found for copying and pasting the graph object (into a WYSIWYG document editor) or the graph image (into a graphics editor).

Does any of that work for you, **Mander**?

---

### Post by Mander on 2009-02-19
I ran across DDM and installed it, but I haven't quite understood how to make it work.  I'll fiddle with that later.

Regarding the other two things mentioned:

Middle click doesn't work, either.  I can still only copy and paste between OpenOffice programs by normal routes (ctrl+c, edit->copy).

Opening the file in the web preview mode does allow me to copy and paste into GIMP.  I never knew that option existed!  Shows what you can learn when you actually look through the menus...

None of these files are read-only, by the way.  I checked to make sure but they are all things that I am actively creating.

So, I think that perhaps the best option may be to upgrade after all.  It just might be a bit of a pain.

---

### Post by SamNSane on 2009-02-19
May I suggest that you test DDM before upgrading OpenOffice and / or Gimp? Some people really swear by it. I don't particularly need its features, having got used to working without the niceties of either download or clipboard managers long ago, so I don't use it. But, since you already have it on your system, you might want to give it a go.

It might also be a good idea to remove DDM before installing the upgrades to OpenOffice and Gimp. I say that more as a consideration for figuring out what solves the problem than for any real concern about issues like conflicts. (I don't believe there would be any.) But I'm sure it would be nice to know what (if anything) actually fixes the problem you're having.

To tell you the truth, I never really noticed a problem with copy & paste when I first moved to Ubuntu and was using the versions that come from the standard repositories.

I'm curious about one thing. When you try to select the graph directly from the spreadsheet, do the object's handles appear on the screen?

Concerning the upgrades themselves, the process isn't even the least bit difficult or dicey.

If you use the launchpad ppa for Open Office ([https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)) all you have to do is add their repository and key to your Software Sources applet. (There are instructions right at the site.)

Using the GetDeb Gimp installer is a littler bit tricker, in that you need all of the following packages (assuming you're using 32-bit standard Ubuntu), which are offered in a list when you search for Gimp at the GetDeb site.

gimp_2.6.2-1~getdeb1_i386
gimp-data_2.6.2-1~getdeb1_all
libbabl-0.0-0_0.0.22-1~getdeb1_i386
libgegl-0.0-0_0.0.18-1~getdeb1_i386
libgimp2.0_2.6.2-1~getdeb1_i386

The thing is that you have to install them in order, dependencies first, then the gimp-data package, then the gimp package itself -- if I recall correctly the order is:

libgimp
libbabl
libgegl
gimp-data
gimp

It's actually easy enough to figure out that I've never actually made notes on the order, and I'm pretty OCD about that sort of thing. You'll see some warnings as you add the packages, and you may have to open a terminal window on one of the items to force and installation to completion. (The installer actually tells you exactly what to type into the terminal window.) But it works, and consistently, without problems. I've done it on 8 systems at the office with nary a problem among them.

I think there may also be a launchpad ppa for a slightly earlier version (but a later one than you have currently) of Gimp, and that would be VERY easy, as with the OpenOffice update.

Whatever you do, I hope it works out well. I'll be hanging around to see how it goes.

---

### Post by Mander on 2009-03-03
> **SamNSane said:**
> May I suggest that you test DDM before upgrading OpenOffice and / or Gimp? Some people really swear by it. 

...

I'm curious about one thing. When you try to select the graph directly from the spreadsheet, do the object's handles appear on the screen?


Just to update, I have installed DDM and I'll see what it can do. 

I do get the handles (the little green boxes, right?) on the graph when I select it to copy.

I haven't messed with upgrading Open Office yet.

---

### Post by SamNSane on 2009-03-03
> **Mander said:**
> Just to update, I have installed DDM and I'll see what it can do. 

I do get the handles (the little green boxes, right?) on the graph when I select it to copy.

I haven't messed with upgrading Open Office yet.

Yeah, I'm not sure that updating is going to get you much of anything. I find that trying to copy and paste a graphic object from OO directly is pretty much hit or miss. I seldom need to do it, anyway. But when I do need to do it, I'm just doing a preview in the browser and getting it from there. That's okay if you only want to use it as a graphic, of course. If it needs to be live-linked back to data in a spreadsheet or database, that's another matter.

I just noticed that the Gimp version that's available in the Hardy backports repository is very close to the latest stable version. It probably makes more sense to use that one, and thus be supported by a repository. In case you decide to update it.

I still recommend the launchpad PPA for the Open Office Scribblers as the source for the Open Office upgrade.

Please come back to tell us how things are working out.

---

