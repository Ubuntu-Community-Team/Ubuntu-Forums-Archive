---
title: "Multiple cd installation"
date: 2009-04-05
forum: General Help
---

### Post by Randomness6454564 on 2009-04-05
I'm trying to install a game made for windows using Wine that has multiple cds and when during the installation process it asks me to insert the second cd. but when I press the button to open the disk tray, I get a message saying that a program is preventing me from unmounting the disk. I restart the installation process but this time I put disk two in the other cd drive with the first disk in the first cd drive. Sure enough, it works. Then it asks for me to put the third cd in and I can't get either tray open. Even when I exit the installation process, I still can't open the tray and I have to restart the computer. Is there a solution? Thanks!

---

### Post by mc4man on 2009-04-05
There are a couple of ways
Some people find that opening a terminal and going this will work
```
wine eject
```

What i do is run the install like you would on windows
To do that check in winecfg (app. menu -> wine -> configure wine) under the drive tab to get the letter for your drive (typically D or E

Then browse the first disc for the name of the install file

Ex.
 Drive is D and installer is setup.exe

```
wine D:\setup.exe
```

When asked for disc 2 the eject button on the drive will work, same for disc 3

When done this way you're assured that wine maintains the correct path, though either way should work

---

### Post by Randomness6454564 on 2009-04-06
I would like try your suggestions but unfortunately the computer is on the fritz. When I start the computer, The normal ASCII screen looks jumbled with many extra characters. It looks really bizarre. I tried to record it but since I don't have the hardware to record the start up screen I pointed the camcorder at it. But since the camera isn't digital, I had to transfer the recorded video using the RCA yellow and white output on the camcorder. But since the software for the capture device isn't working I had to record the camcorder fold out screen with a digital camera in movie mode (I'm lucky the digital camera was working since it has been on the fritz lately as well. The language reverts to German and the date to Jan 1 2005 when it is turned off and sometimes wont turn on.) But since the recording of the fold out screen was too blurry, I had to go to the eye piece. As it turns out, it wasn't really any clearer and gave the video a weird green tint. But it's too late, I already recorded it. I wanted to edit the video but since the software I use isn't working, I had to post the video unedited. So around the 33 second mark it sort of hangs there for a bit. So now the train wreck:

[http://www.youtube.com/watch?v=vomkAvu63Oc]("http://www.youtube.com/watch?v=vomkAvu63Oc")

The video kinda creeps me out. It's the video you would use in a scary movie (to scare nerds I suppose: "The Linux computer that wouldn't start!")

I plan on just taking the hard drive out and hooking it up to this computer. Then try to salvage some data, format the thing, put it back in the computer and install Ubuntu. I really hope it's not a hardware issue. Thanks!

---

### Post by Randomness6454564 on 2009-04-06
The computer did start and I got to the desktop. But then it restarted itself. I tried again and saw some weird results:

[http://www.youtube.com/watch?v=9PKpUVKtCRE]("http://www.youtube.com/watch?v=9PKpUVKtCRE")
[http://www.youtube.com/watch?v=UPeodrRQacg]("http://www.youtube.com/watch?v=UPeodrRQacg")

---

