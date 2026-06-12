---
title: "Notes taking application for Ubuntu, Android (and possibly WM6.1)"
date: 2011-08-24
forum: Desktop Environments
---

### Post by RikoW on 2011-08-24
Dear all,

I'm looking for a note taking application available for Ubuntu and Android so that I can keep my notes in Sync on both devices. Best would be to have also have a WM6.1 client as well, since I sometimes use my old SE X1.

The notes should be stored locally on the devices, so that no online access is needed. Copy files/folders back and forth for example using rsync would not be a show-stopper.

I looked at Evernote which has client for all platforms. However it requires registration and note are stored online I assume. So that's not what I want. OK, Evernote does not have a Linux client, but runs under wine, and there is an open source clone called Nevernote.

Did anybody come across something like that?

Thanks and cheers,

                  Riko

---

### Post by fmjrey on 2011-08-24
I'm also after a similar solution and playing with various apps. I haven't found the ideal application, each app has its own angle, so I may use more than one. Here's what I'm looking at:

[FreeNote]("https://market.android.com/details?id=com.suishouxie.freenote"), a proprietary android app for handwritten notes. Very well made, suitable for quick note entry. Because it can act as an image file/gallery provider, it can be integrated with other android apps when they request an image/file.

[Shuffle]("http://code.google.com/p/android-shuffle/"), an open-source android app for [GTD]("http://en.wikipedia.org/wiki/Getting_Things_Done"). Syncs to [Tracks]("http://www.gtdify.com/"), an open-source [rails]("http://en.wikipedia.org/wiki/Ruby_on_Rails") app for [GTD]("http://en.wikipedia.org/wiki/Getting_Things_Done") that can be installed locally (easier with [bitnami]("http://bitnami.org/stack/tracks")) or used directly as a web service on [GTDify.com]("http://www.gtdify.com/"). It's not really a note application, but a task manager, but I figured one could create a project named "Notes". No file/image attachment is possible, so no handwritten notes possible. I'm considering it for task management essentially.

[Thinking Spaces]("http://www.thinkingspace.net/"), a proprietary android app for [mind-mapping]("http://en.wikipedia.org/wiki/Mind_map"), which can use a file format compatible with some open source and proprietary mind mapping software such as [Freemind]("http://freemind.sourceforge.net/") and [Xmind]("http://www.xmind.net/"). Better suited for brainstorming, exploration of ideas, and not for keeping notes.

[Catch.com]("https://catch.com/learn-more/mobile/") produces a set of android applications which sync with their online service. There's no desktop application, you need to use their web application, which means no offline access to notes on desktop. It's proprietary and only offer 70Mb of online storage for free, but their api and approach is well thought-out and already yields multiple types of applications. Support attachment of images, voice notes, etc. Notes are private by default, and when public you need the unique url to view it. 

I've seen people talk about [Memento]("http://luckydroid.com/") used as an android GTD app. Looks like a promising app, simple database can be quickly made for anything really. Syncs to google docs, so some online desktop editing is possible.

Hope that helps, let us know what you end up with.

---

### Post by RikoW on 2011-08-25
Thanks for your thoughts!

So far it indeed seem like Evernote would be the best choice. Maybe I'll bite the bullet after all and try it out. I'll wait some more, maybe somebody else has some tips, too.

So far on the desktop I use the ZIM Desktop Wiki since some time after using Basket, Tomboy, Gnote before. On my mobile devices I just use the 'build-in' notes function, which of course means 3 different set's of notes ... not ideal.

I'll report back.

Cheers,
     Riko

---

### Post by Frogs Hair on 2011-08-25
This may help .[http://en.wikipedia.org/wiki/Comparison_of_notetaking_software](http://en.wikipedia.org/wiki/Comparison_of_notetaking_software)

---

### Post by RikoW on 2011-09-08
OK, after doing some toying around, I settled for [Evernote]("http://www.evernote.com/") for now.
The real show-stopper was for me was, that I'd like to be able to also get the notes on my by now ancient X1 with WM6.1. 

Even using MS OneNote (which I have running under CXoffice or a virtual machine on my Ubuntu laptop) didn't do the trick since it can only handle one (mobile) notebook and splits up the existing note in smaller chucks. Didn't like that.

So, [Nixnote]("http://sourceforge.net/projects/nevernote/") for the Linux desktop and the corresponding Evernote clients for Android and WM6.1 are my current constellation. Only drawback is that the WM6.1 client needs to be online to access the notebooks on the Evernote server. Not really what I wanted, but the next best thing I could find.

So far so good! If in the future I come up with a different solution, I try to remember to update this thread.

Cheers,
             Riko

---

