---
title: "Ubuntu synergy client help"
date: 2009-01-16
forum: General Help
---

### Post by MagnusL3D on 2009-01-16
Hello, 

I have 2 computers I want to connect with synergy.

Synergy server is Vista
Synergy client is Ubuntu with dual screen using Xinerama.

Synergy works fine between Vista and Ubuntu, but not on the 2nd screen on ubuntu, and it seems to be because im using Xinerama.

As I understand it there is the "xtestIsXineramaUnaware" option one can include in the servers config file, but since the synergy server is Vista I have no config file and this option as far as I can figure is not visable in graphical interface of synergy in Vista.

So any idea's on how to make synergy work for the ubuntu 2nd screen with a vista as the synergy server ?

/M

---

### Post by veloce on 2009-01-22
> **MagnusL3D said:**
> Hello, 

I have 2 computers I want to connect with synergy.

Synergy server is Vista
Synergy client is Ubuntu with dual screen using Xinerama.

Synergy works fine between Vista and Ubuntu, but not on the 2nd screen on ubuntu, and it seems to be because im using Xinerama.

As I understand it there is the "xtestIsXineramaUnaware" option one can include in the servers config file, but since the synergy server is Vista I have no config file and this option as far as I can figure is not visable in graphical interface of synergy in Vista.

So any idea's on how to make synergy work for the ubuntu 2nd screen with a vista as the synergy server ?

/M

I thought they all have a config file but don't always require you to edit it directly.  I would try searching for a config file on Vista and editing it directly.

---

### Post by SergeantScar on 2009-02-20
I had an issue somewhat similar to this but the other way around.. so i dont know if what worked for me will work for you.

my ubuntu machine is on the left side of my XP machine. My XP machine has two monitors and the 'main desktop' is on the right monitor. i had issues moving through my second screen so i set my ubuntu in config to the right of my XP and my XP to the left of my ubuntu.. 

it is kinda backwards but it works for me now..

i hope that wasn't totally worthless..

---

### Post by bwhitaker on 2009-04-30
The way I got this working for me was to do all the layout in synergy. 

On the client(ubuntu intrepid using xinerama) I did this, basically it names each xdisplay from xinerama as a different screen directly into synergy.

```

synergyc --name laptop --display :0.0 serverip
synergyc --name laptop2 --display :0.1 serverip

```



Then on the syngergy server I used a config like this:
Note that laptop and laptop2 are the same computer, but different X displays.
```

section: screens
	desktop:
		switchCorners = none
		switchCornerSize = 0
	laptop:
		switchCorners = none
		switchCornerSize = 0
		xtestIsXineramaUnaware = false
	laptop2:
		switchCorners = none
		switchCornerSize = 0
		xtestIsXineramaUnaware = false
end
section: links
	desktop:
		left = laptop2
	laptop:
		right = laptop2
	laptop2:
		left = laptop
		right = desktop
end

```

This seems to be working perfectly for me.

Also to manually edit your config file for synergy in windows use the info button on the configuration screen to see where the file lives.

---

