---
title: "How to move (pic) files from a camera? [I use Kubuntu 6.06]"
date: 2006-07-18
forum: Desktop Environments
---

### Post by kentl on 2006-07-18
Hi!

I'm using a Canon PowerShot A520 which I connect with my computer through USB. When I connect it its detected as "Canon Digital IXUS 50 (normal mode)" and I can see it in Konqueror at "system:/media/camera".

I have installed Picasa using the guide instructions and if I choose Import when the camera is connected I'm able to select the detected camera. It then fetches a preview of all the images and I select "Import all". Here comes the problem, it transfers around 80 pictures and then it freezes with the transfer window open.

Is there another way to get my pictures? I can't click the camera in Konqueror and copy my pictures. What I would like to do is mount the camera somehow so that I may move my pictures from the camera to a folder on the computer (which I then will import from using Picasa).

All suggestions greatly appreciated! I really need to be able to retrieve the pictures from my camera and I don't want to go back to using Windows.

---

### Post by snaga on 2006-07-18
Not sure what kind of media that the cannon uses, but if you have a card reader for that kind of media, you should be able to retrieve the pictures. Thats what I have to do with mine. I have had trouble with Picasa as well.

---

### Post by fragos on 2006-07-18
If I'm not mistaken, the Canon can be mounted as removable media.  SuSE and Ubuntu treated my Canon that way.

---

### Post by palsyboy on 2006-07-19
As snaga says, it's all about a card reader.  I've never used any of my digital cameras with an OS directly, even when I used to run Windows.  [Here's](http://www.newegg.com/Product/Product.asp?Item=N82E16820163601) a cheap reader for your A520 (I have the same camera, btw).

You could also try the cp command to move the pictures and then chown your home directory to make sure you own them.  It's my experience that GUIs crash during file transfers, but the CLI is rock-solid:
```
sudo cp -Rv /media/camera/ /home/kentl/
sudo chown -R kentl /home/kentl
```
They should be there.

---

### Post by kentl on 2006-07-19
> If I'm not mistaken, the Canon can be mounted as removable media. SuSE and Ubuntu treated my Canon that way.
Did you do anything special to be able to mount it? (I'm new to linux)

When I insert it I get the USB Imaging Interface dialog saying "A new media has been detected. Type: Camera. What do you do? Open in new window / Do nothing". If I choose Open in new window I get the top window in my example below. It says that I have an "Canon Digital IXUS 50" which seems wrong. If I click the camera icon one I get the second from top window, and if I click it a third time I get the window displaying an error message saying "Bad parameters".

[CENTER][CLICK HERE FOR EXAMPLE]("http://thisistheurl.com/file/camera-trouble.png")[/CENTER]

> You could also try the cp command to move the pictures and then chown your home directory to make sure you own them. It's my experience that GUIs crash during file transfers, but the CLI is rock-solid:

See above for what happens. I've included the CLI log as well in that picture. If it is possible I would like it to work without a card reader, as I'm a poor student. It worked very nicely in Windows, just plug it in and off you go. If there is any way to get it working in Linux without a card reader I would be happy.

Notice that Picasa can transfer some of the pictures (around 80 out of 200), so there is some kind of connection. At least through Picasa.

---

### Post by Delkster on 2006-07-19
Just out of curiousity, have you tried for example DigiKam?

---

### Post by kentl on 2006-07-19
DigiKam works! At first I thought that it wouldn't work, as KDE incorrectly identified my camera as an "Canon Digital IXUS 50 (normal mode)" which was what was added if I choose "Auto-Detect". That did not work.

I then manually selected "Canon PowerShot A520" from within DigiKam when I added the camera. And viola it worked!

When I used Picasa I had no other option than the auto detected camera (the IXUS) from KDE.

The problem is identified. KDE detects my camera wrongly. I can not resolve it by manually adding the correct camera in System Settings / Digital Camera either. When I try the added camera won't give information or test successfully.

Is this a bug in KDE? Should I report it somewhere? Any ideas on how to resolve it?

---

### Post by kentl on 2006-07-21
Anyone?

---

### Post by palsyboy on 2006-07-22
I know this isn't the answer you're looking for, but I'll toss it out there, anyway.  The simplest way around all of this is to buy a card reader.  Here's a rant I wrote on justlinux.com:

Don't connect your camera directly to your computer. Instead, get a card reader that plugs in via USB. There are numerous reasons for this: For one, uploading photos costs battery life, so you'll have to recharge more often. Second, if you take pictures at friends' houses, etc., and they want pictures, you can give them copies right then & there. Or if you run out of storage on the card itself, you can back it up to a friend's computer; the same applies if you're on vacation and have a laptop. Essentially, though, if you have Windows or Mac-using friends, and they want pictures or want to borrow your camera, etc., they can use the card reader and not have to install new software on their system to interface with the camera. For a portable card reader, there's always stuff like this. And for regular use with your own computer, it's all about internal card readers.

For approximately ten bucks shipped, you can't beat a card reader to save yourself some headaches while simultaneously adding versatility.  Even on a tight budget, the one I listed earlier should be attainable.

---

### Post by kentl on 2006-08-06
You are right that it's not the solution I'm looking for. It's good as a fallback and it's nice to hear that it works very well.

However I'm more interested in getting the camera to work with KDE as it's supposed to. As KDE has it in it's list of detectable cameras but still can't detect it I consider it a bug. If the bug is strictly KDE-related or is caused by something in the distribution is impossible for me (with my limited knowledge) to tell. I'll file a bug report as soon as possible, right now I'm the middle of some exams at the university so I'll have to focus on them.

The best thing for KDE, Kubuntu and Linux in general is if stuff works as well as they do in Windows. When I ran Windows XP Pro. the camera was successfully detected and everything worked nicely out-of-the-box. I'd like it to be as smooth in the future for me and others as well.

That said Digikam works very well! So I'm not in a hurry to get the issue fixed. Thanks for your reply!

---

