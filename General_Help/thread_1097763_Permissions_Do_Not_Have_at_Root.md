---
title: "Permissions Do Not Have at Root"
date: 2009-03-16
forum: General Help
---

### Post by Milan Milenkovic on 2009-03-16
Can anybody help me out. I'm new to Linux and have recently loaded Ubuntu 8.1 onto a salvaged computer from the disc supplied with issue 286 of ComputerActive.  Everything seems to work fine, except for the niggling problem of deleting files that I don't want, such as most of the fonts that came with the OpenOffice suite.
I see that they are .ttf files and I have loads of .ttf files that I would like to install but am unable to as I,"don't have permission".
Did ComputerActive forget to change the permissions so that the user had unrestricted access to add/delete files as they saw fit.

I have right-clicked on any number of folders and looked at the permissions and on the ones where I would like to add other fonts etc., I am denied permission as,"I am not the owner".  On others I have been able to alter the permissions.

Also, does anybody know of an add on which I could download and have a folder/directory show the images inside as thumbnails on the folder, as you can do in XP.  No big deal if not able to do, but it would be a nice touch to see at a glance what images are inside each folder without opening each one at a time until you find what you are looking for.  At the moment you can only add an emblem to the folder which only indicates that that folder holds image files. Not much help.

Thanks in-advance Milan :(

---

### Post by taurus on 2009-03-16
If you want to move or copy files outside of your $HOME, you need root privilege.

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

Use the same password that you log in with when it asks for a password.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by heindsight on 2009-03-16
Just keep in mind, deleting files outside your home directory is generally not a good idea (that's why you don't have permission to do it).

If you want to remove things, it's usually better to use the package manager. For example, if you want to get rid of some ttf fonts go to
System>Administration>Synaptic Package Manager 
then click the Search toolbar button type: "TrueType" change the "Look In" option to "Description and Name" and the click search.
Now in the right hand pane of the window, you'll see a whole lot of packages, the installed ones have the little box left of their names highlighted. Look for the fonts you want to remove, right click the package name and select "Mark for Removal". Once you've marked everything you want removed, click the Apply toolbar button to apply the changes to your system.

---

### Post by Milan Milenkovic on 2009-03-23
Thanks for you input both taurus and hindsight. Have only got internet access via the library so that is why i've not been intouch. Will try what out what you have posted and let you know the outcome. Have been able to delete fonts via the command line, but they are still listed when i open "Write". As most are vertualy identical, i just wanted to streamline the number of fonts that loaded and only keep the ones i like and also add others that i have on a disc which are all *****.tff.  But i don't seem to be able to open them.
Still will try what you have both suggested and get back to you soon.
Again thanks:)

---

### Post by Milan Milenkovic on 2009-03-23
To heindsight, i see from your profile that you seem to have a version of Ubuntu called "Hardy Heron".  Is this version 8.04 as i've read that each version is called after an animal?
Just curious Milan

---

### Post by sisco311 on 2009-03-23
> **Milan Milenkovic said:**
> To heindsight, i see from your profile that you seem to have a version of Ubuntu called "Hardy Heron".  Is this version 8.04 as i've read that each version is called after an animal?
Just curious Milan

Yes, 8.04 is Hardy Heron & 8.10 is Intrepid Ibex. 
Complete list: [uwiki]DevelopmentCodeNames[/uwiki]

---

### Post by berong on 2009-03-23
hmmm..
wow i have the same question...
thanks for these answers...
but i have another problem...
an error occured which says something about "nautilus nad Corba"?

im just trying to install Rhythmbox when this error occur..
what could be the problem...?

---

### Post by Milan Milenkovic on 2009-03-24
[QUOTE=berong;6946852]hmmm..
wow i have the same question...
thanks for these answers...


berong, if you mean that you: "don't have permission", i have read since posting my above problem, that when you install the Ubuntu operating, you as the first person to enter your details are given "Admin" status.But this only seems to work in the command terminal.
I have been able to delete files via the command terminal, and also change the permissions. I have had the folder open in GUI view whilst at the same time deleting fonts in the command terminal window and watch as the font disapears in the GUI window. However when i open Write the fonts that i want to get rid of are still there.  It's not as easy as it is in Windows.
If i ever find out how to get rid of the fonts that i don't, i'll get back to you.
Sorry can't help on your other problem.
Best of luck Milan

---

