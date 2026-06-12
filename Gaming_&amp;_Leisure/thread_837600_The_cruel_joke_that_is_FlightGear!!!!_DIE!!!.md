---
title: "The cruel joke that is FlightGear!!!! DIE!!!"
date: 2008-06-22
forum: Gaming &amp; Leisure
---

### Post by smartsmokey on 2008-06-22
This program will NOT work properly. I installed everything but Flightgear wizard into Hardy Heron. Then I made a live disc of flightgear. I tried everything to get Flightgear working properly in Heron...but the game starts off with a  172 on the runway, with the screen flicking off for a millasecond every 2 seconds or so, and the size of the window the game is in is half the size of the screen. Tried changing the render option so the runway light problem wasn't interfering - made the game work better, but it's still too small of a window and flickering. Went into compiz and told it not to control full-screen programs so that I can run in full-screen with no conflict. Actually putting flightgear in fullscreen mode? Not possible. Then, when you search the net for commands on Flightgear you can find them, but how the hell are you supposed to enter the commands? What platform? Not terminal. Then I booted by accident from the liveCD of Flightgear I made...and it boots the computer in Puppy, making my normal applications and data just NOT THERE because it booted a different OS! Then I downloaded and installed Flightgear wizard in Hardy Heron. The icon is in the program menu, but when you click on it NOTHING happens. What a friggin JOKE.

---

### Post by inportb on 2008-06-22
Excuse me for asking this stupid question... but have you tried turning off Compiz?

---

### Post by smartsmokey on 2008-06-22
don't know how. The only commands I can see on the net read something like "metacity? compiz --restore" or something. Needless to say, no luck with that.

---

### Post by smartsmokey on 2008-06-22
okay, installed fusion icon to manage compiz. Only thing is it WILL NOT LOAD. I clikc on the icon, and nothing. It's just one  big dead end.

---

### Post by PilotJLR on 2008-06-22
System > Preferences > Appearance > Visual Effects

Then select "None" and Close.

---

### Post by ad_267 on 2008-06-22
You right click on the compiz fusion icon to get a menu.

---

### Post by smartsmokey on 2008-06-22
> **PilotJLR said:**
> System > Preferences > Appearance > Visual Effects

Then select "None" and Close.

Dude you're a saviour. It actually WORKS now! Now all I have to do is figure out what/where this flightgear command interface is because it starts off with the 172 on the runway in a small screen. Can't get it into full-screen, can't get a different airport or plane or anything...just the 172 on the runway at San Francisco. :(

---

### Post by PilotJLR on 2008-06-22
Good!

Check out this:
[http://wiki.flightgear.org/index.php/New_to_FlightGear#Displaying_Available_Aircraft](http://wiki.flightgear.org/index.php/New_to_FlightGear#Displaying_Available_Aircraft)

And also (I think) this command works to run in full screen:
```

fgfs --enable-fullscreen

```

---

### Post by smartsmokey on 2008-06-22
well I can get fullscreen (sort of, just a full-size window, not true fullscreen without the window borders), but still can't change plane, etc. When I typed in the aircraft command it does show me the available planes, but as to how I'm supposed to get a game going with that plane - no clue. I typed "seahawk" and of course got "command line not found." What a load of garbage. So every time I play I have to do like 50 lines of code just to get a game going? For example, fgfs get scnery, fgfs get aircraft, fgfs time, fgfs infinity...........
Too bad flight wizard is a piece of junk that doesn't even run. This sucks.

---

### Post by PilotJLR on 2008-06-22
Ok... I thought the link I sent was clear, but maybe not. I'm not at flightgear at the moment, so let's say "seahawk" is an airplane shown when you listed all the aircraft.
You would then load this plane by:
```

fgfs --aircraft=seahawk

```

That's it... basically put the airplane names in where the work "seahawk" is.

Another recommendation - people will be a lot more willing to help you if you lay off the "this sucks" and "piece of junk" talk. It makes you sound like you're 10 years old.
Which you may be... and that's fine... just take it down a notch.  :-)

---

### Post by smartsmokey on 2008-06-22
oksay aircraft=seahawk(I thinkin that was the command) worked...put me in the cockpit of a skyhawk on the runway. But, when I toggled the 2D cockpit, low and behold I got the 2D cockpit of the CESSNA 172!!!!!!!!!!!! Arghh!!!!!!!!!!!!!!But anyway, I think I might have it down now. I'm not familiar with Linux/command line interface AT aLL...I switched to Ubuntu about a month ago after years of Windows. So far I've been lucky, I have my laptop just how I want it with the apps I want...but it's the stuff like "fgfs--aircraft-get" and stuff that kills me. So, before I start a game in flightgear, I need to change the plane, change the scenery/airport...and I should be good. Now if I can only find the sidewinder joysytick I threw in the closet about 2 years ago when I gace up on the freezes during FS2004.

Thanks for all the help people!!!!!! I would still be at the blinking screen. Now I just need to familiarize myself on how command lines work with games and when to do them and I'm good to go. Ubuntu friggin rocks. So do you people.

---

### Post by PilotJLR on 2008-06-22
Good to hear! Sounds like a good step forward.

The flightgear wiki / manual is a nice place for extra info on it. 

Also - I recall that the Harrier is a really nice airplane in flightgear, though it's also more difficult to fly.

---

### Post by smartsmokey on 2008-06-23
> **PilotJLR said:**
> Good to hear! Sounds like a good step forward.

The flightgear wiki / manual is a nice place for extra info on it. 

Also - I recall that the Harrier is a really nice airplane in flightgear, though it's also more difficult to fly.

A Harrier would be cool, though I'd probably spend 20 mins doing command lines in order to get it going only to get 20feet off the ground and stall. Yeah, there's tons of add-ons...almost any plane/place you can imagine, and then some. I think the whole Linux/Ubuntu thing is the tough part. After I'm familiar with command lines I'll be golden. Maybe I can find a book at the coop today - perhaps in a few days I'll be creating my own planes and scenery. I can't thank whoever made Ubuntu enough. If there was a class on Ubuntu at school I'd celebrate.

---

