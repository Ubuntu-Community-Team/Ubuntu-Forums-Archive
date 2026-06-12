---
title: "how to burn bin/cue movie file to dvd-r?"
date: 2005-12-27
forum: General Help
---

### Post by bionnaki on 2005-12-27
I have a movie that is in bin/cue format. just wondering how I can 1) watch it 2) burn it to dvd-r

any ideas?
thanks party people

---

### Post by stevea1210 on 2005-12-27
I'm not sure which burning programs support bin/cue, but you can open a cue file in VLC, and watch the movie.  VLC supports many different file types.

---

### Post by kingsidy on 2005-12-27
I know that you can use nerolinux, with the record image function. It does support the bin, cue format and will allow you to burn them. Usually you have to pay for a program like nero. The other excellent alternative is k3b. You can burn several types of images with it as well. You can get it from the repositories. I am not sure about gnomebaker, but it should be able to burn those images as well. 
In order to watch it, you can either mount the iso in the terminal, or the other easier option is to right click on the image file and open with VLC in case you have it installed. If not get it from the repositories. It will play the movie and is actually much easier than mounting the image, because you just right click

---

### Post by bionnaki on 2005-12-28
thanks. I'll see if I can burn to disc with k3b.

anyone know how I can convert this to, say, avi?

---

### Post by kingsidy on 2005-12-28
dvdrip and acid rip. I have used both and they do work good

---

### Post by kaamos on 2005-12-28
I think the newest gnomebaker supports bin-images as well.

---

### Post by ipp3l1 on 2006-02-01
My k3b doesn't support bin -images...

---

### Post by TristanMike on 2006-03-03
That's because it's the "*.cue" files you want to burn, and you want to "Burn a CD Image" and select the cue file of what you want to burn. You may have to right click the main selection window and add that button, I can't remember if it's there by default. That should do the trick. You might also want to change the drop down menu in the burning options dialog window from "Auto" to "Bin/Cue" just to make double sure. But I'm burning a bin/cue right now, as I type and I'll wait untill it's finished for the test to let you know if I had any errors....

I had one error. Cdrecord came back with an error before the burn even began. I suspect it has something to do with either 

a) The Breezy "fix" for the CD Door button functionality. Ever since I implemented the fix for the cd door, found here on the forums, I've had problems with my cdrom drive. Mostly it's been when I push the button and eject the cd/dvd and put the new one in, it doesn't recognize it properly, it's like it only reads one or two folders that may or may not be there sometimes with "?????" for the folder name, until I right click/eject and then reinsert.(probably not unmounting correctly) or 

b) I have a cd rom and a dvd rom/writer and I had a cd in the cd part of the computer, which it also may not have liked. So when I properly ejected the cd that was in the burner, I also ejected the cd in the cd-rom tray and that may have fixed it or 

c) both a & b

Either way, it fixed the one error i received and the cd burned correctly. I even burned 2 copies of a 2 disc set of bin/cue files (4 discs) with no problem.

Hope that helps and good luck.

EDIT: Also, Totem played the SVCD's I threw at it. Just thought you'd like to know

---

