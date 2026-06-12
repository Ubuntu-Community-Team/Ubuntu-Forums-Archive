---
title: "Compiz Setings Manager"
date: 2006-09-16
forum: Desktop Environments
---

### Post by colonel_panic414 on 2006-09-16
I have recently upgraded to the new compiz packages in quinn's repos. Everything works, with the exception of the Compiz Settings Manager. No matter what settings I change, they don't take effect. The key combos that I set or that are just default combos will not work. So, either the CSM isn't working right, or I just don't know what I'm doing. BTW, CSM has not worked for me even once since I installed it. Thanks for any help!

---

### Post by turbojugend_gr on 2006-09-16
How-To: 
--> Open CSM  
--> Navigate nautilus to your home folder  
--> Press CTRL+H  
--> Right click the ".compiz" folder  
--> Choose Properties  
--> Edit the Perimissions so you allow everyone to read and execute(run).
--> Close and restart csm

The above should do the trick, Let me know.

---

### Post by colonel_panic414 on 2006-09-16
I just tried that, and it didn't work. Everyone already had Read and Execute permissions.Is there anything else I could do? Thanks for the help!

---

### Post by turbojugend_gr on 2006-09-16
Hmm, check if in the ",compiz" folder for a file "csm_settings", post if it is there. Change it's permissions too. If that doesn't work either try giving all permission (read-write-execute) to all three groups, See if it works that way if it doesn't work again replace the previous permissions (so it would be safe again). Let me know how it goes again.

---

### Post by turbojugend_gr on 2006-09-16
Remember giving read-write-execute both to the folder and the csm_settings file. And taking them back if that doesn't work either.

---

### Post by colonel_panic414 on 2006-09-17
That didn't work either. What should I do next?

---

### Post by turbojugend_gr on 2006-09-17
I am stunned! Hmm I reread you initial post... Something is not clear to me, have you tried to disable the Cube for instance so you can check if that did not work also? 
It is clear that the custon shortcuts you use are not active, but I can't be sure if you have the same with every change you do on csm. You also say that the default shortcuts are not active? 
It's pretty messed up to me. So try making the situation clearer, along with the cube test (ofcourse with full permissions to the file and the folder)

---

### Post by turbojugend_gr on 2006-09-17
If the above are useless, try only to make more clear the whole situation and also try this: >>> In a terminal type "csm" and post the output info you get when you start it and when you change sth.

---

### Post by PriceChild on 2006-09-17
I had this problem... and also alacarte wouldn't change my menus.

My standard solution is now:

sudo chown username:username -R /home/username

It ensures everything is yours, and therefore writable by applications that you spawn.

Pricey

---

### Post by colonel_panic414 on 2006-09-18
Gah! Why didn't I think to try that? I'm currently away from my Ubuntu box, so I'll let you know if it works for me later. Thanks!

---

### Post by colonel_panic414 on 2006-09-18
Yes, i have tried disabling plugins before, but no changes occur. I should probably correct myself. MOST of the default key combos don't work. A few, such as the cube, do work. But thats one of the only ones. Anyway, I have taken your suggestion and gotten the CSM outputs.

```
/home/taylor/.themes/Tactile/gtk-2.0/gtkrc:1046: Unable to locate image file in pixmap_path: "spin_button_up_arrow_prelight.png"
/home/taylor/.themes/Tactile/gtk-2.0/gtkrc:1050: Overlay image options specified without filename
/home/taylor/.themes/Tactile/gtk-2.0/gtkrc:1056: Unable to locate image file in pixmap_path: "spin_button_down_arrow_prelight.png"
/home/taylor/.themes/Tactile/gtk-2.0/gtkrc:1060: Overlay image options specified without filename

```

---

### Post by hipnerd on 2006-09-19
I also cannot get CSM to work. My symptoms so far are identicle except I get no text output from typing CSM. I only get the gui interface -- which doesn't work.

---

### Post by turbojugend_gr on 2006-09-19
@colonel_panic:  M8 from what I see in your csn output, I make out that it cannot map the csm_settings file... I can't think of anything you can do to change that, as it impies specific knowledge on whatever language csm is buily on... So I can only promt to change to Quinnstorm  repositories, because I believe that you are using sth else, from where that issue came from. I can't be sure about that, but I can reassure you there's no harm at doing so.

---

### Post by uhavegotmale on 2006-09-19
I am assuming that you are using Quinn's compiz-plugins since you are having problems with csm

If you have earlier compiz startup scripts like /usr/bin/thefuture in your startup sessions try removing them. You only need /usr/bin/compiz-start in your startup programs. (and /usr/bin/compiz-manager if you are also using the compiz-manager)

I had the same problem like you have described and removing the old script solved my problem. I can use csm now.

Well, it only took 3 hours of tinkering and trial and error for me to figure that out!:rolleyes:

---

### Post by colonel_panic414 on 2006-09-19
Ok, the chown-ing didnt work, so i'll try the start-up script fix, as i do have "thefuture" in there. And, I am using Quinn's repos :)

---

### Post by colonel_panic414 on 2006-09-19
Hey, the advice about changing startup scripts worked beautifully. Thanks for the awesome help guys! One more question though, how do you activate that awesome blur effect that leaves trails when you move windows? I've messed around with the blur plugin, but idk. If it's in some nwere, cvs version, then nevermind. I saw it on a demo vid a few days ago. :D

---

