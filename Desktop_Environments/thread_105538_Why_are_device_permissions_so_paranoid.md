---
title: "Why are device permissions so paranoid?"
date: 2005-12-18
forum: Desktop Environments
---

### Post by gilgongo on 2005-12-18
I've been using Ubuntu only two weeks, but one thing that's coming up to bug me more and more now is the fact that things that need seem to want root permissions sit there like speedbumps seriously degrading Ubuntu's ride, even for somebody who knows what's wrong, let alone a newbie who doesn't.

In the last few days I've had to hack my way around local NTFS mounts. Why not make these readable by default? Ubuntu is a desktop system, no? Also, only root has write access to various devices like firewire, DVD and USB serial. Huh? What's that about?

I'm just an Ubuntu newbie, so it may be I'm missing something here, but almost the first thing I had to to after installing my system was chmod +rw my firewire devices so that I could capture video from my camcorder.

Odd.

---

### Post by Ocxic on 2005-12-18
Devices are owned by root by default, it's the only way to mount one. NTFS is always a bit tricky, if you don't want to fool around with permissions the easiet way is to make a mount point in /mnt (ie: /mnt/firewiredrive) then make a link to your desktop by typing:

ln -s /mnt/your_new_mount /home/your_username/Desktop/

that way you won't have a problem with permissions.

example (this is how i have my other drives mounted):
```

sudo mkdir  /mnt/Storage
sudo mount /dev/hdb1 /mnt/Storage
ln -s /mnt/Storage /home/admin/Desktop

```

this put the mount point in /mnt/Storage with link to my Desktop to access it.

---

### Post by gilgongo on 2005-12-18
Thanks, but I'm more more interested in the philosophical point of *why* these things are only accessible by root in Ubuntu (and I'm not just talking about NTFS mounts).

Ubuntu is a desktop distro aimed (sort of) at newbies. If somebody who's only used Windows before installs Ubuntu can't get their DV camera working with it because of a permissions problem then that's a great shame. Similarly with, say, PPTP.

I know that in "normal" GNU/Linux these things require root level access and I'm not questioning that. What I'm questioning is why Ubuntu enforces this by default.

And if anyone says "Those Windows users are gonna have to realise that we do things differently here in Linux land" they can bite my arse.

---

### Post by cwaldbieser on 2005-12-18
[QUOTE=gilgongo]Thanks, but I'm more more interested in the philosophical point of *why* these things are only accessible by root in Ubuntu (and I'm not just talking about NTFS mounts).

Ubuntu is a desktop distro aimed (sort of) at newbies. If somebody who's only used Windows before installs Ubuntu can't get their DV camera working with it because of a permissions problem then that's a great shame. Similarly with, say, PPTP.

I know that in "normal" GNU/Linux these things require root level access and I'm not questioning that. What I'm questioning is why Ubuntu enforces this by default.

And if anyone says "Those Windows users are gonna have to realise that we do things differently here in Linux land" they can bite my arse.[/QUOTE]
I am not exactly sure what you are suggesting.  Are you saying that you think any user should have permission to start a PPTP connection by default?  The reason there are permissions in place at all is so that you can exercise some modicum of control over your own system.  A virus/worm/cracker is not going to be especially concerned whether you are running a server or a desktop system if it just wants to turn you into an email relay.

---

### Post by risher1 on 2005-12-18
I made a desktop icon as suggested. It works fine except unable to write files .
If I mount the dev in terminal without sudo, i can write, using sudo, no write ! Could I have something else set wrong (Newbie also)   Thanks

---

### Post by Hairy_Palms on 2005-12-18
? i didnt think you cud mount without sudo.............

---

### Post by cwaldbieser on 2005-12-18
[QUOTE=Hairy_Palms]? i didnt think you cud mount without sudo.............[/QUOTE]
The man pages for fstab suggest that you can set up devices to be mountable by normal users.  Also, the "pmount" command lets ordinary users mount removable media under /media.

---

### Post by gilgongo on 2005-12-20
This thread is probably a bit stale, but in reply to cwaldbieser:

> The reason there are permissions in place at all is so that you can exercise some
> modicum of control over your own system.

Agreed, but what I'm saying is that there is a class of actions that most users would consider they should be able to take without having to work out how to circumvent root access to them. Specifically, I mean making VPN connections, grabbing DVD video, mounting filesystems and some others.

Perhaps its a matter of making gksudo more prominent in the UI (for example, a right-click option to run as root with an  option to "always run this application as root") or simply recognising some simple truths like NTFS mounts should be readable by non-root users, or they should have access to their own camera's video footage by default.

From a security point of view, it may in theory be less secure having gksudo popping up a password prompt every time something wants root access. Pragmatically, however, there's nothing to stop a trojan doing the same thing to get that access. And more importantly, if the user has allowed the trojan onto the box in the first place (think Explorezip, think Melissa) then if you've ever witnessed a virus outbreak by trojan vector you'll know that if the user has it in their power to allow root access, they will no matter what asks for it.

