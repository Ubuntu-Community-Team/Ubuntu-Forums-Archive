---
title: "Networking"
date: 2009-05-11
forum: General Help
---

### Post by tbullock on 2009-05-11
Ok, to start I will say I am a total newb with Ubuntu. Even more new to networking. After that I will describe what I have and am looking for.

I have a dell laptop with Ubuntu. It was getting the Blue screen and several failed attempts to fix it I went to Ubuntu because it is free and I did not have the disc to try Windows again. After using Ubuntu I have started to like it more than Windows and this has caused my issues.

I also have a desktop running XP and it has several movies and all my music on it. The laptop has a small drive in it and will not hold this much. Here is where the networking comes to play. I would like to use both together. If I can switch to ubuntu on the desktop I would as long as I do not lose the data. Not sure if this is possible or not.

My wife has a laptop using XP also. Small drives there too.

I have a wireless router and can connect to the net from all 3 wirelessly. I am hoping to be able to use the desktop as a file server for the other 2. I would like to have the desktop sort of like an external hard drive. If I could I would like to be able to control the desktop remotely from the other 2 and sort of just stick the desktop out of the way. I do not mind plugging them together through a network cable but would like to go wireless if possible. I would also like to have the desktop be the print server also. I would love to be able to use all 3 to there potential but am left using the laptop while the desktop just sits by and does nothing other than the occasional cd or dvd. 

I hope this makes sense because it is hard to describe. It is just for the house not a business or something. I just want everything easier and more accessible. All Ideas are welcomed as to how to set it up or what to do to make it work if I have everything I need.

---

### Post by miwaypet on 2009-05-11
I think what you are saying is that you want the desktop to be the server for the network. You want to connect wirelessly with it, and remote into it as needed. Am I correct?

Laying that aside for now. You sat that:

> I also have a desktop running XP and it has several movies and all my music on it. The laptop has a small drive in it and will not hold this much. Here is where the networking comes to play. I would like to use both together. If I can switch to ubuntu on the desktop I would as long as I do not lose the data. Not sure if this is possible or not 

So you need to save this data and then convert the desktop to Ubuntu. To do that you are going to have to either:

1) transfer the data to external hardrive,

or

2) shrink windows ntfs partiton at least enough to install Ubuntu with a /data partition large enough to accomodate your extra data. 

I need to know a) size of desktop hardrive, b) size of data you want to save, c) amount of free space left on hard drive.

Until I have more data I cannot help.

---

### Post by tbullock on 2009-05-12
You are exactly correct on the first part.

The second part gets a little tricky. The desktop has 2 hard drives. A 40 gig drive and 20 gig drive. The 40 has everything on it (xp, music, documents, everything). It has about 18gig free on it. The 20 gig has movies and that is it and has about 12gig free. These are just guesses but I am pretty sure that is about where it is. Where I run into trouble with them is I have been editing clips from my wife's video camera to create a family DVD. I have edited the clips which were on the C: drive (40g) and then started sticking them into the D: drive (20g) to keep what was fixed separated from what still needed work. To top that all I was using MovieMaker that comes with XP to splice the operation. I am pretty sure I cannot continue in Ubuntu with the same program. So that is what has delayed its conversion to Ubuntu. After I have the movie made I think I will backup the data on an external for the swap. Should I hold off before converting this thing to a server? Should I even worry about swapping it from XP? I would like to be able to access the music and movies from my Ubuntu laptop as if they were saved on the laptop. In turn I would like the desktop to still function and be able to download to it as the laptop has such a small drive. I am not sure how to set this up? Also, I will need to be able to connect from windows xp and ubuntu because the wife can't figure ubuntu out. If you have instructions on setting it up within xp so I can get it done and then how to do it with ubuntu later after I get this movie made that would be great. I am using DSL if that makes a difference to because I have heard that effects ip addresses and so forth but other than that I am lost. I hope this is making sense because as I read back through it I have no Idea how to word this to my liking.

---

### Post by tbullock on 2009-05-12
Is there any way to dual boot it? Sort of have a ubuntu server for most the time and then boot windows on occasion? Just thinking here. It may be way to much work. I just want to be able to play a song on my laptop that is saved on the desktop or a movie that is saved there. And use it as a central location the printer is plugged into. I thought about vnc or remote desktop but that doesn't appear to support sound so well and it is really laggy between windows pcs. Is what I am trying to do even possible?

---

### Post by miwaypet on 2009-05-12
What you can do is this. Leave the D drive untouched. Now you can either place any important documents you want to keep in a folder on the D drive because you said it has room on it. Or, if you have a usb stick, move them onto it. To determine if you can move docs, pics, what have you, check the properties of each, and add up all the sizes of each folder. If small enough to fit on second drive then move all into a folder just for that.

Then install Ubuntu on first disk, with a swap 2 times size of ram but not to exceed 2GB. A / partition of 10GB. A /home partition of the remainder. Ubuntu will see the info on the ntfs partiton on second drive. After the install is completed I will help you mount the second drive so it can be read and worked from. Please, under no circumastances touch the second drive when installing. Do not formatt it. Just leave it as is.

If you want to be extra cautious download gparted and burn to a disk. Use it to pre-partition the first hard drive.

---

### Post by tbullock on 2009-05-13
I am going to wait on installing ubuntu on the desktop for a while. Do I need a program or some sort of hardware to setup the network wireless? I know I can do it with a crossover cable but not sure about wireless.

---

### Post by tbullock on 2009-05-13
Ok, I have been able to setup the 2 windows pc's and they are sharing folders. I think that was my main plan. Next will be to connect the Ubuntu Laptop to the network and have access to the files.

---

### Post by miwaypet on 2009-05-13
If all you want to do is network the Ubuntu PC to the windows network, you need to install samba:

```
sudo apt-get install samba libpam-smbpass

```

Right click on the Ubuntu folders that you wish to share.

Check **Share This Folder**.

Check **Allow Other People To Write To This Folder**.

Click **Create Share**.

On your windows desktops. **Right-click** on any empty part of the desktop. Select **New**>**Create Shortcut**.

Enter the **location** as : \\<your hostname>  

Hostname is found by opening terminal in Ubuntu and select the part between **@** and **$**.

Login with Ubuntu user name and password.

Good Luck :p

---

### Post by tbullock on 2009-05-13
Thanks for the info. After I get the movie made and off there I will find something to do with the data and switch over to ubuntu.

---

