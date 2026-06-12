---
title: "WoW and Ubuntu"
date: 2006-01-26
forum: Gaming &amp; Leisure
---

### Post by Pep864 on 2006-01-26
I am really getting frustrated with this so please forgive me if I say something that sounds a little out of line.  

I have recently installed Ubuntu so I am a noob and am not having much luck understanding what is going on.  I am trying to get WoW to work with wine and have read every howto I can find in the forums and come against the same problems everytime...***_Nothing tells me how to install WoW on my linux partion.  What the heck does TODO mean, because that is all I see under the "Installing WoW" sections in the Howto's?_***  The following is what I have tried thus far:

   1: WoW is installed on my windows partition at "C:\Program Files\World of      
       Warcraft\WoW.exe"

   2: When I run winecfg in terminal, all I can find in the applications tab is     
       "C:\Program Files\Common Files" and that folder is empty...no 
       WoW.exe, or any .exe files for that matter.  [B](from what I have read, 
       this is what I am supposed to do so wine can find the .exe file)[/B]

   3: When I try to install from the disk, I get a file browser window with an 
       Install.exe file, but when I click on it, it opens the Add Applications 
       window.  I have yet to figure a way to Add WoW through that.

Not knowing anymore about this system than I do, I have not tried to dig around and change anything on my system to make it work.  To be quite honest, I feel llike I need to be either a Programmer or a Hacker in order to understand alot of the functions of Ubuntu ie...gedit, regedit, source tree's, WTF/config.WTF...and so on and so forth.  

Please someone tell me if I have gotten in over my head?  I had heard that this was very user friendly, but so far I haven't noticed a whole lot of freindliness to this user (from my system that is, not other users).  

***_[SIZE="4"][COLOR="Red"]PLEASE HELP ME!!!!! [-o< :confused: [/COLOR][/SIZE]_***

---

### Post by Perfect Storm on 2006-01-26
Every steps on a new OS takes time. Learning how things are done in another envoriment takes time and patience, but rewarding in the end.
I don't use wine for wow, but cedega. If you want to make it very simple and don't mind paying $5 at months you could go for cedega pay version. Easy to install and easy to get Wow running on it.


.:=The AI Dude=:.

---

### Post by kidcharles on 2006-01-26
Take a deep breath. We are here to help.

In regards to points 1 and 2:

The Wine program uses a fake windows drive to install and run programs that are installed using Wine. This fake drive should not be confused with your actual Windows C: drive that is on a real partition on your hard drive.  When you run winecfg, it's looking in your fake drive (which is located at /home/yourname/.wine/drive_c). That's why it's empty, because it is not your actual Windows C: drive.

In regards to point 3:

I would recommend that if you have a working copy of WoW on your actual Windows drive that you should probably use that rather than trying to install WoW using Wine. You have two options if you go this route:

Option 1: Run WoW on the actual Windows partition using Wine

You should really only do this if the partition uses the FAT32 filesystem.  If it is using the NTFS filesystem you will not be able to write anything in the WoW directory, which I think would make the game basically unplayable (no logging of chats, no addon datafiles, no custom macros, etc.).

Option 2: Copy the WoW directory onto a Linux parition and run it using Wine

This is the better option I would say, if you have the room on your Linux parition(s). You'll have no problem with write-access this way.

Ok, you will probably still have questions about my suggestions, feel free to ask them. Incidentally I'm working on a WoW/Wine howto in this forum ([http://ubuntuforums.org/showthread.php?t=120615](http://ubuntuforums.org/showthread.php?t=120615)) that is an alternative to the other howtos you may have already found.

---

### Post by Pep864 on 2006-01-27
Thank you for the help.  I have an Intel 815G chipset integrated video card, and  have not been able to get cedega to work with it.  Is there a work around for that chipset or do I need to buy a new video card?

Thanks again,

Pep

---

### Post by Perfect Storm on 2006-01-27
Did you setup your card in linux? Or is it only in cedega/wine it won't work.

---

### Post by Pep864 on 2006-01-27
Ummmm...I'm not sure.  How can I tell, and if I haven't set it up, then how do I go about doing that?

I haven't tried playing any other games other than the games that come with the Ubuntu install package, so I really don't know for sure.  Let me know if you need any technical data from my system ( and of course, how to find it) and I will paste it here.  

Thanks

Pep

---

### Post by GIBson3 on 2006-01-27
First off, Welcome to the world that is Gaming and linux...  It's a lot better now than the past though.  Next up...

TO DO:  <--- generally means something they haven't yet done and play [to do] in the future. ;) 

Installing the Game through Wine is possible though as said before Coping it over is usually a "bit easier." To run the installer you would use the console/terminal and issue "wine /cdrom/install.exe"  there maybe command line parameters that need to be passed, your milage will varry... ;)

My system is running a GF3 now, but was on the 815 before...  Save yourself the head ache even if it's _just_ the $50 nvidia special it's going to make your life so much more plesent without trying to get 3D working on the 815.  (I should also note that I had some Display corruption under the 815, which the nvidia drivers cleaned up)

Unfortunately my Ubuntu box is a little to low to run WoW... (though WC3 works well) So I can only give you the what has worked for me... Though you've now peeked my interest and I'm going to try and at least get the Wow install process figured out.. (Honestly I don't need to  be able to play it... just install it ;)  )

---

### Post by Pep864 on 2006-01-30
Thanks so much for the help.  I think that is what I am going to do, get another video card.  You guys have been most helpful thus far.

Thanks 

Pep

---

### Post by GIBson3 on 2006-02-03
Well as a quick update, I've gotten WoW to install via Wine 9.1 and now I'm waiting for the patch to download...  325mb take a long time at 27 KB\s I'll post a "full howto" when it's done and working. :D

---

