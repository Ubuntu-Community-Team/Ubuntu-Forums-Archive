---
title: "Totem still wants to be default media player?"
date: 2008-12-14
forum: General Help
---

### Post by Zevin64 on 2008-12-14
Hi, I've set most of my media file types to open with vlc by right clicking on the file and setting it to open with vlc.

However in some instances, e.g. when I'm finished downloading a media file in firefox and I open it from the download bar in firefox it opens up in Totem instead of vlc. This also happens when I open files from the file browser applet in Avant Windows Navigator, they open up in Totem instead.

I've tried System-->Preferences-->Preferred Applications-->Multimedia and selecting 'Custom' and putting vlc, but in the aforementioned scenarios Totem still opens up.

Any suggestions?

---

### Post by mc4man on 2008-12-14
> I open it from the download bar in firefox

Those are set in firefox ->  edit -> preferences -> applications.

I wouldn't go changing things in a blanket fashion, test out for suitability for each potential edit.

---

### Post by lordbux on 2008-12-14
just do this and all will be right

go to  System>Preferences>Preferred Applications  |||||

there in multimedia tab

form drop down menu elect VLC (if available)
or 
Select custom and In Command text box enter====> ** vlc %s**


hoping to hear good news:KS
long live opensource:guitar:

---

### Post by Zevin64 on 2008-12-14
None of those solutions have worked.

I've also tried typing gksudo gedit /etc/gnome/defaults.list in the terminal and replacing instances of 'totem' in the text file with 'vlc' and not even that works, totem still keeps opening up.:confused:

---

### Post by eBoxNet on 2008-12-14
try to remove totem and reinstall it.maybe this solve your problem (do the same with vlc)

---

### Post by Zevin64 on 2008-12-14
I just removed totem, didn't bother to reinstall. File browser applet works how I want it to now. VLC as default media player seems to override some of preferences in Firefox, e.g. it will open saved mp3s from the download bar instead of amarok. Might have something to do with my changes to gksudo gedit /etc/gnome/defaults.list Will check it out later, I'm satisfied with how things are now.

Thanks everyone.

---

### Post by 7raTEYdCql on 2008-12-14
This is what i normally do and it has worked.

Take a normal ".avi"file for eg.
Right click->properties->open with->select vlc.

With this the downloaded avi (if it is) should open with vlc. Try that for all other filetypes.

---

### Post by scouser73 on 2008-12-14
Right click on the media you want to view, select **Properties** and then **Open With** then what you need to do is make sure that the player you wish to use is selected, and remove the other players.

---

