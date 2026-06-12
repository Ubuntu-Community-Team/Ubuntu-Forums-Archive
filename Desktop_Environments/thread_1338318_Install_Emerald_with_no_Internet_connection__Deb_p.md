---
title: "Install Emerald with no Internet connection?  Deb package?"
date: 2009-11-26
forum: Desktop Environments
---

### Post by ssouthparkk on 2009-11-26
I am going to someone's house for Thanksgiving later, and I am going to load Ubuntu onto their machine with the CD.  I know Compiz is on it, but not Emerald.

If I get the Deb package on a flash drive, will there need  to be dependencies?

They have no Internet.

---

### Post by mac9416 on 2009-11-26
Howdy!

You will need to get the dependencies for Emerald along with the main .deb file.

Probably the best option is to use [Keryx]("http://keryxproject.org"). With Keryx, you create a project on the offline computer, then take it to your online computer to download packages. It looks and acts much like Synaptic, except it is portable and cross-platform.

You'll want to read the Keryx tutorial before going on: [http://crashsystems.net/2009/01/keryx-tutorial/](http://crashsystems.net/2009/01/keryx-tutorial/)

But there is one problem: if you were installing Jaunty, you could download the Emerald .debs using Keryx's Jaunty "default project" (designed to mimic a fresh installation). However, we in the development team have been so busy we haven't created a Karmic default project yet.

Here is the workaround: when you download Keryx and extract it onto your flash drive, you will need to modify the Jaunty default project to act like Karmic. Go to the "projects/jaunty-32-bit-default/sources" folder and open the sources.list in your favorite text editor. Replace each instance of "jaunty" with "karmic" and save the file. Now you can start Keryx, load the modified jaunty default project, and download the Emerald .debs.

When you get to the friend or family member's computer, be sure to create a project on that computer in case you need to get .debs for them in the future.

I know it's a lot of hassle, but once you get that project created on their computer, it's smooth sailing.

Good luck, and happy Thanksgiving!

PS: I will work on that Karmic default project this afternoon.

---

### Post by ssouthparkk on 2009-11-26
I will look into that right now, and will report back. ;)

---

### Post by ssouthparkk on 2009-11-26
Worked!

I tested it on my PC first, I have yet to actually do what I set out to, but I know that if it fails, it isn't your project, because it works.  You have a good thing going, keep it in development. :)

---

