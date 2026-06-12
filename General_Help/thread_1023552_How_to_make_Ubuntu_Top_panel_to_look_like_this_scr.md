---
title: "How to make Ubuntu Top panel to look like this screen...."
date: 2008-12-28
forum: General Help
---

### Post by ke3pup on 2008-12-28
Hi guys

I want to make my Ubuntu 8.10 top panel to look like the panel in this screenshot:

[http://visionsofart.deviantart.com/art/Gaia-08-for-Linux-99037206](http://visionsofart.deviantart.com/art/Gaia-08-for-Linux-99037206)

Can anyone please tell me how i can archive this? 

Any help would be appreciated.

Thank you

---

### Post by stormtrooprdave on 2008-12-28
You can download all the files from that page

---

### Post by vallhalla81 on 2008-12-28
in short you do download the files listed on the left of the screen in the link you provided then with Emerald instaled (this can be done from synaptic) you apply the themes, if you need further help please feel free to write back :)

---

### Post by ke3pup on 2008-12-28
i have downloaded all the files from the site, already had installed emerald Theme manager and have applied the theme , all the windows look like the screenshot but the Panel doesn't change. Its still the same old Ubuntu Panel.

There is a gtk folder in the zip file too , but i couldn't find a way to use it, what program is used to import them into? what i do with all those files. because the emerald file only changes the windows themes but not the panel itself. 

please help. Thank you

---

### Post by parajuito on 2008-12-29
Ok look theres a folder named gtk inside that folder theres another folder named Gaia08 select that folder and right click it then select create archive then create a tar.gz archive and thats it drop the new tar.gz archive to your theme manager.

---

### Post by aMADme on 2008-12-29
Even with the GTK theme installed your panel still won't look like that!

I doubt in that screenshot he is even using gnome, it might be some alternativ windows manager like fvwm, for which the config is not included. 

Your best bet might be to contact the creator directly to find out.

---

### Post by ke3pup on 2008-12-29
> **parajuito said:**
> Ok look theres a folder named gtk inside that folder theres another folder named Gaia08 select that folder and right click it then select create archive then create a tar.gz archive and thats it drop the new tar.gz archive to your theme manager.

Hi , after a bit of Googling i figured to do exactly as you've written here, Only problem is that Now Ubuntu says "the theme might not look as intended because it's missing the required engine".

To say the least, the theme doesn't seem to be working, it's easy to tell since the skins on Panel, Windows ....etc look broken. 

The engine this theme uses is "Pixmap", seem to be installed by Ubuntu since Synaptic says it is . i installed couple of more engines hoping it'll fix it but nothing.

I've kind of given up, Some people posted in this forum that the missing engine is false alarm and all should be good, not i'm my case since the theme doesn't appear as it should. 

any suggestions would be appreciated.

---

### Post by parajuito on 2008-12-29
"The theme might not look as intended because it's missing the required engine." its a false alarm , it's because theres a part of the gtkrc that should have an engine but its missing to fix it just change the following code:

style "unstyle"
{
  engine ""
  {
  }
}

to:

style "unstyle"
{
  engine "pixmap"
  {
  }
}

I dont know why it looks broken in your computer but to me it seems all right :) except for the panel it doesnt looks like in the screenshot.

---

### Post by parajuito on 2008-12-29
I finally know how this was done, it's a background image, the background does all the trick. xD

Look at the 6th comment: [http://visionsofart.deviantart.com/art/Gaia-08-for-Linux-99037206?offset=40#comments](http://visionsofart.deviantart.com/art/Gaia-08-for-Linux-99037206?offset=40#comments)

---

