---
title: "Gnome being replaced by unity on login"
date: 2012-08-05
forum: Desktop Environments
---

### Post by chrismacp on 2012-08-05
Hi,

I couldn't find a similar thread anywhere and cant quite workout how to fix my problem. 

After delaying the move to Unity for a while I finally upgraded my laptop to 12.04. 

I have installed Gnome3 as I prefer it but when I login (having selected either Gnome/Gnome Classic/No effects) I am still presented with Unity.

It looks like gnome is loaded up for half a second then Unity replaces it. Weird.

Not sure how to fix this really? Any ideas anyone?

---

### Post by cybergalvez on 2012-08-05
> **chrismacp said:**
> Hi,

I couldn't find a similar thread anywhere and cant quite workout how to fix my problem. 

After delaying the move to Unity for a while I finally upgraded my laptop to 12.04. 

I have installed Gnome3 as I prefer it but when I login (having selected either Gnome/Gnome Classic/No effects) I am still presented with Unity.

It looks like gnome is loaded up for half a second then Unity replaces it. Weird.

Not sure how to fix this really? Any ideas anyone?

did you install gnome-shell? There is no gnome3 its really gnome-shell, although when you log in it will simply be listed as gnome

---

### Post by chrismacp on 2012-08-05
> **cybergalvez said:**
> did you install gnome-shell? There is no gnome3 its really gnome-shell, although when you log in it will simply be listed as gnome

Hi,

Yes, sorry I installed gnome-shell

---

### Post by chrismacp on 2012-08-05
It's weird actually as I just went back to my laptop to check something and on the lock screen I can see the black gnome-shell bar at the top of the screen. But this changes to the Unity version on the desktop when I unlock.

I tried to go back to software centre to remove gnome-shell but clicking on the 'remove' button had no response. 

Kind of wish I'd stayed on 11.04 now, but want to move on.

---

### Post by cybergalvez on 2012-08-06
> **chrismacp said:**
> It's weird actually as I just went back to my laptop to check something and on the lock screen I can see the black gnome-shell bar at the top of the screen. But this changes to the Unity version on the desktop when I unlock.

I tried to go back to software centre to remove gnome-shell but clicking on the 'remove' button had no response. 

Kind of wish I'd stayed on 11.04 now, but want to move on.

Almost sounds like they are both running at the same time, which I don't think they should. From a terminal window what happens when you type 
```

gnome-shell --replace

```

---

### Post by chrismacp on 2012-08-07
> **cybergalvez said:**
> Almost sounds like they are both running at the same time, which I don't think they should. From a terminal window what happens when you type 
```

gnome-shell --replace

```

Thanks for the suggestion.

That did bring back gnome-shell which I can see now as I'm typing this. Will do a few tests to see if it sticks.

Ok just reverts back to Unity when I logout and login again. Not sure if the --replace is supposed to persist or if it's supposed to be run as root so just trying to look in to that.

---

