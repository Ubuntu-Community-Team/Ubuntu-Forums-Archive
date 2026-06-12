---
title: "Making a linux DVR server."
date: 2009-05-17
forum: General Help
---

### Post by Dvorakis on 2009-05-17
ok, so heres the deal. My girlfriends brother(who is an IT) recently got a me a brand new computer, 2 actually...but one of them I use. It currently has one hard drive installed, and once I figure out weather or not I want windows 7 or XP on it, im going to partition it with linux and ubuntu.

But thats not the point, the computer came with a WinTV card in it, and I really want to put it to use, but this computer runs REALLY hot, so im planning on putting it in my old machine(which runs like a freezer constantly,it has like...9 fans), and running that machine as an ubuntu DVR like server thingy. Probobly using something like myth tv.Then I can proceed to run the videos off of the server on my new computer. The only problem is, I have no idea how I can accomplish this...any tips on a setup, what do you think is the best?

Thanks a bunch! If you need more info,just ask.
Dvorak

---

### Post by mb_webguy on 2009-05-17
My suggestion would be to [start reading]("https://help.ubuntu.com/community/MythTV").  There are different issues involved in setting up a MythTV box depending on the type of television you get (e.g. cable with no box, cable or satellite with a box that you can control directly from the MythTV box using something like a firewire connection, cable or satellite with a box you have to control with something like IR blaster, etc.).  It's not necessarily difficult, but it's too broad a topic to be able to address in a simple forum post.

---

### Post by Dvorakis on 2009-05-17
Well what I was wondering for the most part was,How can I connect computers so that I can record with the linux box, and find the files on the other?

How can I make a connection between the two computers?

---

### Post by mb_webguy on 2009-05-17
As far as sharing the media, starting with v0.20 MythTV includes a UPnP mediaserver, so to access your media on the DVR box, you'd just need a UPnP client.  On Windows, you can use Windows Media Player (among other things) to access the media.  On a Linux box, you can use Totem (with the [totem-plugins-extra]("apt://totem-plugins-extra") package), [djmount]("http://djmount.sourceforge.net/") (which allows you to use any media player to play the shared media), or [XMBC]("http://xbmc.org/") (which is both a UPnP server and client).

A simpler but perhaps less elegant solution would be to simply share the media directories using Samba.

Of course, you'll have to have a router to network the computers, no matter how you go about sharing the media files.

---