In the end, tojan and virus attacks are edge cases best prevented by education and positive social engineering rather than "cured" by imposing paranoid permissions at filesystem level that just piss people off. In that strategy at the very least, Microsoft has it right.

---

### Post by cwaldbieser on 2005-12-20
[QUOTE=gilgongo]This thread is probably a bit stale, but in reply to cwaldbieser:

> The reason there are permissions in place at all is so that you can exercise some
> modicum of control over your own system.

Agreed, but what I'm saying is that there is a class of actions that most users would consider they should be able to take without having to work out how to circumvent root access to them. Specifically, I mean making VPN connections, grabbing DVD video, mounting filesystems and some others.

Perhaps its a matter of making gksudo more prominent in the UI (for example, a right-click option to run as root with an  option to "always run this application as root") or simply recognising some simple truths like NTFS mounts should be readable by non-root users, or they should have access to their own camera's video footage by default.

From a security point of view, it may in theory be less secure having gksudo popping up a password prompt every time something wants root access. Pragmatically, however, there's nothing to stop a trojan doing the same thing to get that access. And more importantly, if the user has allowed the trojan onto the box in the first place (think Explorezip, think Melissa) then if you've ever witnessed a virus outbreak by trojan vector you'll know that if the user has it in their power to allow root access, they will no matter what asks for it.

In the end, tojan and virus attacks are edge cases best prevented by education and positive social engineering rather than "cured" by imposing paranoid permissions at filesystem level that just piss people off. In that strategy at the very least, Microsoft has it right.[/QUOTE]

I am not inclined to take a postion with regards to security/permissions at this time, but I would point out that these are exactly the kind of security issues Microsoft gets raked over the coals for.

I can see your point of view where a home user is likely to consider the permission aspects of their home system as an impediment rather than an asset.  Distributions like Linspire follow this philosophy, letting users pretty much run as root from what I understand.

I suppose that the security forums would probably be the best place to raise your concerns if you ultimately wanted to see them acted upon.

---

### Post by aysiu on 2005-12-20
[QUOTE=gilgongo]
In the last few days I've had to hack my way around local NTFS mounts. Why not make these readable by default? Ubuntu is a desktop system, no?[/QUOTE] Try Mepis.

---

### Post by soulestream on 2005-12-20
the basic answer to your question is linux denies rights by default. All of the problems M$ has had over the last few years is becuase windows grants all permissions by default. Changing permissions in linux is easy to customize to your needs. However granting every user that loaded(or logged in) to a distro rights to all drives, install software, and use any device, is bad security. If you want to be able to rw to a firewire drive, CHMOD it or change the udev rule, to what you want. 

Normally I would say if you dont like it, use windows, but it seems M$ finally started paying attention and with vista most of your usual rights will be denied by default. Why, better security.

soule

---

### Post by towsonu2003 on 2005-12-20
[QUOTE=soulestream]
Normally I would say if you dont like it, use windows, but it seems M$ finally started paying attention and with vista most of your usual rights will be denied by default. [/QUOTE]
but no worries for virus writers: Vista SP2, expected to appear before Vista's release candidate, will give those rights back to the EULA'ed end user ;)

---

### Post by zoiks on 2005-12-21
[QUOTE=gilgongo]And if anyone says "Those Windows users are gonna have to realise that we do things differently here in Linux land" they can bite my arse.[/QUOTE]

Because Linux OS'es were designed by people who decided to make a proactive difference instead of whining.  They designed for people who don't want them to bite their arses.

You can find other distros which make it easier to access the devices themselves.  So go use one of them and have a gay ole time.

---

### Post by anil_robo on 2005-12-21
For an average desktop user, a root account/sudo password is never required for doing most common things like setting up email clients, writing letters and designing slideshows, doing accounts, chatting, plugging-unplugging USB devices etc.

Ubuntu asks for the user to create a user password during install, and also asks to confirm it so that the user doesn't make an error there. For people who don't like to enter their passwords everytime, they can opt to be logged in as root, which is "never" recommended, though possible!

It's perhaps in windows only that you can mess up badly with your system without knowing anything about it. It's only in windows that you can allow your firewall for intruders without knowing about it. It's only in windows that you download viruses disguised in screensavers and they mess up with your master boot record so badly that your system dies instantly! However, there's light! Windows Vista will follow the same password system as Linux has been doing since ages, doesn't matter if you're convenient with it or not! And I'm sure it'll take you months to figure out how to turn that option off in Windows Vista. In Linux, it's just a command away.

If you enter a password before any change that results in "potentially" disastrous consequences, you "know" what you've been doing. At least you were alerted, if you didn't care to listen!

If you don't like to enter you password every time, but still want to enjoy rock-solid security of Linux, I strongly suggest you set yourself a single alphabet password! It'll save some energy of your fingers, yet provide your mind with much needed peace.

Hope it helps! :)

---

### Post by aysiu on 2005-12-21
[QUOTE=anil_robo]
It's perhaps in windows only that you can mess up badly with your system without knowing anything about it.[/QUOTE] I'm glad you left that *perhaps* in there, because you forgot our good friend Linspire.

---

