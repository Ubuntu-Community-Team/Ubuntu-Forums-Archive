---
title: "Tibia graphics!"
date: 2008-11-01
forum: Gaming &amp; Leisure
---

### Post by Thardmann on 2008-11-01
Hello :)

I am trying to make Tibia work on my Ubuntu 8.10 by using wine.. The Client opens, but the graphics are all wrong.. Buttons are not working, and only some parts of the screen are showing the client.. 

So my question is.. How can i change those graphics without using the "options - graphics" IN the client? 

:)

---

### Post by Ripfox on 2008-11-01
> **Thardmann said:**
> Hello :)

I am trying to make Tibia work on my Ubuntu 8.10 by using wine.. The Client opens, but the graphics are all wrong.. Buttons are not working, and only some parts of the screen are showing the client.. 

So my question is.. How can i change those graphics without using the "options - graphics" IN the client? 

:)

You know there's a native Linux client right?

[http://gaming.gwos.org/doku.php/guides:32bit:tibia#tibia](http://gaming.gwos.org/doku.php/guides:32bit:tibia#tibia)

---

### Post by Thardmann on 2008-11-01
Yea i know.. But i dont know how to install it :O

---

### Post by ZoOorO on 2008-11-01
> **Thardmann said:**
> Yea i know.. But i dont know how to install it :O

We are two now :p

---

### Post by Naiki Muliaina on 2008-11-02
I installed the linux client like this. All my downloads are put into the top level of my home directory untill i move them. In this case i left Tibia there.

Open Applications --> Accesories --> Terminal

Type the following replacing the bolded part with what your downlad of Tibia is called.

```
tar zxvf ./**tibia800**.tgz
```

Im guessing the 800 is a higher number now. Open your home folder and there should now be a folder called 'tibia', open the folder and click on 'Tibia'. That should start your game.

To add it to your menu, go back to terminal and type:

```
alacarte
```

This should bring up Ubuntus Menu Editor. On the list on the left click on Games. Then click 'new item' on the right side of the window.

Leave Type as Application.

Type Tibia in Name

Click Browse and find your Tibia file. Click on the Tibia you use to start the game, then click OK.

In comment type what you like.

To add a picture, click on the spring on the left. Click browse and move to a folder that has a tibia icon/image in youd like to use. If youve never done this before you dont see the Icons in the navigation window. You have to find the folder then click open, the Images within that folder will then appear in the first Image window. Select the image you want, click OK. Then click on on the 'Create Launcher' window and you should be good to go.

One small thing i noticed about Tibia. I only played it briefly while checking it was active for my site so didnt realy try much to get this working. But i found if i tried putting the Tibia folder anywhere but my Home folder, it didnt work.

Anywhos, hope you find that usefull.

---

### Post by Chinasgotrice on 2008-11-02
I followed your steps Naiki. Except when I click on the icon it ubuntu doesn't do anything.
And when I try through wine using the terminal I get some graphical error
[http://ubuntuforums.org/showthread.php?t=967503]("http://ubuntuforums.org/showthread.php?t=967503")
You can find in this thread. Not to hijack this thread but I just wanted to chime in.

I heard a rumor that tibia won't work with intel chips that are operating on linux.
What card do you have?

---

### Post by Naiki Muliaina on 2008-11-02
Motherboard : Gigabyte GA-MA790X

Processor : AMD Athlon 64 X2 Dual Core 6000+ 3.1GHz (AM2)

Ram : 8GB Black Dragon Ram

Graphics Card : Nvidia GeForce 9800 GT

Power Supply : OCZ 900W ModXStream Modular PSU

---

### Post by Chinasgotrice on 2008-11-02
Ooo..running Desktop? Im on a lappy. probably why half of the stuff I want to work...doesn't :(

---

### Post by Ripfox on 2008-11-07
Follow the link in my post. You MUST have 3d acceleration to run Tibia. I know it seems strange, but yea.

---

### Post by 5nak3 on 2009-01-02
Hi guys, I tried to run Tibia today on Hardy, but the game wont load.

I've followed the instructions in this thread as well as numerous others and even tried wine.

Through Wine (1.10) the screen is a mess, numerous gaphical glitches makes it unplayable...in fact I couldn't even log in.

The default linux installer I've unzipped into my home directory 
/home/me/tibia 
and then even when I try and load the Tibia program a screen will flicker for a second then vanish.

At first I thought it was because of the 3d acceleration (Ati Mobility 9000 IGP, so not the best card) however, I've got a number of other games (urban terror, openarena, alien arena etc...) all running, as well as Compiz.

When I check if 3d acceleration is running using  

glxinfo | grep rendering

i get the result

direct rendering: Yes

I'm stumped as to what to do now...I really would like an online RPG (not too graphically intensive) and for the moment I'm running The Mana World (using the OpenGl setting) so I don't know why Tibia is not running.

Any help would be appreciated.

---

