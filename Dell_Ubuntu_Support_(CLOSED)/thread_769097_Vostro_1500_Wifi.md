---
title: "Vostro 1500 Wifi"
date: 2008-04-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by StefAndrew on 2008-04-26
My laptop has the Dell wifi card in it. And I can't seem to make a connection of any kind. I don't see any networks around me in roaming mode, and I can't manually connect to anything either. It used to be that I had to disable ipv6 in 7.10 and it would work perfectly, but with 8.04 nothing seems to be working.

---

### Post by esteckis on 2008-05-03
Check under system administration "Hardware Drivers" and see if you have "Broadcom B43 wireless driver listed.. If you do then enable it. It should download the driver and then later on, it should download the FWcutter.
 which I think is also for the wireless.  I have a Dell 6400 which is suppose to be comparible wise the 1505.

---

### Post by esteckis on 2008-05-03
Also another quick note with setting up the wireless to connect. I can't remember exactly, but I think once you enter your key and if it is a shared key to connect, you have to shut down and restart your sytem.  When I shut down and restarted, a window opened up (Keyring window) and asked for my password. Once I entered the password, the wireless connected.

---

### Post by StefAndrew on 2008-06-11
Well, I finally figured it out.  I've been having trouble with getting the wireless working with the b34-fwcutter because I have been setting up Ubuntu each time not connected to a LAN cable.  So, I finally installed Ubunut with the cable plugged in the whole time and it found and setup fwcutter just fine.  I have noticed it does drop the network occassionally, but I'm just so happy it's working.

So the moral of the story, have an active internet connection when installing on a laptop...

---

### Post by Applecache on 2008-06-25
Hey StefAndrew

I have recently bought a vostro 1500 less than a month ago.

I was sondering how old your laptop is, what make (mines Figustu), what capacity and what speed (rpm).

Why i need this is because i am experiences click click on my hard drive and was wondering what if:

1) i got a new one through the warranty and whether it will the problem will still exist

2) if the problem has been aroung for some time

3) if i have a bad hard drive

PS i have done research and found its an Ubuntu error in power management/ load cycle etc but i wanted to ask someone who has a similar laptop to me.


Thnaks:lolflag:


PS i couldnt get an email contact of you so i am using the forums:)

---

### Post by saru411 on 2008-06-26
a clicking HD is normally a sign of failure. It may not fail soon but it can easily fail without warning. I would recommend contacting the Hd manufacturer and seeing if you can get a replacement. If all else fails HDs aren't very expensive right now.

---

### Post by Applecache on 2008-06-26
I would do that but i have been researching the forums and there is a BIG bug with ubuntu with some users experiencing it and others not. 

The bug is whereby the hard drive heads park and unpark or something like that. they do it too often and there is a limit sucha as a fatigue limit in mechanical shafts etc.

So i was worried about it being that.

If only StefAndrew would get back to me

:confused::confused::confused::confused:

---

### Post by StefAndrew on 2008-06-26
The hard drive actually clicks while running windows, vista, too.  So I'm not sure what the issue is.  I had read about the issue in Ubuntu where HD's are dying because of the fatigue, but I actually haven't been using my laptop much at all the last several weeks.  And I haven't really been too worried.  If the drive does fail, I'll probably just have it replaced with a bigger hd.  Mine is only 160gb.  I want to get a 200gb + drive anyway.

---

### Post by saru411 on 2008-06-27
> The hard drive actually clicks while running windows, vista, too.  So I'm not sure what the issue is.
The issue would be a broken HD.

  > I had read about the issue in Ubuntu where HD's are dying because of the fatigue

This was very common in 7.04 but not 8.04. If your HD is clicking now it's most likely what i have stated.

> If the drive does fail, I'll probably just have it replaced with a bigger hd. 

Just make sure to have back ups of whatever is going to be on that HD. Backups are your best friend in Linux, Windows, and/or any other O/S you happen to be running.

---

