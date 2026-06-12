---
title: "Two questions about HL2 / CSS"
date: 2007-10-22
forum: Gaming &amp; Leisure
---

### Post by Aljosja on 2007-10-22
Hi all!

I'm new here and a native dutch speaker so please forgive me if I'm in the wrong forum or my English is very bad.

I've installed Ubuntu 7.10 a few days ago and although I'm completely new to Linux, I must say I'm very impressed by the stability, comfort and smoothness Ubuntu offers. I've started messing around with Wine a bit and tried to install one of my favorite games HL2 and CSS. Installation was no problem at all, and the game runs really smoothly, but there are two small issues with both games:

1. When I start the games, I get the message that my nvidia drivers are outdated (it says I'm using the 6.14 drivers). That's really weird because I thought Ubuntu automatically installs the newest drivers from Nvidia. I've tried installing the Linux drivers from Nvidia's site but I couldn't get them installed. In the package manager I couldn't find any kind of video drivers and because the game runs OK, I can live with the fact I run outdated drivers.

2. This is a more serious problem, because the game thinks My videocard doesn't support DX9.0(c) and so runs the video effects of DX8, and that really has it's effect on the image quality: HDR doesn't work at all, Anti-Aliasing doesn't function and everything looks much worse then it does on My Windows XP partition. I've tried installing DX9.0c, but that doesn't change anything. I've got a 7800GT, so the card is not the problem. Can you guys help me out?

Thank you so much,

Aljosja

---

### Post by Alex Carroll on 2007-10-22
1. Steam will display that message regardless of the drivers you are using, just click "Don't show this message again"

2. Launching CSS or HL2 with the "-dxlevel 90" launch parameter should allow CSS to run in DX9 mode, but when I did this the game became unplayable on my X1800XL. Your 7800GT should be able to handle it, though.

---

### Post by aoanla on 2007-10-22
> **Aljosja said:**
>  I've tried installing DX9.0c, but that doesn't change anything. 

Wine handles DirectX internally by translating it to OpenGL. You really really shouldn't install "real" DirectX in a Wine environment - it can break things.

---

### Post by Aljosja on 2007-10-22
Thanks for the replies!

How do you enable the " "-*dxlevel 90" launch parameter *"?

---

### Post by Sockerdrickan on 2007-10-22
In steam under each games properties.

---

### Post by graabein on 2007-10-22
I've watched some videos of Team Fortress 2 and it looks fantastic. I love the cartoon style of it. 

I'm new to Steam so I have a newbie question:

It's a one-time payment only, right? It says TF2 costs 30 bucks on the homepage, and if I pay it I can download and install and get all the updates and play for free on Steam servers?

:popcorn:

---

### Post by aoanla on 2007-10-23
> **graabein said:**
> I've watched some videos of Team Fortress 2 and it looks fantastic. I love the cartoon style of it. 

I'm new to Steam so I have a newbie question:

It's a one-time payment only, right? It says TF2 costs 30 bucks on the homepage, and if I pay it I can download and install and get all the updates and play for free on Steam servers?

:popcorn:

Yes, that's correct. And, not only that, but if your harddisk dies, you can redownload and install it from the Steam servers!

If you're interested in any of the other Source games in The Orange Box, (Portal, Halflife2 and the two sequel Episodes to it), then it's much better value for money to buy The Orange Box instead of just TF2, by the way.

---

### Post by Aljosja on 2007-10-23
Well, I can't find it in each game's properties, are you sure it should be there?

---

### Post by aoanla on 2007-10-23
> **Aljosja said:**
> Well, I can't find it in each game's properties, are you sure it should be there?

Select game in My Games.
Select Properties.

Select (in the new window) "Set Launch options" (it should be under the "General" tab).

Set the launch options you want.

Close Properties window, Launch game.

(This is actually explained in the Steam website's support section, so...)

---

### Post by graabein on 2007-10-26
> **aoanla said:**
> Yes, that's correct. And, not only that, but if your harddisk dies, you can redownload and install it from the Steam servers!

If you're interested in any of the other Source games in The Orange Box, (Portal, Halflife2 and the two sequel Episodes to it), then it's much better value for money to buy The Orange Box instead of just TF2, by the way.

Thanks but I'm just interested in TF2. My machine is old and I don't care much for sci-fi horror shooters. Everything's either realism or alien violence. Boooring! 

Now for another question: How can I make sure me and my friends end up on the same server and on even balanced teams? I suppose it's not possible to "create your own game" on Steam servers? One has to join an already running one? Can you post a screenshot of the server selection page for TF2?

---

