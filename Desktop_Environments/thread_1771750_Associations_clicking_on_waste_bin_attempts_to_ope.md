---
title: "Associations: clicking on waste bin attempts to open in GIMP? WTF?"
date: 2011-05-30
forum: Desktop Environments
---

### Post by Martyn Thompson on 2011-05-30
Hello people. 

Don't know what I have done or how I have managed to do this but when I click on the Waste Bin it opens up GIMP.  

Obviously once GIMP has opened fully it throws up an error saying it cannot open the file.  

I am sure this must be a related to file associations but don't know how to change them.  Any ideas would be welcomed. 

Thanks, 

Martyn

---

### Post by Copper Bezel on 2011-05-30
It is indeed. The simplest way to fix it is to right-click a folder in Nautilus, select "Open with other application," and select Nautilus. Notice the tickbox to remember this association next time. Most likely, the problem actually started with opening a location in GIMP in exactly this way.

You can also change the entry in .local/share/applications/mimeapps.list.

Edit: Actually, this shouldn't affect the trash bin at all. A little baffling. Is it Unity 2d or 3d?

---

### Post by Martyn Thompson on 2011-06-12
Copper Bezel,

Thanks for your response.  Locating and opening the Trash with the right click method worked and now it seems to work properly from the Desktop (on the panel). 

Search for the reference on the mimeapps.list as suggested but could not find it there. 

Sorry - I believe I am (still) using Gnome... there is no sidebar and I recall on upgrading there was a brief message telling me the soft or hardware isn't up to running Unity.  I will check now though...

Thanks again for the advice... it has worked!

---

### Post by SerafeimG on 2011-07-27
Same problem for me. When I was clicking on Trash Bin, Sound Converter was opening.
I fixed it by opening the mimeapps.list with gedit and deleting the soundconverter from the inode/directory association.

Thanks a lot Copper Bezel.

---

