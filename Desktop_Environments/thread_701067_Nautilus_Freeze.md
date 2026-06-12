---
title: "Nautilus Freeze"
date: 2008-02-19
forum: Desktop Environments
---

### Post by spvo on 2008-02-19
The past couple months I have been having a strange problem with nautilus freezing whenever I try to view specific folders.

I think it is somehow related to gimp / pdfjoin / tiff2pdf.  Basically when I am working with images and pdfs, occasionally natuilus will freeze.  I force it to close, and from then on, whenever I return to that folder (in nautilus) it will crash.  I can view the folder and files fine from the terminal.  Also, rebooting does not seem to help.

Thinking it was a nautilus specific problem I've tried deleting the following files and directories hoping the problem will go away.
~/.thumbnails
~/.nautilus

Deleting the .nautilus removes all the saved views for a folder (eg view as list) will sometimes fix the problem.  And sometimes if I use nautilus to view the folder previously causing the crash, and change the view to list, it will start crashing again.

Does anyone have any idea how to fix this problem?  Its been happening about once a month to me, and its getting very frustrating.

---

### Post by marn on 2008-02-20
I have been having the same problem as well - as far as I can work out it has something to do with the thumbnails/preview settings in Nautilus. Try disabling the preview function in nautilus.

If Nautilus freezes, a  reboot shouldn't be necessary - stopping and restarting gnome should work:

swap to the text mode (Ctrl+Alt+F1)

log in, then
```
sudo /etc/init.d/gdm stop
```
then
```
sudo /etc/init.d/gdm start
```

Nautilus should be OK then. 

It's a bit of an awkward work around, maybe someone has a better solution or can solve the problem!

---

### Post by talsemgeest on 2008-02-20
> **marn said:**
> I have been having the same problem as well - as far as I can work out it has something to do with the thumbnails/preview settings in Nautilus. Try disabling the preview function in nautilus.

If Nautilus freezes, a  reboot shouldn't be necessary - stopping and restarting gnome should work:

swap to the text mode (Ctrl+Alt+F1)

log in, then
```
sudo /etc/init.d/gdm stop
```
then
```
sudo /etc/init.d/gdm start
```

Nautilus should be OK then. 

It's a bit of an awkward work around, maybe someone has a better solution or can solve the problem!
Since you're having the same problem, could you try disabling the preview thumbnails?

---

### Post by marn on 2008-02-20
Well, I have been fiddling with the settings, only previewing files under a certain size and so on. I like the preview function, as I work a lot with image and svg files. That is why I haven't wanted to fully disable them. 

As I said though, things seem to work if you do fully disable the preview function

---

### Post by vanadium on 2008-02-20
You can kill nautilus also with "killall nautilus" or with the "kill" cursor you get after typing xkill in the terminal: no need to restart X.

I was also going to suggest that the problem is related to the preview function. In particular the "sound preview" functionality is causing trouble. I am currently running without preview enabled, which largely speeds up things, although I never had problems with the other preview options myself.

---

### Post by talsemgeest on 2008-02-20
> **marn said:**
> Well, I have been fiddling with the settings, only previewing files under a certain size and so on. I like the preview function, as I work a lot with image and svg files. That is why I haven't wanted to fully disable them. 

As I said though, things seem to work if you do fully disable the preview function
So I guess it might just be a necessary evil...

---

### Post by spvo on 2008-02-21
You both were right, disabling the preview fixed the problem.  I've played around with the problem a bit more and have noticed a few other strange things.  The folder that was causing nautilus to crash will only crash it in list view, not in icon view.  The reason deleting ~/.nautilus originally fixed the problem was because that restores all folders to the icon view.

I guess this is just a general bug, so for now I've disabled preview all together.  Is there, however, a way to restrict preview to specific file types?  The only things I want it for are for pdfs and jpegs, so I would like to only have it preview those two file types.  Is this possible?

Anyway, thanks for your help so far.

---

### Post by talsemgeest on 2008-02-21
Ill see if I can figure it out when I get back onto my ubuntu computer in a bit...

---

### Post by talsemgeest on 2008-02-21
Sorry, can't find anything. But I am pretty sure that I have done it before, so I will keep looking...

---

### Post by spvo on 2008-02-22
> Sorry, can't find anything. But I am pretty sure that I have done it before, so I will keep looking... 

That would be great if you can.  I poked around in the nautilus settings with gconf-editor but wasn't able to find anything useful.

---

### Post by aaack on 2008-03-15
Well, I had the same problem, Nautilus froze when I opened certain directories, If I left the window open eventually (like an hour after the hang) the X server restarted.

I solved the problem just unchecking the compact icons distribution (sorry I don't know the option's name in english, in spanish is "Usar distribución compacta").

I guess it's an elusive bug but I can repeat this behavior every time I check that option, problem is I really don't know why nautilus hangs on that directory and it's ok in others.

Hope that helps a little bit.

---

### Post by Chokkan on 2008-04-12
I also had this problem and I've simply disabled the previews which seems to have solved it. Odd bug as it only happened in one particular folder that I could see.

---

### Post by billstei on 2008-06-08
I'm not sure if this is the same problem or a different one but if I do:

Start Nautilus
Click Tree arrow next to File System
Click Tree arrow next to usr
Click Tree arrow next to share
Nautilus hangs with the message "Loading..." in the tree

But if I do this:

Start Nautilus
Click Tree arrow next to File System
Click Tree arrow next to usr
Click folder share

Nautilus populates the right side with the folders of /usr/share very quickly without any hanging.  These folder icons are identical to what should have populated the tree display in the former test so I would expect similar computational delays/workload.  Furthermore, since there are no files subject to previewing in /usr/share this does not to me seem like a preview problem.  What I find is that the hanging occurs when the number of sub-folders is (relatively) large.  I had a folder in my home dir that had a large number of sub-folders, and Nautilus quit hanging when I split the folder into two groups/folders with respectively fewer sub-folders.  This problem goes back at least to Gutsy release, as I have been experiencing it all through that period.

Just some observations.

Bill

---

