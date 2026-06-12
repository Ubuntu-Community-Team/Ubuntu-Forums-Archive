---
title: "Firefox update-Ubuntu"
date: 2006-04-19
forum: Desktop Environments
---

### Post by Floppyjoe on 2006-04-19
A new Ubuntu version of Firefox was recently released with the updater tool.  I have a newer version of Firefox running and don't want to downgrade to this new repository release. Is there a way to get rid of the update icon in the panel so that i don't have to install this other version. It keeps telling me I have updates and when i check it's just this other version of Firefox.  

Floppyjoe

---

### Post by roncrump on 2006-04-19
[QUOTE=Floppyjoe]A new Ubuntu version of Firefox was recently released with the updater tool.  I have a newer version of Firefox running and don't want to downgrade to this new repository release. Is there a way to get rid of the update icon in the panel so that i don't have to install this other version. It keeps telling me I have updates and when i check it's just this other version of Firefox.  
[/QUOTE]

I also installed the newer version (1.5, now at 1.5.0.2), using the instructions on the wiki. However, the old version remains there as it is used by the operating system for various bits and pieces.

I believe that doing the system update will update this old version (1.0.7) to a newer version (1.0.8 ), and update other stuff related to how breezy uses it, but will not touch your newer version (mine is 1.5.0.2). At least I hope that is the case - I updated this morning but then had to dash to catch my bus and didn't try firefox.

Ron.

---

### Post by Floppyjoe on 2006-04-19
Thanks. I have Version 1.5.0.2 also and hope it won't change my prefered aplications and applications menu items.

---

### Post by Floppyjoe on 2006-04-20
Update--It worked fine without a hitch so far.

---

### Post by louis_nichols on 2006-04-20
well... you can open synaptic, go to firefox package, and then under "package menu" youhave an option "lock version". just check it and it won't ask you again about updating ff

---

### Post by InterNut on 2006-04-20
Great. i was just woundering about this myself.
i think ill try the update thingy, i dont want to disable the firefox packages in updater tool.

great forum, and users... ive learnt alot here, and so far i had no real problems with ubuntu, just minor things, like i added a extra drive for my downloads, i used the disks manager under system/administration... worked great... untill i rebooted, the drive was gone.... 
did some RTFM and found that i had to mount it in fstab *doh*... tried that and it seems to work now, (i havent rebooted yet *G*).

anyhow, great forum and dist, and all ppl here seems to be kind and helpfull, i havent seen any *RTFM* *GOOGLE* replyes... i really hate those replyes, cuz they wont help a noob at all.... 

keep up the good work... and hopefully i can contribute soon also!

---

### Post by mrazster on 2006-04-20
I noticed this toyesterday...but since I don't use the 1.0.7 or 8 version at all...I just removed it with synaptic. And haven't noticed any difference at all in the system.

Was it a misstake to remove the older firfox..??...if so why..??...what tasks does ubuntu use firefox for..?...other then the obvious ofcourse.

---

### Post by worty on 2006-04-21
I don't think it uses it for anything. Make sure to update your preferred applications (System -> Preferred Applications) to the your new firefox binary.

---

### Post by ec2 on 2006-04-21
Is it actually so important to own version 1.5.0.2 rather than 1.5? Are there so important bug fixes or something?`I think you should just update firefox, and that's that.

---

### Post by Bazon on 2006-04-21
[QUOTE=ec2]Is it actually so important to own version 1.5.0.2 rather than 1.5? Are there so important bug fixes or something?`I think you should just update firefox, and that's that.[/QUOTE]
At least [here is the changlog](http://www.squarefree.com/burningedge/releases/1.5.0.2.html)....

I think updating Fx is always a thing you have do handle a bit for yourself:

- Two different updates Systems: apt*/Synaptic vs. Firefox internal.
- Firefox internal update only works if you copy Fx in the user directory.

So anyway, I keep an eye on Firefox for myself and do the updates as I like.
*(Even to newer branch versions sometimes...)*

---

### Post by missmoondog on 2006-04-21
what if i don't use firefox at all? do i still need the update as firefox seems to be an important item in ubuntu's/gnomes eyes as far as trying to uninstall it.

thanks

---

