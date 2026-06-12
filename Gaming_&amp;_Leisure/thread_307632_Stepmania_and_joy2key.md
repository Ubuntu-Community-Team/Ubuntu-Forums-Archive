---
title: "Stepmania and joy2key"
date: 2006-11-26
forum: Gaming &amp; Leisure
---

### Post by Luggy on 2006-11-26
I got stepmania running on edgy and am borrowing a dance pad from my roommate. The dance pad is for the playstation 2 so I'm also using one of his PS2 to USB adapaters. I get the whole shabang running and it works, well sorta...

The arrows ( up down left right ) are synced up to the axis of the dance pad joystick so when you need to stomp on the left and right arrows you only end up hitting one of them ( because you can't be in opposite directions of one the same axis at a time ).

Sooo I've been trying to use joy2key to remap the joystick axis to keyboard outputs but I can't seem to get it to work. Every time I try to run it say
```
joy2key -buttons a

```

I get the message
```
Must specify a target first!

```

I can't figure out how I'm supposed to get it to work. I'd really appricate it if anyone could help. I know a bunch of people here play stepmania and I'm sure they encoutnered this problem.

---

### Post by anacron on 2006-12-07
I don't know about your adapter, but mine has "dancepad mode" which can be enabled by holding up, select and start at the same time for about 3 seconds, this is quite normal problem with dancepads universaly (and easy to find with google too ;) ), so I suggest trying to do this before mapping buttons differently... also be sure to disable "automatic mapping" thingie from stepmania options, because it ruins your button bindings every time you start it with dancepad...

---

### Post by rune_kg on 2007-01-13
check-out: man joy2key

you need to specify X/console/rawconsole as target. Also you probably need -dev /dev/input/js0 as input device. So something like:

joy2key -dev /dev/input/js0 -X -axis [axis here separated by blank space] -buttons [buttons here separated by blank space]

should get you going:)

Rune Kaagaard
[http://runelyd.dk](http://runelyd.dk)

---

