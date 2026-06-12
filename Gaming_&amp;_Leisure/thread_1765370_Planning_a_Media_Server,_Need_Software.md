---
title: "Planning a Media Server, Need Software"
date: 2011-05-23
forum: Gaming &amp; Leisure
---

### Post by Raditude on 2011-05-23
Hey everyone,

I'm hoping to land a job working on a cruise ship soon. This job will have me away from land and high speed internet for about 8 months straight. Because of this, I have decided I would like to build a Media Server, that will store hundreds of movies and TV shows and thousands of songs.

The idea would be a Linux system with 8TB of hard drive space, HDMI out, and an internal router and wireless router to stream to my MacBook and other devices (say I make some friends on the ship with their own laptops). I'd like to share the movies and music over a wired and wireless network for up to maybe 8 devices. I'd connect the Server to an HDTV to watch movies right from the box.

I am looking for some free open-sourced software that could run this server in Ubuntu. I want it to be able to rip CD's and DVD's, Load DVD covers and Album Art, and a way to tag each movie with things like actors, director, genre, theme, nudity, etc. 

Then when connected to the TV, I want to be able to use an iTunes like interface to select movies and on the clients with a web browser, be able to search and select movies and songs to stream.

---

### Post by mastablasta on 2011-05-23
you mean something like [http://www.mythbuntu.org/](http://www.mythbuntu.org/)?
 
it would probably be mythTV and normal ubuntu server for what you need.
 
and why not post this question in another part of forums (e.g. multimedia)

---

### Post by Raditude on 2011-05-23
That sounds good except for this:

> 
**  I have no interest in recording TV but I wish to use Myth as a music/video jukebox. Is this possible? **

 No. Myth has two plugins called [MythMusic]("http://www.mythtv.org/wiki/MythMusic") and [MythVideo]("http://www.mythtv.org/wiki/MythVideo") which can be used to handle audio and video libraries, respectively. However, [mythfrontend]("http://www.mythtv.org/wiki/Mythfrontend") requires a running [mythbackend]("http://www.mythtv.org/wiki/Mythbackend") to connect to, and [mythbackend]("http://www.mythtv.org/wiki/Mythbackend") requires at least one properly configured capture card. 
 

[http://www.mythtv.org/wiki/Frequently_Asked_Questions](http://www.mythtv.org/wiki/Frequently_Asked_Questions)

---

### Post by thatguruguy on 2011-05-23
If you download a full mythbuntu install (which you can get at [mythbuntu.org]("http://www.mythbuntu.org/")), you can install the backend and frontend on the same machine.  If you're not going to use it as a dvr, or when you go out to sea, you can set up a "dummy" tuner.  Details on setting up a "dummy" tuner are available [here]("http://www.mythtv.org/wiki/Dummy_Tuner").

---

